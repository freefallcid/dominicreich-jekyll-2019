---
title:  "How to setup a news server"
excerpt: "Installation and quick configuration of a netnews server."
image:
  path: &image /assets/images/howto-news-server.jpg
  feature: *image
  width: 2288
  height: 744
  teaser: /assets/images/howto-news-server-teaser.jpg
categories: [articles]
tags: [netnews,freebsd]
last_modified_at: 2019-01-21T08:56:52+01:00
toc: true
---

This tutorial shows the initial setup and basic configuration of INN 2.6.0 on FreeBSD 11.0.

It's all about [usenet](https://en.wikipedia.org/wiki/Usenet)---which is probably dying, but I
read alot in the internet and found not much information about building your own news server so
I decided to write down my findings and my experience.

We will have a look at the setup and the initial configuration to have a news server up and running.

## Requirements

We are going to install [InterNetNews](https://www.eyrie.org/~eagle/software/inn/) 2.6.0 on FreeBSD 11.0.
You should have basic knowledge about FreeBSD and its ports. You may also benefit from a routined workflow
when compiling ports.

## Installation of INN

On the terminal head over to `/usr/ports/news/inn` and configure the port. `make config` will help us with that.
You can also configure all dependencies at one, use `make config-recursive` instead. After that, install the port
with `make install clean`.

To start or stop the server as service within FreeBSD you should add the following line to `/etc/rc.conf`.

``` conf
innd_enable="YES"
```

This will also start the server after boot.

## Configuration

The basic configuration is pretty simple. You find many information in the manpages of `inn.conf`,
`ctlinnd`, `readers.conf`, `active`, `newsgroups` and `moderators`.

### inn.conf

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

### readers.conf

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

A client that connects on the local interface gets all rights `RPIANL`---for detailed information about rights and its descriptions have a look at the manpage of `readers.conf`. Look at `ACCESS GROUP PARAMETERS`.

With this configuration any client can see the newsgroups `dominicreich.info` and `dominicreich.support`. The latter is also writable to post a question for an admin. All other newsgroups are hidden.

A useraccount on the newsserver can see the `dominicreich.*` hierarchy. He can also post in there.

<!-- Der Admin darf auch in Gruppen schreiben, die mit `'j'`, `'n'` oder `'x'` in der active-Datei markiert sind. So ist es etwa möglich, die `*.info` Gruppe auf `'j'` oder `'x'` zu setzen (damit niemand schreiben kann), der Admin jedoch Artikel/Ankündigungen absetzen kann. Somit würde man das "Problem" umgehen, dass der Moderator der Gruppe (wenn auf `'m'` gesetzt) mit neuen Artikeln von Benutzern "belästigt" wird. -->

### expire.ctl

To save our articles forever, we add this line into `expire.ctl`:

``` conf
dominicreich.*:A:never:never:never
```

### control.ctl

To allow control messages for `newgroup` and `rmgroup` add this to `control.ctl`

``` conf
newgroup:admin@tmsn.at:dominicreich.*:doit
rmgroup:admin@tmsn.at:dominicreich.*:doit
```

{% notice warning %}
**Watch out!** There is no verification yet implemented. A fake message from `admin@tmsn.at` would add or delete groups. If you plan to use your newsserver on a production environment you should probably think about a good implementation of any kind of user verification.
{% endnotice %}

If you don't need these control messages, use the default value `all:*:*:drop` and delete the rest.

### moderators

I addes this line:

``` text
dominicreich.*:moderator@news.dominicreich.com
```

The file's syntax is described in the header of the file itself. Usually there is `%s` in the local part of the mail address.

### Group management

Groups are managed with the tool `ctlinnd`. Let's add a test group to our configuration.

``` console
# ctlinnd newgroup dominicreich.test y
Ok
```

And a deletion would look like this:

``` console
# ctlinnd rmgroup dominicreich.test
Ok
```

## Files in `/usr/local/news/db`

### `active`

The `active` file contains the managed newsgroups. `ctlinnd` make changes in this file.

A fresh file looks like this:

``` conf
control 0000000000 0000000001 n
control.cancel 0000000000 0000000001 n
control.checkgroups 0000000000 0000000001 n
control.newgroup 0000000000 0000000001 n
control.rmgroup 0000000000 0000000001 n
junk 0000000000 0000000001 n
```

### `newsgroups`

The newsgroups' descriptions are held in this file.

A fresh file:

``` conf
control             Various control messages (no posting).
control.cancel      Cancel messages (no posting).
control.checkgroups Hierarchy check control messages (no posting).
control.newgroup    Newsgroup creation control messages (no posting).
control.rmgroup     Newsgroup removal control messages (no posting).
junk                Unfiled articles (no posting).
```

## Add users to your configuration

I created my userfile manually---with `openssl`. You can also use the tool `htpasswd` (which usually gets installed with the Apache webserver). When using `htpasswd` make sure to use crypt for password encryption.

``` console
$ openssl passwd -crypt
Password:
Verifying - Password:
/qw8fWcTdXCpQ
```

It's output is saved together with a username in your specified password file. I chose `/usr/local/news/etc/.passwds`---look in [`readers.conf`](#readersconf) where I specified this file.

``` conf
admin:5zylMZ158icoo
user1:mCWuM92v9SC0A
user2:bD3paTOdSAKGg
user3:/qw8fWcTdXCpQ
```

## Restart INN

To save changes you want to restart the newserver.

``` console
# service innd restart
Stopping innd: .
Starting innd.
Scheduled start of /usr/local/news/bin/innwatch.
```

## More configuration

You can hide the host that injected the message with those lines in `inn.conf`.

``` conf
addinjectiondate:            true
addinjectionpostingaccount:  false
addinjectionpostinghost:     false
```

That removes the hostname and the ip address of the sender. With `addinjectionpostingaccount` the users accountname (specified in `readers.conf`) gets added to `Injection-Info`.

Let's have a look on some examples.

### All information in `Injection-Info` header line

``` conf
Path: news.dominicreich.com!.POSTED.xx-yyy-zz-zz.adsl.highway.telekom.at!not-for-mail
From: User <user@tmsn.at>
Newsgroups: dominicreich.test
Subject: Re: testpost for the testgroup
Injection-Date: Mon, 3 Apr 2017 20:16:38 +0000 (UTC)
Injection-Info: gefion.dominicreich.com; posting-account="user1@users.dominicreich.com"; posting-host="xx-yyy-zz-zz.adsl.highway.telekom.at:xx.yyy.zz.zz";
        logging-data="58264"; mail-complaints-to="abuse@news.dominicreich.com"
```

### Only the user account in `Injection-Info` header line

``` conf
Path: news.dominicreich.com!.POSTED!not-for-mail
From: User <user@tmsn.at>
Newsgroups: dominicreich.test
Subject: Re: testpost for the testgroup
Injection-Date: Mon, 3 Apr 2017 20:15:48 +0000 (UTC)
Injection-Info: gefion.dominicreich.com; posting-account="user2@users.dominicreich.com";
        logging-data="57952"; mail-complaints-to="abuse@news.dominicreich.com"
```

### All info removed---but with additional `Sender` header

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

For this you also have to uncomment the commented line in the `readers.conf` `users` access block. Uncomment `nnrpdauthsender: true` and the sender header gets added.

## Epilogue

This is a basic configuration. I do not own a newserver nor did I ever owned one. I have read a lot of information when I initially wrote this tutorial (which was back in 2017). You should definitly read more about this topic when you want to set your own server up.

Hints, suggestions or critic can be sent to me per mail or comments. Thank you!

*[INN]: InterNetNews
*[NNRP]: Network News Reader Protocol
*[NNTP]: Network News Transfer Protocol
