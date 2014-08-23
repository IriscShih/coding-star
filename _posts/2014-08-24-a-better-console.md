---
layout: post
title: a better console
description: "using MacVim, zsh and iTerm"
headline: "useful tools for working with the terminal in MacOS"
categories: JavaScript
tags: 
- MacVIM
- ZSH
- iTERM
comments: false
mathjax: true
featured: true
published: true
david: true
iris: false
---

Ever used Vim in Mac but somehow wish, you could select text with your mouse cursor?
Sadly your normal terminal cannot recognize mouse events in MacOS. Furthermore, 
using bash might be not the best way to your way into Code Heaven. In the following I will list some cool tools, which are useful for everyday coding with VIM.

## Oh-my-zsh
Forget bash, zsh comes with auto-fill, git support and hundreds of plugins for nodejs, python, etc. And it is easy to install.
Just go to [oh-my-zsh](http://ohmyz.sh/). You will never miss bash again.

{% highlight bash %}
curl -L http://install.ohmyz.sh | sh
{% endhighlight %}

## MacVIM
MacOS preinstalled Vim is old... really old. Time for an update! 

[MacVim](https://code.google.com/p/macvim/) supports multiple windows with tabbed editing and a host of other features such as:

- bindings to standard OS X keyboard shortcuts (⌘Z, ⌘V, ⌘A, ⌘G, etc.),
- transparent backgrounds,
- full-screen mode,
- multibyte editing with OS X input methods and automatic font substitution,
- ODB editor support,
and more. Most importantly, MacVim brings you the **full power of Vim 7.4** to Mac OS X.

Install it from the site and just set an alias to vim in your .bash_profile.
Restart your terminal app and voila, Vim 7.4 on your Mac!

{% highlight bash %}
alias vim="/Users/user/Applications/MacVim.app/Contents/MacOS/Vim"
{% endhighlight %}

or override it completely (need Xcode and Homebrew for that!)

{% highlight bash %}
brew install macvim --override-system-vim
{% endhighlight %}

## iTerm 2 - the better terminal.app
Please, get rid of your terminal. There is something better out there.
iTerm 2 is just wonderful! It is transparent, has cool shortkeys which allows you to work with the terminal lightning fast, it has textsearch and it allows you to edit your .vimrc file in that way, that VIM can recognize the mouse cursor! Awesome!

{% highlight bash %}
vim ~/.vimrc

set mouse=a
{% endhighlight %}

You can install it [here](http://iterm2.com/)

That are some nice tools I discovered for setting up lightning speed dev with your console.
Have fun!


