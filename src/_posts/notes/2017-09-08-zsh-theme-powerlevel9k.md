---
title: "Powerlevel9k: a theme for ZSH (and prezto)"
excerpt: "A very nice theme if you use prezto in your ZSH terminals."
tags: [macos, zsh, terminal]
# last_modified_at: 2018-02-25T13:29:54+01:00
categories: [til]
---

There's very nice theme for ZSH that I actually use myself.

It's name is [Powerlevel9k][theme] and it uses powerline patched fonts with additional symbols.
If you use [prezto] the [installation] is very, very easy.

``` terminal
$ git clone https://github.com/bhilburn/powerlevel9k.git  ~/.zprezto/modules/prompt/external/powerlevel9k
```

Read those [installation instructions for prezto][installation] but if you want to use your prezto
configuration on multiple computers you should better use the following method to create the correct
symlink (with a relative path[^relative]).

``` terminal
$ cd ~/.zprezto/modules/prompt/functions
$ ln -s ../modules/prompt/external/powerlevel9k/powerlevel9k.zsh-theme prompt_powerlevel9k_setup
```

Now you need to install the [powerline patched fonts][font-awesome] to display the symbols correctly.
I personally use the [pre-patched Source-Code-Pro font][fonts]---you may use whatever fits your needs.

Copy the `.ttf`-files to `~/.fonts` and update the font-cache.

``` terminal
$ fc-cache -vf
```

That's it. All newly opened terminal windows should use the time now.

[^relative]: In the [original installation instruction][installation] an absolute path is used for the symlink---because '`~`' gets expanded to an absolute path. On different platforms that path will be different. On Linux that path is something like `/home/$USER`; but on macOS that path might be something like `/Users/$USER`.

[theme]: https://github.com/bhilburn/powerlevel9k/
[prezto]: https://github.com/sorin-ionescu/prezto
[font-awesome]: https://github.com/bhilburn/powerlevel9k/wiki/Install-Instructions#step-2-install-a-powerline-font
[fonts]: https://github.com/gabrielelana/awesome-terminal-fonts/tree/patching-strategy/patched
[installation]: https://github.com/bhilburn/powerlevel9k/wiki/Install-Instructions#option-3-install-for-prezto
