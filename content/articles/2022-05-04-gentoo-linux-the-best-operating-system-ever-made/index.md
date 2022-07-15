---
title: 'Gentoo Linux: The Best Operating System Ever Made'
date: '2022-05-04'
slug: gentoo-linux-the-best-operating-system-ever-made
tags: ["foss"]
bibliography: ../../../static/bibliography.bib
csl: ../../../static/citations/apa-no-initials.csl
link-citations: true
reference-section-title: References
---

In my previous blog post titled *How to Install Gentoo – The Efficient Way*, I said that Gentoo Linux is “truly the best operating system of all time” ([Al-Zubaidi, 2022](#ref-install-gentoo)).
I stand by that statement and there are many reasons as to why I think it is.
The top three currently most popular operating systems are Windows 10, macOS, and Chrome OS.
You may or may not have heard of Linux.

<div class="figure">

<img src="{{< blogdown/postref >}}index_files/figure-html/pie-1.svg" alt="Operating system market share" width="672" />
<p class="caption">
Figure 1: Operating system market share
</p>

</div>

[Statcounter](#ref-desktop-os-marketshare) ([2022](#ref-desktop-os-marketshare))

Technically, Linux is not an operating in and of itself, rather it is the core of the operating system and each distribution should provide all the additional programs required for that distribution.
There are hundreds of distributions of Linux, so making a decision is tirelessly difficult for most people who are just getting started with Linux.
Many people have the bad habit of constantly distribution-hopping between different distributions to experience all of them for themselves.
Some people suggest to “choose the distro that works the best for you” ([Smith, 2018](#ref-best-linux-distro)), but the problem with this suggestion is that most people do not know what works best for them.
The biggest issue that makes it difficult to choose the correct distribution is that too many of them are similar to each other.
A lot of them are only different by their desktop environment, theme, and package manager.
This post is not about solving the distribution-hopping problem, it will be instead focusing on how the Gentoo stopped me from continuing to do so.

What makes Gentoo stand out from every other Linux distribution is that it is not similar to any other.
Even its forks—such as Funtoo, Calculate Linux, and Redcore Linux—are not similar to pure Gentoo.
The most distinct features of Gentoo is its package manager, system management, speed, and versatility.

# Portage: Package Manager

In my opinion, Gentoo’s package manager, Portage, has the best syntax for any package manager.
The output on the terminal is undoubtedly beautiful.
Gentoo is a source-based based distribution.
This means that compiles programs from their source code instead of using prebuilt binaries.
The biggest benefit from this method is the ability to optimize the operating system for your specific computer using `USE` flags.
To what extent you want to optimize Gentoo is absolutely your decision to make.
You can go all out, setting as many `USE` flags as possible to achieve ultimate minimalism.
You can set a moderate amount of `USE` flags to make the most important optimizations while leaving trivial options to their defaults.
Or you can use no optimizations at all and instead benefit from the other perks that come with using Portage and—more broadly, Gentoo.

The second biggest benefit of Portage is greater security.
When you install an precompiled binary—even if it is free software, you have to place your trust in whoever compiled it.
It is possible that somebody could have changed the code and it would be impossible to prove it.
The chances of this issue occuring is obviously impossible if you compile the software from its source code.
You might think that it is unlikely to notice any malicious code in large projects, but that is definitely [not the case](https://security.stackexchange.com/questions/194953/how-is-compiling-a-program-from-source-more-secure).

**[Ben](https://security.stackexchange.com/users/93625/ben):**

> In theory, at some point in time every line of code in Chromium, Linux, Firefox, etc.
> has been looked at by at least one person.
> Furthermore someone definitely looks at every change made. If the source code was ever non-malicious, it would be difficult to make it malicious.

Nevertheless, there are a considerable amount of binary packages in Gentoo.
You can check the names and the amount by running these commands respectfully:

``` shell
$ eix "\-bin" -c --in-overlay gentoo | grep "\-bin "
```

``` shell
$ eix "\-bin" -c --in-overlay gentoo | grep "\-bin " | wc -l
```

If you do not have Gentoo installed and want to search for packages, the [Gentoo Portage Overlays](https://gpo.zugaina.org/) search engine is a good alternative.

Binary packages are common for huge programs that take hours to build, or proprietary software.
Gentoo prevents you from installing any software that is not licensed with a free license by default.
I do not recommend installing proprietary software—but if you actually want to, set `ACCEPT_LICENSE="*"` (The default is `-* @FREE` ([Gentoo, 2021b](#ref-gentoo-license-groups)).)
Even binary packages have `USE` flags to customize them to the most possible, although less than source packages of course.
Options other than `USE` flags exist and can be set globally in `/etc/portage/make.conf` or per-package in `/etc/portage/package.env` ([Gentoo, 2022a](#ref-gentoo-make.conf), [2022b](#ref-gentoo-package.env)).
These include compiler flags, `make` and `emerge` options, features, CPU flags.
Each of these options are covered extensively in the [Gentoo wiki](https://wiki.gentoo.org/).

# eselect: System Management

There are ways other than the use of the package manager with which you can configure your operating system.
Most distributions do not pay attention to this, thus they have poor system configuration.
Arch Linux, which has the excellent package manager `pacman`, has bad system management otherwise.
Gentoo includes the `eselect` command which allows you to easily manage your system.
You can easily manage software versions, environment variables, repositories.
It is a nice bonus feature that shows the passion and attention to detail the Gentoo developers have.
Despite the difficult installation process, Gentoo is the easiest distribution to use.
To give an example, it is much easier and safer to set your `/bin/sh` symlink.
On Arch, you would have to risk breaking your entire system by running this command:

``` shell
# ln -sfT /bin/dash /bin/sh
```

On Gentoo, you can use `eselect`:

``` shell
# eselect sh set dash
```

# Speed

Gentoo Linux was named after the gentoo penguin, the fastest swimming species of penguin ([Wikipedia, 2022](#ref-wikigentoo)).
The gentoo penguin is also slim (minimalist) unlike emperor penguins which are fat (bloated).
This is probably not intended, but a detail I noticed.
The reason Gentoo is very fast is its extensive customization.
As discussed before, you can optimize the operating system to suit your computer and needs.
This causes it to run considerably faster, since there is minimal bloat and software is trimmed down.
Gentoo boots faster than most other operating systems due to this minimalism and its init system, OpenRC.
It takes less than ten seconds to fully boot a computer even when using BIOS—which is slower than UEFI.

Gentoo’s resource usage is always surprisingly low.
I rarely ever exceed one gigabyte of memory usage even with many windows and browser tabs open.
Since the file size of customized binaries is smaller than those of prebuilt binaries, you will notice more free disk space when using Gentoo.
Just make sure to clean out your source code files and prebuilt binary packages.
You can do so with [eclean](https://packages.gentoo.org/packages/app-portage/gentoolkit).
You will also be able to complete the same tasks with a slower CPU frequency, saving electricity and money.
I notice that it is generally much snappier in every way than any other operating system I have ever used.

# Versatility

Gentoo Linux is versatile because it can do anything on any type of computer.
It is currently available for nine different CPU architectures ([Gentoo, 2021a](#ref-gentoohandbook-main)).
You can install Gentoo on anything between a Raspberry Pi and a supercomputer.
It works equally well for all types of computers because it is optimized for the specific type of computer.
The reason (unlike most original distributions) it has barely any derivatives is that it’s already complete and does not need any major changes.
The only gripe I have with Gentoo is that some of its software—including Portage, is written in Python.
But with the `native-extensions` `USE` flag, Portage will be compiled with native C extensions to speed it up.
Gentoo Linux is the closest thing to a perfect operating system.

# References

<div id="refs" class="references csl-bib-body hanging-indent" line-spacing="2">

<div id="ref-install-gentoo" class="csl-entry">

Al-Zubaidi, Amar. (2022). *How to install gentoo – the efficient way*. <https://amarakon.github.io/amarakon.com/blog/how-to-install-gentoo-the-efficient-way>

</div>

<div id="ref-gentoohandbook-main" class="csl-entry">

Gentoo. (2021a). *Handbook: Main page*. <https://wiki.gentoo.org/wiki/Handbook:Main_Page>

</div>

<div id="ref-gentoo-license-groups" class="csl-entry">

Gentoo. (2021b). *License groups*. <https://wiki.gentoo.org/wiki/License_groups>

</div>

<div id="ref-gentoo-make.conf" class="csl-entry">

Gentoo. (2022a). */etc/portage/make.conf*. <https://wiki.gentoo.org/wiki//etc/portage/make.conf>

</div>

<div id="ref-gentoo-package.env" class="csl-entry">

Gentoo. (2022b). */etc/portage/package.env*. <https://wiki.gentoo.org/wiki//etc/portage/package.env>

</div>

<div id="ref-best-linux-distro" class="csl-entry">

Smith, Luke. (2018). *What is ‘the best’ linux distro?* <https://lukesmith.xyz/blog/what-is-the-best-linux-distro>

</div>

<div id="ref-desktop-os-marketshare" class="csl-entry">

Statcounter. (2022). *Desktop operating system market share worldwide*. <https://gs.statcounter.com/os-market-share/desktop/worldwide>

</div>

<div id="ref-wikigentoo" class="csl-entry">

Wikipedia. (2022). *Gentoo linux*. <https://en.wikipedia.org/wiki/Gentoo_Linux>

</div>

</div>
