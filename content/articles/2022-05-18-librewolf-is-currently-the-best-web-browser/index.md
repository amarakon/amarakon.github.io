---
title: LibreWolf is Currently the Best Web Browser
date: '2022-05-18'
slug: librewolf-is-currently-the-best-web-browser
tags: ["www"]
bibliography: ../../../static/bibliography.bib
csl: ../../../static/citations/apa-no-initials.csl
link-citations: true
reference-section-title: References
---

# Qualifications

In order for me to consider them good, web browsers must

1.  not send analytics.
    It should not make analytics either.
    I do not want to hear about how it maintains the software’s survival.
    I genuinely do not care.
    I do not want “bug reports.”

2.  have no home pages. Seriously, I do not want my browser to start on Google.
    The address bar is there for a reason.
    Good luck to people who are too stupid to know how to use it.

3.  respect users’ privacy.
    Web browsers must minimize telemetry as much as possible.
    Sometimes, telemetry is necessary.
    There should not be an abundance of it though.
    The default search engine must be a privacy-respecting one.
    Google and Bing are absolute no-nos, even though they are the two most popular search engines.
    DuckDuckGo recently ruined its reputation by deciding to downgrade “Russian disinformation.”
    It became popular enough to head in the same evil direction as Google.

4.  be hardened if it is a fork.
    If a web browser is a fork of another web browser, it should be *hardened*.
    This means that it should have increased security and privacy whenever possible.
    Obviously, anyone who creates a fork should understand the original source code.
    This makes you have the ability to change anything for hardening purposes.
    If the web browser is completely original, it should be secure to begin with.

5.  be free software.
    To be classified as free software, web browsers must follow the Free Software Foundation’s (FSF) *four essential freedoms* ([GNU, 2021b](#ref-gnu-what-is-free-software)):

    1.  Run the program as you wish, for any purpose.

    2.  Study how the program works, and change it so it does your computing as you wish.
        Access to the source code is a precondition for this.

    3.  Redistribute copies so you can help others.

    4.  Distribute copies of your modified versions to others.
        By doing this you can give the whole community a chance to benefit from your changes.
        Access to the source code is a precondition for this.

    At the very least, the web browser must be open-source.
    It should be free software too though.

6.  be regularly maintained and have excellent documentation.

# Web Engines

The two most popular web engines, Chromium and Gecko, are bloated.
There are alternative and more minimal web engines such as WebKitGTK and QtWebEngine.
There are also decent web browsers based on these web engines.
But the problem is that they are just not usable enough yet.
They are too limited and especially too slow.
Chromium is faster than Gecko but only by a little bit.
The speed difference between Chromium and Gecko are unnoticeable most of the time.
But Chromium is made by Google.
Just like all software made by Google, Chromium is garbage.
The explanation for why is for another article though.
**For now, the best browser must use the Gecko web engine.**

# IceCat

GNU IceCat—as opposed to Mozilla Firefox—is by far the most privacy-respecting browser out there.
It is based on Firefox, but **hardened to the extreme**.
It comes preinstalled with LibreJS, HTTPS Everywhere, SpyBlock, and AboutIceCat ([GNU, 2021a](#ref-gnuzilla)).
LibreJS is actually developed by the GNU Project, its purpose is to block proprietary JavaScript.
LibreJS is only available for Firefox-based browsers.
HTTPS Everywhere is a Firefox add-on that encrypts your communications with many major websites, forcing the use of HTTPS instead of HTTP.
SpyBlock blocks privacy trackers and it is also an ad blocker.
It does not block ads for the purpose of not seeing them, it blocks ads to increase privacy.
AboutIceCat adds an `about:icecat` webpage which obviously gives information about IceCat.

There are two reasons as to why IceCat is not the best web browser.
First, IceCat is not accessible enough.
Actually installing and using IceCat is difficult to get into.
The latest binaries, available on [ftp.gnu.org](https://ftp.gnu.org/gnu/gnuzilla/), are out of date.
The only way to get the most up-to-date version is by compiling it.
Second, IceCat is **hardened to the extreme**.
This is good for privacy, but it is not practical.
Many regular tasks you would want to do on a web browser are impossible.
You cannot shop, watch YouTube or Netflix, or generally use websites that have a bit of JavaScript.
You can slightly *deharden* it, but that would defeat its purpose.
**If you can compile it and use it fine, IceCat is the best web browser.**
Otherwise, LibreWolf is a better option.

# LibreWolf

Using the six things that make a good web browser I talked about before, I will argue that LibreWolf is the best.
[LibreWolf](https://librewolf.net/)

1.  does not send analytics.
    It does not make analytics either.
    LibreWolf used to have the area in the settings page where it asks to send analytics, but that was grayed out from the beginning.
    Recently, LibreWolf removed that area completely.
    Not only does it not send or make analytics by default, it does not even give you the option to, because it knows that it should not do so.
    Clearly, LibreWolf is showing that a project does not need analytics to survive.
    Do not fall for any of the sob stories you see elsewhere.

2.  has no home pages.
    By default, LibreWolf has a blank page (`about:blank`) as the homepage.
    This is what all web browsers should do.

3.  respects users’ privacy.
    LibreWolf minimizes telemetry: It has no experiments, adware, annoyances, or unnecessary distractions.
    The default search engine is DuckDuckGo.
    Unfortunately, DuckDuckGo is no longer a viable search engine because it betrayed users’ trust.
    I hope that LibreWolf changes the default search engine to something more private, like Startpage.
    DuckDuckGo is obviously better than Google though.
    But even Bing is better than Google.
    LibreWolf does include a variety of search engine options, including Startpage, Searx, Qwant.

4.  is hardened.
    LibreWolf is a fork of Firefox.
    It maximizes privacy without sacrificing usability.
    It is basically just as usable as Firefox, but more private.
    Simultaneously, it is almost as private as IceCat, but a lot more usable.
    LibreWolf even adds extra options that you do not see in Firefox.
    In the settings page, there will be an extra “LibreWolf” section for LibreWolf specific settings.

5.  is free software.
    LibreWolf is licensed under the GNU General Public License (Version 2) (GPL-2).
    This is a free software license.
    Since it is licensed under a free license, it follows the FSF’s four essential freedoms.
    It is of course also open-source.

6.  is regularly maintained and has excellent documentation.
    LibreWolf is always built from the latest Firefox stable source.
    It is updated almost as often as Firefox itself is.
    Its [documentation](https://librewolf.net/docs/faq/) is no joke even better than Firefox’s documentation.
    It explains all of the features of LibreWolf and instructions on how to turn them off if you do not want them.
    As a bonus, it also includes recommended Add-ons.

# References

<div id="refs" class="references csl-bib-body hanging-indent" line-spacing="2">

<div id="ref-gnuzilla" class="csl-entry">

GNU. (2021a). *GNUzilla and IceCat*. <https://www.gnu.org/software/gnuzilla/>

</div>

<div id="ref-gnu-what-is-free-software" class="csl-entry">

GNU. (2021b). *What is free software?* <https://www.gnu.org/philosophy/free-sw.en.html>

</div>

</div>
