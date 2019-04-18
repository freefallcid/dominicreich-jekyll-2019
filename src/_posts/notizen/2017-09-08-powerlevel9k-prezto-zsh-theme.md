---
title: 'Das ultimative ZSH-Theme für prezto: Powerlevel9k'
excerpt: >
  Ein sehr gelungenes Theme falls du zsh und prezto in deinem Terminal verwendest.
tags: [macos, zsh, terminal, til]
last_modified_at: 2019-04-18 17:58:42
categories: [notizen]
toc: true
repo: prezto
support: true
---

Ein sehr schönes Theme für dein ZSH-Terminal. Ich verwende es mit
[prezto]({{ site.author.github }}/{{ page.repo }}).

![Beispiel-Bildschirmfoto](/assets/images/prezto-zsh-theme-demo.jpg)
{: .browser-frame}

Das Theme heißt [Powerlevel9k](https://github.com/bhilburn/powerlevel9k) und es
verwendet modifizierte Schriftarten mit zusätzlichen Symbolen.

## Installation

Falls du auch prezto verwendest, ist die Installation ganz einfach.

``` terminal
$ git clone https://github.com/bhilburn/powerlevel9k.git \
~/.zprezto/modules/prompt/external/powerlevel9k
```

Folgende [Installations-Anleitung][Installation] ist sehr hilfreich, doch falls du dein Setup
auf mehreren verschiedenen Betriebssystemen (z.Bsp. Linux, FreeBSD, macOS)
nutzen möchtest, solltest du folgende Methode verwenden, um das neue Theme in
prezto zu integrieren.

[Installation]: https://github.com/bhilburn/powerlevel9k/wiki/Install-Instructions#option-3-install-for-prezto

``` terminal
$ cd ~/.zprezto/modules/prompt/functions
$ ln -s ../modules/prompt/external/powerlevel9k/powerlevel9k.zsh-theme prompt_powerlevel9k_setup
```

Im Unterschied zur Anleitung verwendete ich relative Pfade, denn absolute Pfade
würden bereits beim Verwenden von Linux und macOS schon nicht mehr funktionieren,
denn `~` würde auf den Systemen zu verschiedene Pfaden führen:

- `/home/$USER` unter Linux
- `/home/$USER` unter FreeBSD -- wobei `/home` ein Symlink zu `usr/home` ist
- `/Users/$USER` unter macOS

Du solltest außerdem eine Schriftart verwenden, die die nötigen Symbole
darstellen kann.

## Verwendung von modifizierten Schriftarten

Eine einfache (aber von mir nicht empfohlene) Methode wäre die Installation der
[modifizierten Powerline-Schriftarten][patched]. Wähle die von dir gewünschte
Schriftart aus und speichere die `.ttf`-Datei in `~/.fonts`.  
Aktualisiere den Schriftarten-Cache mittels:

``` terminal
$ fc-cache -vf
```

## Verwendung von Systempaket-Schriftarten

Eine bessere Methode wäre zum Beispiel die Installation von Paketen, die auf
deinem System ohnehin verfügbar sind. Auf meinem MacBook sind das zum Beispiel die
[Nerd-Fonts](https://github.com/ryanoasis/nerd-fonts#option-4-homebrew-fonts) --
verfügbar via [Homebrew](https://brew.sh/index_de).
Auf meinem FreeBSD-Notebook ist das der Port
[nerd-fonts](https://www.freshports.org/x11-fonts/nerd-fonts).

Dementsprechend muss die Konfiguration von prezto in `~/.zshrc` angepasst werden:

```bash
POWERLEVEL9K_MODE='nerdfont-complete'
```

Lies dich doch durch dieses Thema, im [Wiki][schriftarten] des Themes gibt es
verschiedene Methoden für die korrekte Anzeige dieser Symbole.

[schriftarten]: https://github.com/bhilburn/powerlevel9k/wiki/Install-Instructions#step-2-install-a-powerline-font
[patched]: https://github.com/gabrielelana/awesome-terminal-fonts/tree/patching-strategy/patched

Du solltest das Terminal eventuell schließen und erneut öffnen, denn die
Schriftarten werden im aktuell geöffneten Terminal in der Regel nicht übernommen.
