---
title: "WineHQ with Ubuntu 14.10?"
date: 2015-04-22
forum: Wine
---

### Post by bob_smith3 on 2015-04-22
Hi all;
I am new to Ubuntu and Linux, so please excuse any false views I have. So I recently installed Ubuntu 14.10, and now I'm looking for a compatible version of WineHQ. However, the binaries are given only for 14.04 LTS version. Will they be compatible with 14.10? I believe the latest Ubuntu versions can run software designed for older versions, but I just want to clarify this.
[https://www.winehq.org/download/](https://www.winehq.org/download/)
All input is greatly appreciated!
Thanks,
Bob Smith

---

### Post by TheFu on 2015-04-22
Support for 14.10 is only 6-9 months. Most people new to Linux and non-developers [should run only the LTS releases]("http://blog.jdpfu.com/2013/07/19/why-ubuntu-users-should-run-an-lts-release") - IMHO. After all, being forced to load a new OS every 6 months isn't what most people want.  5 yrs, yes, that is much better. Generally, I will switch from LTS to LTS every 2 years in June.  I can say today that the plan is to load 16.04 in June of 2016. I will skip all odd-year (15.xx, 17.xx, ...) and October (xx.10) releases. Support on those are too short for my needs.  Not all released versions are created equal.

WineHQ is just a website with information about running specific programs under WINE.  Don't have any idea what "binary" you are talking about - definitely don't download and install anything from there.  Install **wine** and the **winetricks** packages from the repo and follow the appdb at winehq instructions to get any specific win32 programs working. Don't expect most programs to work perfectly and always expect some parts of those programs to not work at all. Hopefully, the non-working parts aren't important.

You shouldn't be loading any programs from outside the package manager. This isn't Windows. We avoid "setup.exe" type installations for many reasons - usually because they break the easy OS and application patching that APT provides.  Either use Software Center, Synaptic, apt-get or aptitude to load programs.  Avoid downloading a .deb file or tgz or tar.gz or similar methods. These will put you back into the MSFT software management mode, which is one of the best reasons to stop running Windows, IMHO.

[http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) has some links to resources to help you learn the most important things about Linux ASAP. For you, the first 4 links in the list and the **Ubuntu Desktop Guide** a little farther down the page would be good.  Most of the links are 3 min of reading - not long. Definitely check out the **Linux for Windows Users** link there. It explains things important to know and will end some misconceptions/assumptions that people only familiar with MS-Windows bring with them.

Welcome to Linux. If nothing else, Linux is flexible in the extreme.  There are usually 10 different ways to do anything, sometimes 1000 different ways.

---

### Post by Bucky Ball on 2015-04-22
Yep, just a slight confusion. ;)

Open Software Centre and install wine and winetricks, as advised by TheFu. The link you gave is telling you to install the same, but from their website. Much better to get it from the official repos where possible, and always check there first. Good luck.

---

### Post by bob_smith3 on 2015-04-22
Thank you so much both of you.

