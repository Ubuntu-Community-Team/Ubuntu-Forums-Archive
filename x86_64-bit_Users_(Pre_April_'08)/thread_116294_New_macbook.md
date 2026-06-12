---
title: "New macbook"
date: 2006-01-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by Chayak on 2006-01-12
Well if anyone watched the keynote the new apple systems are quite nice.  A dual core laptop that size.  PPC disks will no longer work on them and it makes me wonder if the x86 disks will.  In all honesty I don't think I'll be installing linux on that machine.  The pro apps are too good to pass up.  Anyone else?

---

### Post by Down8ve on 2006-01-12
Much agreed.  I have been using Macs for some time in my work and looked at Fedora 4, Ununtu 5.10 and Yellow Dog.  The only reason I was tempted to switch to Linux was to speed up my old hardware, but these desktops always managed to make me miss OSX as much as Windows did.

Now that they are making speedy hardware I shall place my order next week.

DSM

---

### Post by shawn12345 on 2006-01-12
i find myself tempted by OSX every now and again but when i do i only last a few weeks with it. I find the lack of interface customization,  and performance irritating....not to mention the eye candy stuff for home users feels silly.

 I like the style of the hardware, various built in ports, and the sleep mode is reliable. Thats it. I prefer the flexability of being able to use whatever hardware i want so linux allows that.

Of course in my work i deal with science data not presentatiton. Now if i did heavy video or graphics or alot of presentations I would use OSX.

linux rules. its freedom.

---

### Post by AndrewStout on 2006-01-12
I'd love to hear if anyone has any info (or well-grounded speculation) about the new MacBooks (or new iMacs) and linux.  I inferred that Ubuntu PPC will not apply to x86-based Macs; it would be nice if plain-old x86 Ubuntu did, since that's the most complete version (pesky stuff like Flash, Java, etc.)--and, of course, I won't buy a machine that no version of Ubuntu will run on.  Assuming they'll run x86 Ubuntu, the new MacBooks look pretty snazzy--definitely my choice next time I can justify buying a new laptop.

I've been trying to make the transition from MacOS to Linux for years--first linux on PPC hardware was too rough (and I didn't have the patience); now I've got an x86 desktop that runs Ubuntu most of the time.  I need linux for my research work (the tools that I need don't quite play nice on OS X yet), and it's nice to have the option to customize everything; I like MacOS for its ease of use and polish.  OS X Just Works--except when it doesn't: it's nice not to have to do several hours of research and blind tweaking to get something basic (sound, for instance) to work; but it's infuriating not to be able to easily install a tool (matplotlib, for instance).  So for now, I do both.

I look forward, hopefully in the near future, to the time when I can triple-boot Ubuntu, OS X, and the operating system that game manufacturers seem to think is the only one that matters, both on a MacBook and on my self-built desktop--and in the more distant future, to the utopian situation when one operating system will have the flexibility of linux and the just-works-ness of OS X, with all the software I need or want.

---

### Post by shawn12345 on 2006-01-13
I must admit also i switched to ubuntu because of serial numbers and cdroms and software. Aside from my pismo i change my other computer alot. I hate entering in serial numbers especially windows ones and dont like having cdroms sitting around taking up space or looking messy.

My office stays much neater. New computer, 1 cd (ubuntu), rest is ubuntu install or downloadable or apt-get

---

### Post by ssam on 2006-01-13
the first stubling block to running linux (or current versions of windows) is that it uses [Extensible Firmware Interface, (EFI)]("http://en.wikipedia.org/wiki/Extensible_Firmware_Interface"), instead of [Open Firmware]("http://en.wikipedia.org/wiki/Open_Firmware") or [BIOS]("http://en.wikipedia.org/wiki/BIOS").

That quite possibly means that current versions of windows and linux won't be able to boot it. although there is the possiblility that apple have included a BIOS compatable mode for booting current x86 operating systems. i have spotted a [claim]("http://xlr8yourmac.com/archives/jan06/011106.html#S20439") that someone booted a windows install cd on an intel mac at the expo, but seen nothing verifiable.

[elilo]("http://elilo.sourceforge.net/cgi-bin/blosxom") is a linux boot loader for EFI. odds are that if you could install a linux based on elilo. or somehow use elilo to boot ubuntu.

once it is booting there might be hardware driver problems. the ATI card will be a likely source of them.

---

