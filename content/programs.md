---
title: Software and Hardware I Use and Endorse
date: "2022-07-16"
tags: ["foss"]
---

This is a list of the most important software and hardware I use.
It may include programs that I have developed [myself](https://github.com/amarakon).

# What Makes a Good Program

I do not endorse the use of proprietary software because it is immoral and bad.
I use software that is minimal, extensible, and fast.
Very rarely do I use software that is written in Python.
I like to do something in the simplest way possible.
I prioritize minimalism over convenience.
For example, if I want to rotate or crop an image, I will use ImageMagick instead of my image editor (GIMP).

# Software

## Basic

Operating system
: I use Gentoo GNU/Linux.
To me, there is no operating system that comes **close** to being as good as Gentoo.
Where do I even begin?
The best thing about Gentoo is it's configuration. 
It has the best balance of being configurable and being easy-to-use.
Most people criticize it for how long it takes to install it, but they do not think about how easy it is to **maintain**.
You can customize the operating system to optimize it for your computer.
This scares normies, but remember that this is completely **optional**.
For more information, read my [article](/articles/gentoo-linux-the-best-operating-system-ever-made/) about Gentoo.

Terminal emulator
: Unfortunately, there is no perfect terminal emulator.
They are all flawed.
This is surprising since I view terminals as simple software.
But the one I use is Alacritty.
It balances simplicity and features.
It does not have tabs, or a scroll-bar, or any of that bullshit bloated terminals have.
But it uses GPU acceleration which makes it the fastest terminal.
And it is generally reliable.
Kitty is bloated and slower than Alacritty.
st (simple terminal) is too simple!

Shell
: It is easily Zsh (Z shell) for me.
It has the best syntax highlighting, plugins, and auto-suggestions.
I do not use it for scripts, but I use it for my default shell for my terminal.
For scripts, I use Dash (Debian Almquist shell).
It is usually the `#!/bin/sh` symbolic link and it is faster than Bash and Zsh.
Even if you want to use Bashisms or Zshisms, there is no point in not setting the shebang to `#!/bin/sh`.
Bashisms and Zshism can be converted to be POSIX-compliant most of the time.

Window manager
: I do not use a desktop environment because they are all bloated, so I use only a window manager.
The window manager I use is dwm (dynamic window manager).
It is the fastest way to work with windows.
It tiles windows by default, allowing you to use many windows at the same time.
Currently, I am working with four windows at the same time.
This is not possible with a floating window manager.
I have also added many [patches](https://github.com/amarakon/dotfiles/tree/master/etc/portage/patches/x11-wm/dwm) to dwm.
But make no mistake about it, dwm is perfectly usable out of the box.

Text editor
: I use Neovim, which is based on Vim.
Neovim is not your average text editor.
First of all, it can only be used from the terminal.
Second, it also doubles as a code editor or IDE.
Most importantly, you don't just **type**.
There are many modes: normal insert, visual, visual line, visual block.
This allows you to more efficiently work with text.
It takes 10 minutes to learn it, but it is so much better when it is mastered.

Web browser
: Just like how there is no perfect terminal, there is no good web browser.
The one that balances privacy and usability the best is LibreWolf.
IceCat focuses too much on privacy while Firefox has terrible privacy.
Almost everything still works on LibreWolf, but I still have Firefox installed just in case.
These are the extensions I have installed: (Hopefully their names explain what they do.)
    - [uBlock Origin](https://addons.mozilla.org/en-CA/firefox/addon/ublock-origin/)
    - [CanvasBlocker](https://addons.mozilla.org/en-CA/firefox/addon/canvasblocker/)
    - [LocalCDN](https://addons.mozilla.org/en-CA/firefox/addon/localcdn-fork-of-decentraleyes/)
    - [ClearURLS](https://addons.mozilla.org/en-CA/firefox/addon/clearurls/)
    - [Universal Bypass](https://addons.mozilla.org/en-CA/firefox/addon/universal-bypass/)
    - [I don't care about cookies](https://addons.mozilla.org/en-CA/firefox/addon/i-dont-care-about-cookies/)
    - [cookies.txt](https://addons.mozilla.org/en-CA/firefox/addon/cookies-txt/)
    - [LibRedirect](https://addons.mozilla.org/en-CA/firefox/addon/libredirect/)
    - [Nord Web Theme](https://addons.mozilla.org/en-CA/firefox/addon/nord-web-theme/)

    For more information about web browsers, see my [article](/articles/librewolf-is-currently-the-best-web-browser/) about LibreWolf.

## Utilities

File manager
: I use [DFM](https://github.com/amarakon/dfm) (dmenu File Manager).
I created DFM myself because all of the currently available file managers are bad.
This is because they use GTK or QT.
I do not want an entire window for a file manager!
I just want to open files in dmenu, that is satisfactory for me.
For copying, moving, removing, and other commands with files, I just use the terminal.
But for opening a few files, I use DFM because it is faster.

Media player
: mpv and VLC are literally the only good media players out there.
But I prefer mpv because it is more minimalist and it has a terminal user interface for audio files.
mpv is so configurable yet it is great out of the box as well.
It is free and it gets the job done.

Image viewer
: nsxiv is the mpv of image viewers, enough said.

Document viewer
: Zathura is the Vim of document viewers, enough said.

Download manager
: I like to download files from the command-line.
wget is installed on most GNU/Linux distributions by default, but there is a better alternative.
aria2 is faster and has better syntax highlighting.
Also, it supports torrents.
So you do not need a separate program for managing torrents.

## Production

Video/audio
: To convert videos and audio, I use FFmpeg.
It is so simple it is laughable: `ffmpeg input.mp4 output.mkv`.
To record video and audio, I use [FFRec](https://github.com/amarakon/ffrec) which is based on FFmpeg.
I developed FFRec because recording with plain FFmpeg is painfully annoying.
For editing videos, I don't care about the differences between most video editors, but I use Olive.

Images
: ImageMagick is the ffmpeg of image converters, enough said.
To take screenshots, I developed [MagickShot](https://github.com/amarakon/magickshot) for the same reason I developed FFRec.
And GIMP is the only good free image manipulation program.

Typesetter
: The only acceptable typesetting program is LaTeX, and there are many reasons for that.
Good luck typesetting math with anything else.
But technically, I do not use LaTeX; I use R Markdown.
However, R Markdown uses LaTeX.
It just adds layers ontop of it to simplify the process.
Read my [article](/articles/comparing-the-best-markup-languages-for-making-pdf-documents/) about markup languages for more information.

# Hardware

Computer
: My computer is a laptop.
It is the ThinkPad T420.

Storage devices
: Western Digital Blue solid state drives are good enough to me 🤷.
