---
title: "ubuntu on MacBook Pro"
date: 2006-05-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Adam Boettiger on 2006-05-04
I am considering dual-partitioning my MacBook Pro with OS X and ubuntu but have the following questions before I do:

1. Which flavor of ubuntu should I use, the x86 family, i686 kernel?

2. Are there still issues with Airport Extreme not functioning properly with ubuntu?

Thanks in advance for any help or comments.

---

### Post by rado_london on 2006-05-04
As far as I know there still is no official Linux version for macbook. However i think they will release one soon.

---

### Post by Ptero-4 on 2006-05-04
If you have enough space you can install a minimal WinXP with BootCamp and then use the XP's built-in bootloader to boot linux x86 from there.

---

### Post by slux on 2006-05-04
Assuming the AP Extreme chipset is still the same it is on PPC macs, we nowadays have the driver that is a result of a long time of reverse engineering work. It's still rather new so I'm guessing it has some issues and isn't included in Breezy's kernel but it's better than nothing. Of course, with an x86 mac one has the option of using something as ugly as ndiswrapper too...

I'd be interested in hearing what the situation is with the Radeon Mobility x1600? I've read some reports that it isn't supported on Linux right now, at least not by the proprietary ATI drivers... Could anyone fill me in on the exact situation?

I'd venture to guess that Linux on the MacBook Pro will still have some rough edges since full support hasn't usually been available right after release. I'd be glad to be proven wrong though. I guess the power-saving features like hibernation aren't working?

---

### Post by sonofcolin on 2006-05-04
[QUOTE=slux]Assuming the AP Extreme chipset is still the same it is on PPC macs[/QUOTE]
It isn't. It is an Intel chipset.

---

### Post by slux on 2006-05-04
Ah right, that makes sense. Doesn't it have a driver then? Intel's been fairly good with Linux support in the past, including wireless...

---

### Post by sonofcolin on 2006-05-04
Apparently:

Manufacturer: Broadcom Corp.

Chipset Family Type: 802.11 Wireless LAN 
Chipset Family: BCM43xx 802.11abg WLAN Dual-Band 
Chipset: BCM4306 Dual-Band WLAN miniPCI+3 
Hardware IDs: PCI2 (Device ID): 4312 
PCI4 (SubDevice ID): 0007

---

### Post by veggiedude on 2006-05-05
Why? Haven't you considered Parallels Workstation?

---

### Post by peterwor on 2006-05-05
Adam,
I'm running Ubuntu 5.1 on my MacBook Pro right now, using Parellels VM workstation. Its absolutely awesome. I have WinXP, OSX, Ubunto and Solaris installs on mt MBP all running like a charm.
I would take a serious look at [www.parallels.com](www.parallels.com) and this VM software. I'm using Beta 6 and its magic. Does everything I want it to.  Just remember to choose the "debian" linux flavor when you build your VM.

Cheers,
Peter

---

### Post by Ptero-4 on 2006-05-05
Have any of you installed linux on a (W)intelMac. If you have done so. I ask. Does it work? Does the bootloader and linux partitions remain in place after a restart?
Does the hw work normally (provided you have the drivers)? Is it capable of succesfully playing religious/gosspel/christianinc content (videos, music) from the HD or CD without f*ckin' up the computer or breaking the drives?

---

### Post by sciurus on 2006-05-05
I've managed to boot the Dapper Beta 1 live cd on a Macbook Pro. I don't have anything to report that isn't already widely mentioned on sites like [http://www.mactel-linux.org/wiki/Main_Page](http://www.mactel-linux.org/wiki/Main_Page) ,  [http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp) , and [http://cipherfunk.org/diary/archives/monthly/2006-04.html](http://cipherfunk.org/diary/archives/monthly/2006-04.html)

---

### Post by Ptero-4 on 2006-05-07
Well, sciurus. Seems you got luck in there. But keep watching your MacBook's behavior closelly.

P.d: The reason for my questions is that those new Macs have enough parts similar to the ones in beige box Wintels that it warrant the presence of TCPA monitoring and control hardware (look for TCPA + Ptero-4 and you'll eventually get an earlier post of mine about a HP Pavilion my sister used to have which presented the syntoms I asked you about the same moment I tried to put linux on it, situation that I later identified as caused by a TCPA control chip present in the Pavilion CPU and connected to several other of the PC's internal components, the post contains also a link detailing what is TCPA). Now I may be wrong, but the fact that all modern Intel CPU's (The ones obviously Apple uses) have TCPA chips and will fry themselves if they're installed in a computer with no TCPA-enabled internal components, make's me think that Apple will have to put TCPA-enabled components in their Mactels to avoid the flood of complaints from new users saying "Hey, my brand new Macbook pro fried as soon as I turned it on, and it was in battery, no AC", users who obviously doesn't know or understand the suicide tendencies of the Intel CPU inside their new Mac and only want to use the computer.

---

### Post by Adam Boettiger on 2006-05-09
Peter, thanks for the info on Parallels. It looks promising but I cannot get the VM client to go past the screen that says boot disc not found. I did select debian on creation. Will poke around a bit more. If you have any suggestions please contact me.

[QUOTE=peterwor]Adam,
I'm running Ubuntu 5.1 on my MacBook Pro right now, using Parellels VM workstation. Its absolutely awesome. I have WinXP, OSX, Ubunto and Solaris installs on mt MBP all running like a charm.
I would take a serious look at [www.parallels.com](www.parallels.com) and this VM software. I'm using Beta 6 and its magic. Does everything I want it to.  Just remember to choose the "debian" linux flavor when you build your VM.

Cheers,
Peter[/QUOTE]

---

### Post by youbuntoo on 2006-05-09
I agree w/ Peterwor.  Parallels is pretty magical.  It's easy and fast, just the way I like it.  Partitioning seems like more trouble than it's worth to me, when there's an easier solution out there that runs at near native speeds.

---

### Post by rodrigogar on 2006-05-16
dumb question, i am lil familiar with macs, but i want to get the new macbook, cant you just install the ubuntu distro and it will create (or show you to create) the additional partitions and boot menu?

---

### Post by Ptero-4 on 2006-05-16
rodrigogar. The problem with the MacBook is that like all of the other WinTel Macs, they have a special boot system called EFI which is different from the regular BIOS that PC's have. Since gentoo (a f*ckin hard to use linux distro) is the only one that have elilo (a EFI boot loader that still is quite experimental) that is the only distro that can be installed straight into a x86 Mac. ubuntu like the others still doesn't use elilo and thus have to relly on the BIOS emulation that Apple recently introduced in their EFI to install.

---

### Post by rodrigogar on 2006-05-16
thanks for your comprehensive response and not treating me like a ocmplete retard as i want to learn more about mac and linux.

---

### Post by ssam on 2006-05-17
ubuntu has elilo [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=elilo&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=elilo&searchon=names&subword=1&version=all&release=all)

i dont think apple mind if people run linux on their mac, yellowdog are an apple authorised retailer of mac running linux. they have not always chosen the most linux friendly components though.

using BOIS rather than EFI would have been a step backwards from open firmware. apple tend to push new technologies by removing the old ones. like iMac not having a floppy disk, or serial / paralell ports.

---

### Post by rodrigogar on 2006-05-17
hey guys, check out this page.
[http://modular.math.washington.edu/macbook/](http://modular.math.washington.edu/macbook/)

ubuntu on mac :|

---

