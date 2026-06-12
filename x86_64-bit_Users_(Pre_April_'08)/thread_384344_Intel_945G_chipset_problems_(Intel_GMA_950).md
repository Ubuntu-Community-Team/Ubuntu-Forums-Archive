---
title: "Intel 945G chipset problems (Intel GMA 950)"
date: 2007-03-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by craiger316 on 2007-03-14
I have this problem where when gdm (Gnome Desktop Manager) is stopped it halts my entire system.  I can never reboot cleanly, which is troubling.

Typically from within Gnome if I Logout, Restart or Shutdown it will just take me to a black screen and halt.  If I try to change video resolutions it also halts, but typically with some artifacts on the screen.

My motherboard is the Asus P5L-VM 1394:
[http://www.asus.com/products4.aspx?modelmenu=1&model=1324&l1=3&l2=11&l3=194](http://www.asus.com/products4.aspx?modelmenu=1&model=1324&l1=3&l2=11&l3=194)

If I Ctrl-Alt-Fx into a tty and try to manually shutdown gdm, it flashes some (what appear to be) stack-trace type information (mostly it looks like register values) and then halts.

I have tried the "915resolution" hack but to no avail :(

The driver that X is using is the "i810" driver.

Anyone have a solution for this?  I am running the 64bit alternate Edgy distro.  Even if it means settling for a vanilla driver, I don't care, this box is a server but I still wish to use Gnome from time to time when I'm in the office, I just want it to be able to shutdown properly.

Thanks

---

### Post by bibleman on 2007-03-14
I have the same problem. I even have the same hardware. I can never get a clean shutdown, logout, reboot or anything. When I did a manual shutdown from the terminal it was obvious that there is a kernel panic/dump. If there is any other information please ask for it and it shall be supplied.

---

### Post by craiger316 on 2007-03-14
bibleman, I'm both happy and sorry you are experiencing the same problems.  At least I know I'm not alone now...

Hopefullly someone will have gotten past this.

---

### Post by bibleman on 2007-03-14
It is irritating to have to manually press the power button to shutdown but I was getting used to it. I have had similar problems with other distros like fedora, and gentoo. I was searching these forums for this problem and I was glad(well sort of) to find someone else with the same problem.

Unfortuantely for me I just had a failure with my network card and now I cannot access the internet from that computer. It could even possibly be a bad mb because I tried a PCI network card that wouldn't work either. I still want to see if there are any suggestions from those who know more about the 64bit version of ubuntu.

---

### Post by craiger316 on 2007-03-26
Just a friendly *bump* to see if anyone has had, or has solved this problem.

Thanks.

---

### Post by DR4545 on 2007-03-26
Well, I haven't installed yet but the "Check CD for defects" won't finish for me (I checked the MD5, it's fine)  And, I have an Intel 945 chipset.

---

### Post by craiger316 on 2007-03-26
> **DR4545 said:**
> Well, I haven't installed yet but the "Check CD for defects" won't finish for me (I checked the MD5, it's fine)  And, I have an Intel 945 chipset.

Thanks, let us know.  I know this sounds cliche, but did you try burning the iso at a low speed (8x, 4x if it will let you).  It does actually seem to make a difference.

---

### Post by dburnett77 on 2007-03-30
I just got a new wide screen monitor, and was having problems with the default driver for the Intel 950.

I saw somewhere to download the newer driver "xserver-xorg-video-intel" via Synaptic.  I then changed the entry in xorg.conf in the Driver section from "i810" to "intel", and I got all the resolutions I needed, plus the correct refresh rates.

I don't know if this will help, but it worked for me.

---

### Post by lukemh on 2007-04-10
i have the same motheboard, i am a ubuntu/linux new new newbie and i have no problems shutting down through the red shutdown button

---

### Post by craiger316 on 2007-04-21
What version of Ubuntu?  Edgy or Fiesty?

---

### Post by eAspenwood on 2007-05-18
Has anyone been able to resolve this?

I am having the same exact problems as craiger316 with my 945GZ chipset.

I'm only having this problem with 64 bit linux w/ both GNOME and KDE.  Worked perfectly fine in 32bit.  Also, I'm running CentOS 5 linux. I realize this is an Ubuntu forum, but this is the only place I could fine with the same exact problem.

I tried switching the video driver from "i810" to "intel", but that did not help.

-- J.

---

### Post by eAspenwood on 2007-05-18
The workaround mentioned here resolved the issue for me:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/34697](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/34697)

Workaround is to enter  BIOS setup and set:

Advanced -> CPU Configuration -> Execute Disable Function = Enabled

Worked like a charm. Finally! That only took 2 days to resolve....

-- J.

---

### Post by craiger316 on 2007-05-22
Wow, I'll have to give that a try!  Although now I've been running on Vista x64, I'd have to have a compelling enough reason (other than windows sucks ;) to try again (i.e. getting Xen to actually work)

LOL, I love that one guy's comment on Launch Pad "It has been fixed in kernel some time ago". Uhmmm, bzzzzzt wrong!  Unless "some time ago" means within months, and if that is the case Fiesty should work just fine without the bios fix.  Anyone try it with Fiesty?

Thanks.

---

### Post by dabl on 2007-05-22
Here's a bit of info on Intel video chips and drivers:

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsIntel](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsIntel)


Looks like "shared memory" may be relevant to getting these things working right ....  :)

---

### Post by julius malchovitch on 2007-05-25
Hello everybody, just as an information, does anyone of you have [this bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/111257") with the intel 950gma graphics card?

Thanks,
julius

---

