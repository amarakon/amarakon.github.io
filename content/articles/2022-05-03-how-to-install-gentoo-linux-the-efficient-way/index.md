---
title: How to Install Gentoo Linux – The Efficient Way
date: '2022-05-03'
slug: how-to-install-gentoo-linux-the-efficient-way
tags: ["foss", "tutorial"]
bibliography: ../../../static/bibliography.bib
csl: ../../../static/citations/apa-no-initials.csl
link-citations: true
reference-section-title: References
nocite: ["@gentoohandbook"]
---

So you finally moved from the beginner distributions and you know want to install truly the best operating system of all time; Gentoo Linux.
Contrary to popular belief, installing this operating system is not difficult in the slightest but it is certainly time consuming.
Usually it will take around five hours to install.
This might deter you, but remember that this operating system will actually save you time in the long run.
Not only is it faster than other operating systems, it also makes the user more intelligent, leading to efficient computer usage.
No current Gentoo user regrets spending five hours installing the operating system to save many more hours in total.

For this installation tutorial, you will need to have an existing Unix-like operating system—like any Linux distribution.
Before I get to the beginning of the installation process, there are a few things you must know.
First, you have to care about computing for the installation of Gentoo to be worth it.
Second, please view the [Gentoo handbook](https://wiki.gentoo.org/wiki/Handbook:Main_Page) while you are watching this video.
It is unlikely but possible that some of the information in this video will be outdated.
The Gentoo wiki also has many details that I will not go into because they are not important enough.
Third, you need to know the architecture of your computer’s CPU, usually it is AMD64.
Finally, you must know whether your computer firmware uses BIOS or UEFI.
Generally, only extremely old computers support only BIOS, only terrible new computers support only UEFI, and most computers support both.
You should be completely sure though to avoid messing your entire installation.
Finally, please note that when text in code blocks are wrapped in `<>` symbols, that means that you need to replace the text.

# Prepare the Disks

Obviously, since Gentoo requires installation from the command-line, you will need to open a terminal.
Use the `lsblk` command do check the available block devices.
To be cautious, you can unplug any storage devices you do not want to accidentally wipe.
Also make sure to know which block device your current running operating system so you do not accidentally wipe that either.
Use the `wipefs` command to wipe a block device if it already has a partition scheme.
Then use the `cfdisk` command to begin partitioning.

``` shell
`# user` lsblk
`# root` wipefs -a /dev/<NAME>
`# root` cfdisk /dev/<NAME>
```

If you’re using BIOS, select DOS.
And if you’re using UEFI, select GPT.
If you’re using BIOS, all you need is one partition.
If you’re using UEFI, you need to make a partition that is at least 128 MB, this will be the boot partition.
You should label this partition “EFI system.”
Then create the second partition using the rest of the space.

Once you exited cfdisk, you need to format your partitions.
If you’re using BIOS, all you have to do is format your one partition as ext4 or any other usable file system you prefer:

``` shell
`# root` mkfs.ext4 /dev/<NAME>1
```

If you’re using UEFI, you must format your first partition as VFAT and your second partition your preferred file system:

``` shell
`# root` mkfs.fat -F 32 /dev/<NAME>1
`# root` mkfs.ext4 /dev/<NAME>2
```

If you’re using BIOS, mount the root partition:

``` shell
`# user` mkdir /mnt/gentoo
`# root` mount /dev/<NAME>2 /mnt/gentoo
```

If you’re using UEFI, mount the root partition and the boot partition:

``` shell
`# root` mkdir /mnt/gentoo
`# root` mount /dev/<NAME>2 /mnt/gentoo
`# root` mount /dev/<NAME>1 /mnt/gentoo/boot
```

# Installing the Gentoo Installation Files

Temporarily set the correct date and time using the `MMDDhhmmYYYY` syntax:

``` shell
`# user` date <MMDDhhmmYYYY>
```

Go to the [download section](https://www.gentoo.org/downloads/#other-arches) of the Gentoo wiki and copy the link of a stage tarball.
I recommend the standard Stage 3 OpenRC.
Download the tarball to `/mnt/gentoo` using the link you copied.
Decompress the archive afterwards.

``` shell
`# user` cd /mnt/gentoo
`# root` wget <URL>
`# root` tar xpvf stage3-*.tar.xz --xattrs-include='*.*' --numeric-owner
```

Run `` `# root` nano /mnt/gentoo/etc/portage/make.conf ``.
Set march equal to native.
The `-j` flag means the amount of threads you want Portage, the package manager to use.
The `-l` flag means the load average.
The `PORTAGE_NICENESS` option refers to how much priority portage should have (the higher the number, the higher the priority).
Setting `ACCEPT_KEYWORDS="~amd64"` will allow portage to install bleeding edge software.
The `VIDEO_CARDS` option is dependent on your video card ([Gentoo, 2020](#ref-gentoocard)).
The `USE` flags are for features you want or do not want in your packages.
The `GRUB_PLATFORMS` option should be set to `"pc"` for BIOS and `"efi-64"` or `"efi-32"` for UEFI.
Copy everything else I did.

    COMMON_FLAGS="-march=native -O2 -pipe"
    CFLAGS="${COMMON_FLAGS}"
    CXXFLAGS="${COMMON_FLAGS}"

    MAKEOPTS="-j2 -l3.6"
    EMERGE_DEFAULT_OPTS="-j2 -l3.6"
    PORTAGE_NICENESS="1"
    ACCEPT_KEYWORDS="~amd64"
    VIDEO_CARDS="intel i915 i965"
    USE="X pulseaudio savedconfig -bluetooth -geolocation -drm"

    # NOTE: This stage was built with the bindist Use flag enabled
    PORTDIR="/var/db/repos/gentoo"
    DISTDIR="/var/cache/distfiles"
    PKGDIR="/var/cache/binpkgs"

    # This sets the language of build output to English.
    # Please keep this setting intact when reporting bugs.
    LC_MESSAGES=C
    L10N=""

    # Other
    GRUB_PLATFORMS="pc"
    GENTOO_MIRRORS="https://mirror.csclub.uwaterloo.ca/gentoo-distfiles/ https://gentoo.osuosl.org/ https://mirrors.rit.edu/gentoo/ http://mirror.csclub.uwaterloo.ca/gentoo-distfiles/ http://gentoo.osuosl.org/ http://mirrors.rit.edu/gentoo/"

# Installing the Base System

Set up the *gentoo* repository:

``` shell
`# root` mkdir -p /mnt/gentoo/etc/portage/repos.conf
`# root` cp /mnt/gentoo/usr/share/portage/config/repos.conf /mnt/gentoo/etc/portage/repos.conf/gentoo.conf
`# root` cp --dereference /etc/resolv.conf /mnt/gentoo/etc/
```

Mount necessary file systems:

``` shell
`# root` mount --types proc /proc /mnt/gentoo/proc
`# root` mount --rbind /sys /mnt/gentoo/sys
`# root` mount --make-rslave /mnt/gentoo/sys
`# root` mount --rbind /dev /mnt/gentoo/dev
`# root` mount --make-rslave /mnt/gentoo/dev
`# root` mount --bind /run /mnt/gentoo/run
`# root` mount --make-slave /mnt/gentoo/run 
```

Enter the new installation environment by chrooting into it:

``` shell
`# root` chroot /mnt/gentoo /bin/bash
`# root` source /etc/profile
`# root` export PS1="(chroot) ${PS1}"
```

Installing a Gentoo ebuild repository snapshot from the web and update it:

``` shell
`# root` emerge-webrsync
`# root` emerge --sync
```

Update the @set (all of your packages).
This will take a lot of time.
If you get a circular dependency error, which is not uncommon, consult the Gentoo wiki ([Gentoo, 2022a](#ref-gentoocircle)):

``` shell
`# root` emerge -uDN @world 
```

Select the time zone for the system.
Look for the available time zones in `/usr/share/zoneinfo/`.
I chose `America/Toronto`.

``` shell
`# user` ls /usr/share/zoneinfo
`# root` echo "America/Toronto" > /etc/timezone
`# root` emerge --config sys-libs/timezone-data
```

Choose the right locale by running `` `# root` nano /etc/locale.gen ``:

    en_CA.UTF-8 UTF-8

``` shell
`#root` locale-gen
```

Check the locale list by running `$ eselect locale list`, then select the right one:

    Available targets for the LANG variable:
      [1]   C
      [2]   C.utf8
      [3]   en_CA.utf8
      [4]   POSIX
      [ ]   (free form)

``` shell
`# root` eselect locale set 3
```

Reload the environment:

``` shell
`# root` env-update && source /etc/profile && export PS1="(chroot) ${PS1}"
```

# Install the Kernel

The easiest way to install the kernel is by installing the gentoo-kernel package.
If you want to customize the kernel, check the Gentoo handbook page on configuring the Linux kernel ([Gentoo, 2015](#ref-gentookernel))
If you need Linux firmware (you most likely do), then install the `linux-firmware` package.

``` shell
`# root` emerge gentoo-kernel linux-firmware
```

# Configure the System

You need to set up fstab:

``` shell
`# root` blkid > /etc/fstab
```

Open the file by running `` `# root` nano /etc/fstab ``.
If you have an SSD, you should enable the `noatime` and `discard` options.
If you are using BIOS, arrange your fstab to something like this:

    # /dev/sda1
    UUID=9167fa6f-bb77-4337-a547-48a20506d297   /   ext4    noatime,discard 0 1

If you are using UEFI, do something like this instead:

    # /dev/sda1
    UUID=dbb15f21-c203-4665-a520-7f92f51661ae   /boot   vfat    defaults,noatime     0 2

    # /dev/sda2
    UUID=9167fa6f-bb77-4337-a547-48a20506d297   /   ext4    noatime,discard 0 1

Set the host name by running `` `# root` nano /etc/conf.d/hostname ``:

    hostname="<host name>"

Install NetworkManager and add it to the default runlevel for internet connection:

``` shell
`# root` emerge net-misc/networkmanager
`# root` rc-update add NetworkManager default
```

Edit the hosts file by running `` `# root` nano /etc/hosts ``:

    127.0.0.1   localhost
    ::1         localhost
    127.0.1.1   <host name>

Set the root password by simply running `` `# root` passwd ``.

# Configure the Bootloader

You now need to install a bootloader, the most common one is GRUB.
When using BIOS:

``` shell
`# root` emerge sys-boot/grub
`# root` grub-install /dev/<NAME>
`# root` grub-mkconfig -o /boot/grub/grub.cfg
```

When using UEFI:

``` shell
`# root` emerge sys-boot/grub
`# root` grub-install --target=x86_64-efi --efi-directory=/boot
`# root` grub-mkconfig -o /boot/grub/grub.cfg
```

## Reboot the system

``` shell
`# root` exit
```

``` shell
`# root` cd
`# root` umount -l /mnt/gentoo/dev{/shm,/pts,} 
`# root` umount -R /mnt/gentoo
`# root` reboot
```

# Finalize the Installation

First, log in as root:

    Login: root
    Password: <password>

Add a user for daily use and set its password:

``` shell
`# root` useradd -mG wheel,news,audio,video,portage <user>
`# root` passwd <user>
```

Finally, remove the now unneeded tarball from the root directory:

``` shell
`# root` rm /stage3-*.tar.*
```

Congratulations, you have successfully completed the installation of Gentoo Linux.
But do not get too excited, because we are not technically done yet.

## Graphical Environment

Now all you need to do is install a display server, xinit or a desktop manager, and a window manager or a desktop environment.

``` shell
`# root` emerge x11-base/xorg-server x11-apps/xinit x11-wm/dwm
`# user` echo "exec dwm" > ~/.xinitrc
`# user` startx
```

# References

<div id="refs" class="references csl-bib-body hanging-indent" line-spacing="2">

<div id="ref-gentookernel" class="csl-entry">

Gentoo. (2015). *Configuring the linux kernel*. <https://wiki.gentoo.org/wiki/Handbook:AMD64/Installation/Kernel>

</div>

<div id="ref-gentoocard" class="csl-entry">

Gentoo. (2020). *Video cards*. <https://wiki.gentoo.org/wiki/Category:Video_cards>

</div>

<div id="ref-gentoocircle" class="csl-entry">

Gentoo. (2022a). *Circular dependencies*. <https://wiki.gentoo.org/wiki/User:Sam/Portage_help/Circular_dependencies>

</div>

<div id="ref-gentoohandbook" class="csl-entry">

Gentoo. (2022b). *Gentoo AMD64 handbook*. <https://wiki.gentoo.org/wiki/Handbook:AMD64>

</div>

</div>
