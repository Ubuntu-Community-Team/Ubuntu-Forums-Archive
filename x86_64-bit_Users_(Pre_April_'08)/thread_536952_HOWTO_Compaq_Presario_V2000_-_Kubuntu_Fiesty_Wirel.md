---
title: "HOWTO Compaq Presario V2000 - Kubuntu Fiesty: Wireless, Suspend and More"
date: 2007-08-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by iamnoah on 2007-08-28
I have a Compaq Presario V2000 with an AMD Turion 64, at least that's what the sticker said.  For the most part, the 64 bit version of Kubuntu worked fine for me, but two things didn't work out of the box. 

The first was the wireless. Fortunately, this has been addressed [[COLOR="DarkOrange"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=197102") . You want to take the ndiswrapper route.  After you've run the script, network manager (in the system tray) should work, except for one thing: If you try to connect to an unencrypted AP, it gets stuck at 28%.  To get it unstuck, do this:
```
sudo ifdown eth1
sudo ifup eth1
```
Unfortunately, you'll have to do that every time you reboot.  Suspending to ram and resuming also works, once we've fixed it (next).

The second major issue is suspend to ram (and hibernate), both of which hang on resume.   I followed the instructions  [[COLOR="DarkOrange"]here[/COLOR]]("http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/")
([[COLOR="DarkOrange"]Google Cache[/COLOR]]("http://209.85.165.104/search?q=cache:KfudQZESNAQJ:blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/+ubuntu+suspend&hl=en&ct=clnk&cd=4&gl=us&client=firefox-a") because site was down when I wrote this).  Unfortunately, by themselves, those instructions don't work because the Presario V2000 isn't in the current whitelist (see [http://en.opensuse.org/S2ram](http://en.opensuse.org/S2ram)),  You have to make a minor tweak to the suspend script to force suspend (line 84 needs "-f -a 1").  Corrected scripts are [[COLOR="DarkOrange"]attached[/COLOR]]("http://ubuntuforums.org/attachment.php?attachmentid=41998&stc=1&d=1188412339") (untar in /). In summary: ```
sudo apt-get install uswsusp
sudo tar zxf presario-V2000-hal-scripts.tar.gz -C /
```

Also, after resuming, your sound may have disappeared.  To fix it, restart alsa:
```
sudo /etc/init.d/alsa-utils restart
```
*EDIT: I've added this (without the sudo) to the end of the hal suspend scripts you downloaded above so it should no longer be necessary.*

Now all that's left is to get some 3rd party software working.  I found the following helpful:
[LIST]
[*][[COLOR="DarkOrange"]Installing Flash[/COLOR]]("http://ubuntuforums.org/showthread.php?t=476924")
[*][[COLOR="DarkOrange"]Acrobat Reader[/COLOR]]("http://www.adobe.com/products/acrobat/readstep2.html") - kpdf is lighter weight, but sometimes you have to have it. You'll need to ```
sudo apt-get install ia32-libs-gtk
``` before you run acroread. It fails to load some plugin when it starts, but I haven't had any problems with it.
[*][[COLOR="DarkOrange"]Installing Wine[/COLOR]]("https://help.ubuntu.com/community/WineForAMD64")
[*][[COLOR="DarkOrange"]Fixing Wine[/COLOR]]("http://ubuntuforums.org/showthread.php?t=432604") - helps for some applications. I needed to do it to play [[COLOR="DarkOrange"]Warcraft II[/COLOR]]("http://appdb.winehq.org/appview.php?iVersionId=592") \\:D/ (I'm a medieval man...) You'll need to run winecfg and set Audio Hardware Acceleration to "Emulation" for War2 as well :)
[/LIST]

---

