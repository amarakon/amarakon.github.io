---
title: MagickShot – ImageMagick Screenshot
date: "2022-07-29"
---

https://github.com/amarakon/magickshot

MagickShot is a program I created because I am surprised it does not exist yet.
It is a screenshot utility, but there are many screenshot utilities.
However, none of them do **everything** I want them to do:

1. screenshot with mouse selection
1. sceenshot a specified window
1. screenshot a specified monitor
1. screenshot the entire display

Most of them only support the first and last options.
Besides, they are too bloated anyways.
MagickShot is a simple shell script that improves upon the existing `import` tool from ImageMagick.
And it ends up taking screenshots just like magic 😉.

# Usage

```shell
# Screenshot
`# user` magickshot --selection # Select an area to screenshot with the cursor
`# user` magickshot --window # Screenshot the focused window
`# user` magickshot --window=62914562 # Screenshot window 62914562
`# user` magickshot --selection --window # Select a window to screenshot with the cursor
`# user` magickshot --monitor # Screenshot the focused monitor
`# user` magickshot --monitor=0 # Screenshot monitor 0
`# user` magickshot --display # Screenshot the display

# Miscellaneous
`# user` magickshot --title=%F # Set the title format to %F (YYYY-MM-DD)
`# user` magickshot --notify # Play a notification sound
`# user` magickshot --no-notify # Do not play a notification sound (always overrides `--notify`)

# Help
`# user` magickshot --help # Print the help message and exit
```

By default, MagickShot uses screenshots the focused window.
The default output directory is `~/.local/share/magickshot/Screenshots`.
If you give a directory as an argument, it will use that directory instead.
If you use anything else as an argument, it will use that for the file name.

# Dependencies

1. imagemagick
1. xdotool
1. xrandr
1. [printmon](https://github.com/amarakon/printmon)

# Installation

## Universal

```shell
`# user` git clone https://github.com/amarakon/magickshot
`# user` cd magickshot
`# root` make install
```

## Gentoo

```shell
`# root` eselect repository add amarlay git https://github.com/amarakon/amarlay
`# root` emerge --sync amarlay
`# root` emerge media-gfx/magickshot
```

# Uninstallation

## Universal

```shell
`# user` cd magickshot
`# root` make uninstall
```

## Gentoo

```shell
`# root` emerge -c media-gfx/magickshot

# Remove my overlay (optional)
`# root` eselect-repository remove -f amarlay
`# root` emerge --sync
```

# Configuration

You can change the default options for MagickShot via the configuration file.
The configuration file is located at `~/.config/magickshot/magickshot.conf` by default.

```shell
output_directory=~/Images/Screenshots
title="%Y-%d_%R:%S"

sound_directory=/usr/share/sounds/deepin/stereo
sound_success=$sound_directory/complete-print.wav
sound_failure=$sound_directory/dialog-error-serious.wav
```
