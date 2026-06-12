---
title: "Open Office and printing"
date: 2005-06-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by daFool on 2005-06-06
How to get it to work?

Only printer showing is generic one and that does not work. Every other application tried prints nicely. I've tried upgrading to new pango-libs as mentioned in [bug 6762](https://bugzilla.ubuntu.com/show_bug.cgi?id=6762) from breezy but that only fixes crashing oopadmin. How do I get OO to print or is even possible?

Probably [bug8663](https://bugzilla.ubuntu.com/show_bug.cgi?id=6883) is somehow related to this problem and instructions given it would fix it but I have a feeling that they are not end user instructions...
 :???:

---

### Post by tonym on 2005-06-07
This problem has been there for some time and there seems to be no sign of a fix.  I know its rather negative but I have gone back to i386 because of this.

---

### Post by Optimal Aurora on 2005-06-07
Yes even I have experienced the problem and I don't know how to get it working, sorry... Just wanted to let you know you aren't the only one that experiences this problem...

---

### Post by Optimal Aurora on 2005-06-07
Hay yal...
I found out that you have to upgrade the openoffice.org and them to the breezy and they have fixed that problem with at least my printer working... It stills calls my printer Generic printer but it does print...

---

### Post by daFool on 2005-06-08
[QUOTE=Optimal Aurora]Hay yal...
I found out that you have to upgrade the openoffice.org and them to the breezy and they have fixed that problem with at least my printer working... It stills calls my printer Generic printer but it does print...[/QUOTE]

How did you do that? I'm complete newbie when apt-get, dselect and pals are concerned.

---

### Post by Optimal Aurora on 2005-06-11
You may not want to try because the breezy update updated other things as well and some of them didn't work well with my system and cause me to have to reinstall hoary...

---

### Post by Optimal Aurora on 2005-06-12
Oh and hay someone on another thread I started about the printer problem said that you may have to wait until v 2.something is out because no one is doing anything about this problem in v 1.1.something...

here you can read this like that Jarz Corp left me... [http://www.ubuntuforums.org/showthread.php?t=16266&highlight=openoffice+cups](http://www.ubuntuforums.org/showthread.php?t=16266&highlight=openoffice+cups)

---

### Post by hva on 2005-06-13
try removing openoffice.org-gtk-gnome package: my cups printers showed up in printing dialog and work perfectly.

---

### Post by wiraone on 2005-06-13
[QUOTE=hva]try removing openoffice.org-gtk-gnome package: my cups printers showed up in printing dialog and work perfectly.[/QUOTE]
 Did as the above, my printer is showing up but I still couldn't print out anything from OOWriter.

---

### Post by Mais on 2005-06-26
[QUOTE=hva]try removing openoffice.org-gtk-gnome package: my cups printers showed up in printing dialog and work perfectly.[/QUOTE]

Didn't work for me at all. OO.o still showed only a generic, still no printing capability.

---

### Post by Optimal Aurora on 2005-06-28
> Found a nice way to get x86_64 OOo 2.0 builds.

[ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/ooo64bit02/Build-3/](ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/ooo64bit02/Build-3/) has a .rpm which will Alien perfectly, and install to /opt/ using dpkg. Using it now

Sooo much better than OOo 1.1.3 

This is the only way I got mine to print in OpenOffice and it is quiet stable and works really good on my system...

to install go to the RPMS directory in the download (when you are in a terminal that is) and type in alien -i openoffice* 

this will install every one except the testtool which is no biggy...

---

### Post by estel on 2005-06-28
Hmm, I've just discovered that I can't save in that OOo2.0 build

---

### Post by Big Venus on 2005-06-29
Isn't that not the most up to date version... Meaning the openoffice is now at 1.9.112

---

### Post by estel on 2005-06-29
[QUOTE=Big Venus]Isn't that not the most up to date version... Meaning the openoffice is now at 1.9.112[/QUOTE]
 Yes, but there aren't any more than a couple of bug fixes between the betas. You're usually safe not upgrading the beta for about a month or two. Anything from .96 onwards was really very stable.

---

### Post by manicka on 2005-06-29
I used the info at this thread to get the latest beta working. )read the entire thread as some of the links have changed)

[http://www.ubuntuforums.org/showthread.php?t=30866&highlight=openoffice+beta](http://www.ubuntuforums.org/showthread.php?t=30866&highlight=openoffice+beta)

Cups printer is recognised without problem.

I also removed 1.1.3. Don't know if that makes a difference

---

### Post by fozner on 2005-07-30
I had this problem tonight with Fedora Core 4 and I got it working by enabling some services that I had disabled earlier.  I don't know exactly which ones are necessary and which ones are not but these are the ones I enabled

cups
cups-config-daemon
mdmpd
messagebus
snmpd
smb
snmptrapd

There may be others that when disabled will stop the useful functioning of a printer and, like I said, some of the ones I listed may be unnecessary depending on whether you are using a network printer (like my HP4550N) or something else.  Re-installing or upgrading will of course re-enable the necessary services but for some it will be faster to take a look at system-config-services.

---

