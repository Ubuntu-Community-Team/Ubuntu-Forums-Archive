---
title: "HELP! - Ubuntu Not Loading Correctly - HELP!"
date: 2008-06-22
forum: x86 64-bit Users
---

### Post by psykospun on 2008-06-22
[SIZE="4"]ok. here's my problem. I restarted my computer, like normal. everything was hunky-dory. just fine. came to the boot screen, like normal. went to log on to Ubuntu and my menu bars never loaded up. (not normal) "where is my menu?" i was thinking. no cube either. just my wallpaper and a few icons on the desktop.

I tried booting into recovery mode, but it never did much help for me, knowing that i only have a beginners level skill at this OS.

I need help from an expert to load up normally. Please Help.[/SIZE]


**Ubuntu 7.10 amd64**- gutsty gibon _upgraded_ to **Ubuntu 8.04** Hardy Heron.

---

### Post by psykospun on 2008-06-23
[COLOR="Red"]Post moved to General Help.[/COLOR]

[http://ubuntuforums.org/showthread.php?t=837941]("http://ubuntuforums.org/showthread.php?t=837941")

---

### Post by rbanavara on 2008-06-23
Make sure your graphic driver is properly installed (turn on your restricted drivers). ALso make sure your color depth is atleast 24bits:

===
Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    [COLOR="Red"]24[/COLOR]
===

---

