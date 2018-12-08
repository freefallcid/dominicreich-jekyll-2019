---
title:  "How to setup a news server"
excerpt: "Installation and quick configuration of a netnews server."
image:
  path: &image /assets/images/howto-news-server.jpg
  feature: *image
  teaser: /assets/images/howto-news-server-teaser.jpg
categories: [howto]
tags: [netnews,freebsd]
---

This tutorial shows the initial setup and basic configuration of INN 2.6.0 on FreeBSD 11.0.

It's all about [usenet](https://en.wikipedia.org/wiki/Usenet)---which is probably dying, but I
read alot in the internet and found not much information about building your own news server so
I decided to write down my findings and my experience.

We will have a look at the setup and the initial configuration to have a news server up and running.

# Requirements

We are going to install [InterNetNews](https://www.eyrie.org/~eagle/software/inn/) 2.6.0 on FreeBSD 11.0.
You should have basic knowledge about FreeBSD and its ports. You may also benefit from a routined workflow
when compiling ports.

# Installation of INN

On the terminal head over to `/usr/ports/news/inn` and configure the port. `make config` will help us with that.
You can also configure all dependencies at one, use `make config-recursive` instead. After that, install the port
with `make install clean`.

To start or stop the server as service within FreeBSD you should add the following line to `/etc/rc.conf`.

``` conf
innd_enable="YES"
```

This will also start the server after boot.

# Configuration

The basic configuration is pretty simple. You find many information in the manpages of `inn.conf`,
`ctlinnd`, `readers.conf`, `active`, `newsgroups` and `moderators`.

## inn.conf

INN installs within `/usr/local/news/`. Configuration files reside in `/usr/local/news/etc/`.

We will make basic settings or changes in `inn.conf`.

``` conf
organization:    "A very local News Site"
server:          news.dominicreich.com
pathhost:        news.dominicreich.com
moderatormailer: %s@news.dominicreich.com
domain:          dominicreich.com
complaints:      abuse@news.dominicreich.com
```

## readers.conf

This files defines the access rights on the news server. My `readers.conf` looks like this:

``` conf
# auth block
#

auth "default" {
  auth: "/usr/local/news/bin/auth/passwd/ckpasswd -f /usr/local/news/etc/.passwds"
  default: "<FAIL>"
  default-domain: users.dominicreich.com
}

auth "localhost" {
    hosts: "localhost, 127.0.0.1, ::1, stdin"
    default: "<localhost>"
}

# access block
#

access "users" {
  users: "*@users.dominicreich.com,!<FAIL>@users.dominicreich.com,!admin@*"
  newsgroups: "*,!control,!control.*,!junk"
  #nnrpdauthsender: true
  access: RP
}

access "fail" {
  users: "<FAIL>@*"
  newsgroups: "dominicreich.info,dominicreich.support"
}

access "admin" {
  users: "admin@*"
  newsgroups: "*"
  access: RPA
  perlfilter: false
}

access "localhost" {
    users: "<localhost>"
    newsgroups: "*"
    access: RPIANL
}
```



Wird ein Client über die lokale Schnittstelle, also `localhost` verbunden, so erhält er alle Rechte `RPIANL` -- die Rechte und deren Erklärungen findest du in der Manpage von `readers.conf` unter ACCESS GROUP PARAMETERS.  
Mit dieser Konfiguration ist es Benutzern außerdem erlaubt, die Newsgroups `dominicreich.info, dominicreich.support` zu sehen und auch in `dominicreich.support` zu posten, um etwa ein Anliegen vorzubringen oder eine Frage zu stellen. Alle anderen Newsgroups werden versteckt.

Hat aber ein Benutzer einen Benutzeraccount auf dem Newsserver, so darf er `dominicreich.*` sehen bzw. auch darin schreiben. <!-- Der Admin darf auch in Gruppen schreiben, die mit `'j'`, `'n'` oder `'x'` in der active-Datei markiert sind. So ist es etwa möglich, die `*.info` Gruppe auf `'j'` oder `'x'` zu setzen (damit niemand schreiben kann), der Admin jedoch Artikel/Ankündigungen absetzen kann. Somit würde man das "Problem" umgehen, dass der Moderator der Gruppe (wenn auf `'m'` gesetzt) mit neuen Artikeln von Benutzern "belästigt" wird. -->

## expire.ctl

Um unsere Artikel ewig zu speichern, fügen wir in der `expire.ctl`-Datei folgende Zeile an.

``` conf
dominicreich.*:A:never:never:never
```

## control.ctl

Wir werden Steuernachrichten für `newgroup` und `rmgroup` zulassen.

``` conf
newgroup:admin@tmsn.at:dominicreich.*:doit
rmgroup:admin@tmsn.at:dominicreich.*:doit
```

Wir sollten womöglich eine Verifizierung mit einbauen, sodass diese auch verifiziert werden -- damit habe ich mich im Rahmen dieses Beitrags nicht befasst. Wer Bedenken hat, sollte die Steuernachrichten möglichst weglassen. Werden keine Steuernachrichten benötigt oder gewollt, so lasse einfach `all:*:*:drop` als den ersten Eintrag stehen und lösche den Rest. Das bietet sich an, wenn du den Server ohnehin in deinem eigenen Netzwerk ohne direkte Anbindung ans Usenet laufen lassen willst.

## moderators

Für den Fall der Fälle habe ich diese Zeile eingefügt:

``` text
dominicreich.*:moderator@news.dominicreich.com
```

Das Format wird ganz oben in der Datei erklärt. Im Normalfall wird `%s` im lokalen Teil der Email-Adresse verwendet. 

## Gruppen hinzufügen

Gruppen werden mit `ctlinnd` verwaltet. Wir fügen hier jetzt eine Testgruppe hinzu.

``` console
# ctlinnd newgroup dominicreich.test y
Ok
```

Die Gruppe können wir wieder mit `ctlinnd` löschen.

``` console
# ctlinnd rmgroup dominicreich.test
Ok
```

# Dateien unter `/usr/local/news/db`

## Die active-Datei

In der active-Datei stehen die Newsgroups, die vom Newsserver verwaltet werden. Mit `ctlinnd` werden sozusagen Änderungen in dieser Datei gemacht.  
Anfangs sieht die active-Datei so aus:

``` conf
control 0000000000 0000000001 n
control.cancel 0000000000 0000000001 n
control.checkgroups 0000000000 0000000001 n
control.newgroup 0000000000 0000000001 n
control.rmgroup 0000000000 0000000001 n
junk 0000000000 0000000001 n
```

## Die newsgroups-Datei

In der newsgroups-Datei stehen die Beschreibungen zu den einzelnen Newsgroups.  
Anfangs sieht die newsgroups-Datei so aus:

``` conf
control             Various control messages (no posting).
control.cancel      Cancel messages (no posting).
control.checkgroups Hierarchy check control messages (no posting).
control.newgroup    Newsgroup creation control messages (no posting).
control.rmgroup     Newsgroup removal control messages (no posting).
junk                Unfiled articles (no posting).
```

# Benutzer hinzufügen

Ich habe meine Benutzer in einer Datei angelegt (manuell). Dazu habe ich `openssl` verwendet. Man kann auch das meist mit Apache mitinstallierte `htpasswd` verwenden -- dabei sollte man darauf achten, dass das Passwort mittels `Crypt` erzeugt wird.  
Mit `openssl` erzeugt man den Hash wie folgt:

``` console
$ openssl passwd -crypt
Password:
Verifying - Password:
/qw8fWcTdXCpQ
```

Die Ausgabe wird zusammen mit dem Benutzernamen in der gewünschten Datei gespeichert. Wie oben in der `readers.conf` bereits zu sehen war, habe ich `/usr/local/news/etc/.passwds` als Datei gewählt.

``` conf
admin:5zylMZ158icoo
user1:mCWuM92v9SC0A
user2:bD3paTOdSAKGg
user3:/qw8fWcTdXCpQ
```

# INN neu starten

Um etwa Änderungen zu speichern.

``` console
# service innd restart
Stopping innd: .
Starting innd.
Scheduled start of /usr/local/news/bin/innwatch.
```

# Weitere Einstellungen

Will man den Host, von dem ein Artikel stammt nicht in den Headern sehen, so kann man in `inn.conf` noch folgende Einstellungen vornehmen.

``` conf
addinjectiondate:            true
addinjectionpostingaccount:  false
addinjectionpostinghost:     false
```

Das entfernt den Hostname und die IP Adresse des Senders. Mittels `addinjectionpostingaccount` wird der Benutzername (wie in der `readers.conf` festgelegt) in die `Injection-Info` hinzugefügt.

Nachfolgend habe ich noch ein paar Beispiele.

## Alle Informationen im Injection-Info Header

``` conf
Path: news.dominicreich.com!.POSTED.xx-yyy-zz-zz.adsl.highway.telekom.at!not-for-mail
From: User <user@tmsn.at>
Newsgroups: dominicreich.test
Subject: Re: testpost for the testgroup
Injection-Date: Mon, 3 Apr 2017 20:16:38 +0000 (UTC)
Injection-Info: gefion.dominicreich.com; posting-account="user1@users.dominicreich.com"; posting-host="xx-yyy-zz-zz.adsl.highway.telekom.at:xx.yyy.zz.zz";
        logging-data="58264"; mail-complaints-to="abuse@news.dominicreich.com"
```

## Nur der zugehörige Benutzeraccount im Injection-Info Header

``` conf
Path: news.dominicreich.com!.POSTED!not-for-mail
From: User <user@tmsn.at>
Newsgroups: dominicreich.test
Subject: Re: testpost for the testgroup
Injection-Date: Mon, 3 Apr 2017 20:15:48 +0000 (UTC)
Injection-Info: gefion.dominicreich.com; posting-account="user2@users.dominicreich.com";
        logging-data="57952"; mail-complaints-to="abuse@news.dominicreich.com"
```

## Alle Informationen entfernt -- jedoch mit zusätzlichem Sender Header

``` conf
Path: news.dominicreich.com!.POSTED!not-for-mail
From: User <user@tmsn.at>
Newsgroups: dominicreich.test
Subject: Re: testpost for the testgroup
Sender: user2@users.dominicreich.com
Injection-Date: Mon, 3 Apr 2017 18:15:07 +0000 (UTC)
Injection-Info: gefion.dominicreich.com;
        logging-data="54917"; mail-complaints-to="abuse@news.dominicreich.com"
```

Das wird erreicht, wenn in der `readers.conf` im `users` access-Block `nnrpdauthsender: true` gesetzt wird. (das ist die Zeile, die oben auskommentiert ist)

# Nachwort

Die Konfiguration sollte somit abgeschlossen sein. Selbstverständlich sollte sich jeder genauer in die Materie einlesen; die hier vorgeschlagene Konfiguration ist sicherlich zu wenig, um den Server produktiv ins Internet zu stellen -- doch fürs heimische LAN würde ich das wohl so belassen.

Hinweise, Anregungen oder auch Kritik kannst du gerne per Email oder in den Kommentaren loswerden. Vielenk Dank!

[Usenet]: https://de.wikipedia.org/wiki/Usenet
[InterNetNews]: https://www.eyrie.org/~eagle/software/inn/

*[INN]: InterNetNews
*[NNRP]: Network News Reader Protocol
*[NNTP]: Network News Transfer Protocol
