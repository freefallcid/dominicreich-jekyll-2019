---
title: 'Powerlevel9k ➔ Powerlevel10k'
excerpt: >
  Das Theme (in meinem Fall für prezto) sieht genauso aus wie Powerlevel9k,
  ist jedoch um ein Vielfaches schneller.
tags: [macos, freebsd, linux, terminal, prezto, zsh]
last_modified_at: 2019-06-25T21:16:12+02:00
categories: [notizen]
toc: true
repo: prezto
support: true
---

Als ich im [September 2017]({% post_url notizen/2017-09-08-powerlevel9k-prezto-zsh-theme %})
auf Powerlevel9k gestoßen bin war ich total überwältigt. Nun habe ich
Powerlevel10k entdeckt, als ich das _Upstream-Repository_[^upstream] von prezto auf Updates
untersucht habe.

[^upstream]: Das [Original-Repository](https://github.com/sorin-ionescu/prezto) von [Sorin Ionescu](https://github.com/sorin-ionescu).

## Im direkten Vergleich zu Powerlevel9k

### Powerlevel9k

![Beispiel Powerlevel9k](/assets/images/prezto-powerlevel9k.jpg)
{: .browser-frame}

### Powerlevel10k

![Beispiel Powerlevel10k](/assets/images/prezto-powerlevel10k.jpg)
{: .browser-frame}

Man kann direkt erkennen, dass hier bereits unterschiedliche Git-Symbole verwendet
werden. Ebenfalls wird im neuen Theme eine Uhr im rechten Prompt hinter der
Uhrzeit angezeigt.

### Powerlevel10k mit Pure Power auf macOS

![Beispiel Powerlevel10k (MacOS)](/assets/images/prezto-powerlevel10k-macos.jpg)
{: .browser-frame}

Für die Installation von Pure Power lese einfach weiter. Weiter unten gib's dann
einen Copy&Paste-Befehl :wink: (oder [direkt zum Absatz](#pure-power))

## Installation

Generell solltest du dir das
[Repository auf Github][repo] ansehen. In der README sind
[verschiedene Installationsmethoden][installation] angeführt und erklärt.

[repo]: https://github.com/romkatv/powerlevel10k
[installation]: https://github.com/romkatv/powerlevel10k#installation

Ich verwende prezto, weshalb ich nur in meiner `.zpreztorc` das neue Theme auswählen
muss.

```
zstyle ':prezto:module:prompt' theme 'powerlevel10k'
```

{% notice %}
**Achtung:** Falls das Theme so nicht übernommen wird, konnte es prezto beim Update via
`zprezto-update` vermutlich nicht aktualisieren. Dies lässt sich aber schnell
manuell lösen. Gehe dazu in das Verzeichnis von prezto und aktualisiere das
Git-Repository von Hand -- mit den Submodulen, denn das neue Theme ist nur ein
weiteres Submodul.
{% endnotice %}

```terminal
$ cd ~/.zprezto
$ git pull
$ git submodule update --init --recursive
```

### Pure Power

Pure Power (`.purepower`) ist eine Konfigurationsdatei für das Powerlevel10k-Theme.
Es sorgt dafür, dass dein Prompt schnell und effizient arbeitet. Ein kurzer Auszug
aus der Datei:

> This file defines configuration options for Powerlevel10k ZSH theme that will make your prompt
> lightweight and sleek, unlike the default bulky look. You can also use it with Powerlevel9k -- a
> great choice if you need an excuse to have a cup of coffee after every command you type.

Um `.purepower` ins Heimverzeichnis zu installieren führe folgenden Befehl aus:

```terminal
$ ( cd && curl -fsSLO https://raw.githubusercontent.com/romkatv/dotfiles-public/master/.purepower )
$ echo 'source ~/.purepower' >>! ~/.zshrc
```

Die zweite Zeile sorgt dafür, dass die Datei am Ende der `.zshrc`-Datei
"gesourced"[^sourced] wird.

[^sourced]: Wenn eine Datei "gesourced" wird, wird sie geladen bzw. "ausgeführt".

## Fazit

Ich bin mit dem neuen Theme sehr zufrieden. Im Vergleich zu Powerlevel9k ist es
gefühlt ein gutes Stück schneller. Ebenso konnte es vorkommen, dass man den
rechten Prompt beim alten Theme "zerschossen" hat. Das ist mir beim neuen Theme
bis jetzt noch nicht passiert.

Obwohl der rechte Prompt meist nett aussah, verschwendete er doch viel Platz. Mit
Pure Power wird im rechten Prompt eigentlich nur die Ausführzeit des letzten
Befehls angezeigt sowie der `benutzer@rechnername`, falls man nicht als
Standardbenutzer oder am eigenen Rechner arbeitet.
