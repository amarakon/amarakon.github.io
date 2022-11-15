---
title: Gentoo Linux Should be Approved by the Free Software Foundation
date: '2022-05-05'
slug: gentoo-linux-should-be-approved-by-the-free-software-foundation
tags: ["foss", "fsf"]
bibliography: ../../../static/bibliography.bib
csl: ../../../static/citations/apa-no-initials.csl
link-citations: true
reference-section-title: References
---

Gentoo Linux is a 100% free operating system.
All of its source code is publicly available on GitHub, meaning that it’s open-source.
It is licensed under a free license: GNU General Public License (Version 2).
It does not include any preinstalled proprietary software.
Its package manager, Portage, blocks proprietary software against the user’s will by default.
All of these reasons prove that is a completely free operating system that is against the use of proprietary software, so it should be in the Free Software Foundation’s (FSF) [list of free Linux distributions](https://www.gnu.org/distros/free-distros.en.html).

# Free System Distribution Guidelines ([GNU, 2022b](#ref-gnu-fsdg))

The GNU free system distribution guidelines (GNU FSDG) is an article supported by the FSF.
It includes the guidelines that a distribution must follow in order to be endorsed by the FSF.
Gentoo Linux easily follows these guidelines and I will prove it.

## Complete distributions

Only distributions that are complete in themselves and ready to use can make the list.
The distribution should be self-hosting, meaning that the distribution cannot include free software that can only be built by using proprietary software.
“If a distribution is incomplete—if it requires further development, or presupposes installing other software as well—then it is not listed here, even if it is free software.”
Even though Gentoo’s installation process is minimal, it still includes all the software necessary to install it.
It does not include any software that can only be built by using proprietary software.
Gentoo is complete, fully developed, and never presupposes installing other software.

## License rules

> All information for practical use in a free distribution must be available in source form.

> The information, and the source, must be provided under an appropriate free license.
> We evaluate specific licenses and list our determinations in our license list.

Like mentioned in the opening paragraph, all of Gentoo’s source code is licensed under GPL-2.
GPL-2 is obviously an appropriate free license because it is made by the GNU Project which is supported by the FSF.
GPL-2 is part of the [official GNU license list](https://www.gnu.org/licenses/license-list.html).

## Non-free firmware

> Some applications and drivers require firmware to function, and sometimes that firmware is distributed only in object code form, under a nonfree license.
> We call these firmware programs “blobs.”
> On most GNU/Linux systems, you’ll typically find these accompanying some drivers in the kernel Linux.
> Such firmware should be removed from a free system distribution.

Since Gentoo uses a minimal command-line installation process, no blobs are included in the operating system.
The `linux-firmware` package is not installed—actually, it is blocked.
Gentoo blocks all proprietary program packages, but obviously that can be changed with any operating system—even those that are approved by the FSF.

## Non-functional data

> Data that isn’t functional, that doesn’t do a practical job, is more of an adornment to the system’s software than a part of it. Thus, we don’t insist on the free license criteria for non-functional data.

Gentoo is the most minimal and best functioning distribution there is.
There is no line of code in the Gentoo source that is unnecessary.

## Trademarks

> Trademarks are associated with some software.
> For example, the name of a program may be trademarked, or its interface may display a trademarked logo.
> Often, the use of these marks will be controlled in some way; in particular, developers are commonly asked to remove references to the trademark from the software when they modify it.

[Gentoo’s trademark](https://www.gentoo.org/inside-gentoo/foundation/name-logo-guidelines.html) is completely reasonable.
Its type of trademark is generally accepted in the free software demographic.

## Documentation

> All the documentation in a free system distribution must be released under an appropriate free license.
> Additionally, it must take care not to recommend nonfree software.

While Gentoo does have wiki pages on proprietary software, it does not recommend them.

## Patents

> We don’t generally ask free system distributions to exclude software because of possible threats from patents.

I do not understand why this section is in the FSDG.
This automatically qualifies every distribution.

## No malware

Gentoo does not contain any digital rights management, back doors, or spyware.

## Commitment to correct mistakes

According to Wikipedia ([2022](#ref-wikigentoo)), in 2018 the Gentoo GitHub repository was hacked because an attacker was able to deduce the password.
Gentoo immediately responded by improving their security practices to prevent this from happening again.
Gentoo has made no other major mistakes.

## Maintenance

Even though it is not popular, Gentoo is still maintained.
Many new packages and wiki pages are constantly being added every day.

## Name confusion

> We will not list a distribution whose name makes confusion with nonfree distributions likely.
> For example, if Foobar Light is a free distribution and Foobar is a nonfree distribution, we will not list Foobar Light.
> This is because we expect that the distinction between the two would be lost in the process of communicating the message.

This is pretty easy to explain.
There are no proprietary distributions with an almost identical name to Gentoo.
There is not **any** distribution like that for that matter, free or non-free.

## Please teach users about free software

Gentoo obviously teaches users about free software.
It is the perfect distribution for learning.
Since it requires effort and knowledge, all users will naturally learn plenty of information about Linux and free software in general.
The Gentoo wiki is also my favorite wiki website.
It is significantly more detailed than any other distribution’s wiki.

## Please avoid repeating propaganda and confusion

> Please see our list of [words to avoid](https://www.gnu.org/philosophy/words-to-avoid.html), which are either biased, misguided or misleading, and try to avoid them in your public statements and discussions with the public.

Gentoo (wiki) uses good vocabulary and does not use words incorrectly, does not spread any propaganda, and does not mislead people.

# Free Software Foundation’s Justification

The Free Software Foundation justifies not including Gentoo Linux on their list of free Linux distributions with the following short statement: “Gentoo includes installation recipes for a number of nonfree programs in its primary package system” ([GNU, 2022a](#ref-gnu-explaining)).
This is true, Gentoo does include non-free program packages in its primary package system.
But this should not disqualify Gentoo from being approved by the FSF.
First, the Gentoo wiki does not endorse the installation of these packages.
It has webpages about these packages but they are never unreasonably referenced anywhere, let alone endorsed.
All of the applications and tools recommended and endorsed by Gentoo wiki are free ([Gentoo, 2022a](#ref-gentoo-recommended-applications), [2022b](#ref-gentoo-recommended-tools)).
Even if the Gentoo wiki did endorse proprietary software, that would not matter because then Gentoo wiki is not part of the Gentoo operating system.

The GNU FSDG states “The system should have no repositories for nonfree software and no specific recipes for installation of particular nonfree programs ([GNU, 2022b](#ref-gnu-fsdg)).”
Pay attention to the wording.
Gentoo has no repositories **for** non-free software, but it has a repository **with** non-free software.
That is an important distinction.
Like I pointed out earlier, the actual operating system does not contain specific recipes for the installation of particular non-free programs, but the Gentoo wiki reasonably does.
It does not matter whether it is the official Gentoo wiki that includes these recipes or a third-party article.
Neither are included in the operating system.

If Gentoo does not follow the GNU FSDG, then neither do the supposedly free distributions endorsed by the FSF.
It is possible and easy to add proprietary software in these distributions by adding a third-party repository.
The FSF clearly thinks that any distribution which makes it possible to install proprietary software should be disqualified.
I understand this view, but that should make all of the currently approved distributions disqualified as well.
True freedom is giving the user the choice to make responsible and good decisions without any unreasonable authority.
Gentoo Linux is a perfect example of an operating system that gives its users true freedom.

**[energyman76b](https://forums.gentoo.org/profile.php?mode=viewprofile&u=17194&sid=2b558d9c692f1caa91e4c63b0ec334a8) on [Gentoo forums](https://forums.gentoo.org/viewtopic-t-791603-start-25.html):**

> The FSF hates user freedom.

# References

<div id="refs" class="references csl-bib-body hanging-indent" line-spacing="2">

<div id="ref-gentoo-recommended-applications" class="csl-entry">

Gentoo. (2022a). *Recommended applications*. <https://wiki.gentoo.org/wiki/Recommended_applications>

</div>

<div id="ref-gentoo-recommended-tools" class="csl-entry">

Gentoo. (2022b). *Recommended tools*. <https://wiki.gentoo.org/wiki/Recommended_tools>

</div>

<div id="ref-gnu-explaining" class="csl-entry">

GNU. (2022a). *Explaining why we don’t endorse other systems*. <https://www.gnu.org/distros/common-distros.en.html>

</div>

<div id="ref-gnu-fsdg" class="csl-entry">

GNU. (2022b). *Free system distribution guidelines*. <https://www.gnu.org/distros/free-system-distribution-guidelines.en.html>

</div>

<div id="ref-wikigentoo" class="csl-entry">

Wikipedia. (2022). *Gentoo linux*. <https://en.wikipedia.org/wiki/Gentoo_Linux>

</div>

</div>