> [B][COLOR=#000000]Support for 14.10 is only 6-9 months. Most people new to Linux and non-developers [/COLOR][should run only the LTS releases]("http://blog.jdpfu.com/2013/07/19/why-ubuntu-users-should-run-an-lts-release")[COLOR=#000000] - IMHO. After all, being forced to load a new OS every 6 months isn't what most people want. 5 yrs, yes, that is much better. Generally, I will switch from LTS to LTS every 2 years in June. I can say today that the plan is to load 16.04 in June of 2016. I will skip all odd-year (15.xx, 17.xx, ...) and October (xx.10) releases. Support on those are too short for my needs. Not all released versions are created equal.[/COLOR]

[COLOR=#000000]WineHQ is just a website with information about running specific programs under WINE. Don't have any idea what "binary" you are talking about - definitely don't download and install anything from there. Install [/COLOR][/B]**[B]wine and the **[B][B]winetricks packages from the repo and follow the appdb at winehq instructions to get any specific win32 programs working. Don't expect most programs to work perfectly and always expect some parts of those programs to not work at all. Hopefully, the non-working parts aren't important.

You shouldn't be loading any programs from outside the package manager. This isn't Windows. We avoid "setup.exe" type installations for many reasons - usually because they break the easy OS and application patching that APT provides. Either use Software Center, Synaptic, apt-get or aptitude to load programs. Avoid downloading a .deb file or tgz or tar.gz or similar methods. These will put you back into the MSFT software management mode, which is one of the best reasons to stop running Windows, IMHO.

[http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) has some links to resources to help you learn the most important things about Linux ASAP. For you, the first 4 links in the list and the [/B]**[B]Ubuntu Desktop Guide a little farther down the page would be good. Most of the links are 3 min of reading - not long. Definitely check out the ****[B]Linux for Windows Users**** link there. It explains things important to know and will end some misconceptions/assumptions th**at people only familiar with MS-Windows bring with them.

Welcome to Linux. If nothing else, Linux is flexible in the extreme. There are usually 10 different ways to do anything, sometimes 1000 different ways[/B][/B][/B][/B]**[B][B][B].**[/B][/B][/B]

Thank you TheFu for this amazing introduction!
So the way I understand, the Software Centre is simillar in concept to the Google Play Store in Android? All the programs come from it? Also  I had the 14.04.2 LTS version, but unfortunately, the wi-fi connectivity had issues, so I upgraded to the latest 14.01 version, and all seems good now. I don't mind re-installing the latest release every 6-9 months.

So the apt-get method for 14.04 is.:
[COLOR=#333333][FONT=arial]
```
[/FONT][/COLOR][COLOR=#333333][FONT=arial]sudo add-apt-repository ppa:ubuntu-wine/ppa[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]sudo apt-get update[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]sudo apt-get install wine1.7 winetricks[/FONT][/COLOR]
```


 Will this same method work for 14.10?

> [COLOR=#000000]Yep, just a slight confusion. [/COLOR]:wink:

[COLOR=#000000]Open Software Centre and install wine and winetricks, as advised by TheFu. The link you gave is telling you to install the same, but from their website. Much better to get it from the official repos where possible, and always check there first. Good luck.[/COLOR]

Short and sweet and to the point! Thanks!

---

### Post by Bucky Ball on 2015-04-23
That's it. As I mention, avoid installing third-party PPAs where possible. Wine and winetricks are in the official repos already. Get them from there and forget the PPA. ;)

---

### Post by TheFu on 2015-04-23
Software Center is just an interface into APT.  APT is the real genius here.  There are multiple interfaces into APT and they all can be used, depending on the task at hand. I've **never** used Software Center - not once - so I can only rely what I've heard. It dumbs down the package interface and hides lots of very useful packages from end-users. Canonical isn't dumb, so there must be a place for SC - just not for me. I'm old, grumpy, and don't like change, especially when it removes features that I've learned to love.  APT has been used with Debian and now Ubuntu since the 1990s - I think it is the original package manager since we shipped tgz files around before that.

Never heard of 14.01. There was a release in January?

Bucky Ball says you don't need to use the PPA, so I wouldn't.  But if you've read my articles, then you know that using the PPA is 3rd in my list of good ways to get software under central APT management for Debian-based distros.

Everyone says they are willing to re-install every 6+ months ... then they come back here in 2 yrs looking for help for a release that hasn't been supported in all that time. Just sayin'.  It is your choice and there are probably options to make wifi work under 14.04, as things are backported to the LTS releases - there's a hardware compatibility kernel with drivers that gets backported for this reason. [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) explains.

---

### Post by bob_smith3 on 2015-04-23
Sorry, I meant to say 14.10. Anyways, 15.04 has been released today and I upgraded.

So that means the "sudo apt-get" command directly downloads the libraries, and the software centre is more of a GUI to access the APT?

---

### Post by TheFu on 2015-04-23
They are each package managers and pull the packages from exactly the same places and install them on your machine(s) in exactly the same way - at least for 99.9999% of the software that most end users care about.  They are just different interfaces into the APT and repository databases.  I'm over simplifying of course.  

If you care more - you can google for better comparisons.

My next install will be 16.04. Currently running 14.04 myself. Newer isn't always better, but I do appreciate people like you who do.

---

