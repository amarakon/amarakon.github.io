---
title: DFM – dmenu File Manager
date: "2022-11-07"
---

https://github.com/amarakon/dfm

The dmenu file manager is the best and fastest way to manage files!
It is even faster than using the terminal, but has the perks of a graphical user interface.
Therefore, it has the best of both worlds.
You can use it to quickly open files in literally around one second.
And unlike graphical file managers, it supports shell abbreviations such as `..`, `*`, and `~`.
You can also quickly go back to any directory by typing part of its name!
This is my best project so far, and it is definitely criminally underrated.
I guess it is better explained visually:

![](/images/dfm.gif)

# Usage

```shell
# Modes
dfm --open # Open the selection
dfm --print # Print the selection

# Copying
dfm --copy # Copy the selection
dfm --copy=primary # Copy the selection to the primary clipboard
dfm --no-copy # Do not copy (always overrides `--copy`)

# Miscellaneous
dfm --cat # Concatenate the selections
dfm --sensitive # Use case-sensitive matching
dfm --insensitive # Use case-insensitive matching
dfm --length=LENGTH # Set dmenu's length to LENGTH
dfm --full # Use the full path for the prompt
dfm --abbreviated # Use the abbreviated path for the prompt

# Help
dfm --help # Print the help message and exit
```

By default, DFM uses the `open` mode.
You can enter a directory by pressing the `Return` key.
Similarly, you can select a file by pressing the `Return` key.
`Return` will use the selected file or directory.
If you want to use the text in the prompt, use `Shift+Return`.
To autocomplete the text in the prompt with the current selection, simply press `Tab`.
To select multiple files, press `Control+Return` on each selection and press `Return` on the last one.
(This requires the [multi-selection](https://tools.suckless.org/dmenu/patches/multi-selection/) dmenu patch.)


All shell abbrevations work.
You can use a wildcard (`*`) to select all the files.
You can go to the home directory by typing `~`.
Keep in mind that these will not work if there is literarlly a file or directory called `*` or `~`.
Use `.` to refresh the current directory or `..` to go back to the parent directory.
A better way to go back to multiple parent directories is to use the "backtrack" feature.

## Backtrack

One of the best features of DFM is the ability to quickly backtrack to any directory.
This allows you to type a directory you passed in the prompt to return to it instead of constantly doing `..`.
If you are in the `/home/amarakon/.local/src/amarakon/dfm` directory, you can type `.local` in the prompt and press `Return` to quickly backtrack to the `/home/amarakon/.local` directory.
You do not even need to type the full name!
You can type `.l` instead of `.local` for example.
If there is more than one match, it will use the closest one.
For example, if I was in the `/home/amarakon/.local/src/amarakon/dfm` directory and I chose to return to `amarakon`, It will return me to `/home/amarakon/.local/src/amarakon`.
It was inpired by [bd](https://github.com/vigneshwaranr/bd).

# Dependencies

1. dmenu
1. perl (for case-insensitive matching)
1. [sesame](https://github.com/green7ea/sesame) or xdg-utils (sesame is preferred because it supports multi-selection and it is faster.)
1. xclip (clipboard support)

# Installation

## Universal

```shell
git clone https://github.com/amarakon/dfm
cd dfm
make install
```

## Gentoo

```shell
sudo eselect repository add amarlay git https://github.com/amarakon/amarlay
sudo emerge --sync amarlay
sudo emerge x11-misc/dfm
```

# Uninstallation

## Universal

```shell
cd dfm
sudo make uninstall
```

## Gentoo

```shell
sudo emerge -c x11-misc/dfm

# Remove my overlay (optional)
sudo eselect-repository remove -f amarlay
sudo emerge --sync
```

# Configuration

You can change the default options for DFM via the configuration file.
The default location for it is `~/.config/dfm/dfm.conf`.

```shell
copy=true # Copy to clipboard
cat=true # Concatenate the selection
case_sensitivity=sensitive # Use case-sensitive matching
length=30 # Set dmenu's length to 30
path=full # Use the full path
```

```shell
copy=false # Do not copy to clipboard
print=true # Print the selection
path=abbreviated # Use the abbreviated path
```

```shell
open=true # Open the selection with the default program
case_sensitivity=insensitive # Use case-insensitive matching
```

```shell
copy=primary # Copy to primary clipboard
```
```shell
copy=secondary # Copy to secondary clipboard
```
```shell
copy=buffer-cut# Copy to buffer-cut clipboard
```
