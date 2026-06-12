---
title: "AMD64bit Edgy LiveCD loader hangs, can't install :("
date: 2006-11-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by em0j on 2006-11-25
Hello all,

I've read most of the posts about installing 64bit Edgy. With out a doubt there are issues. I'm about to give-up so I'm asking for help.
I recently put together a brand new system just for gaming. I pride myself at going to lan parties with the ony "[COLOR="Sienna"]U-Box[/COLOR]" as I call it.

_Comp specs_
**MB:** Abit NF-M2 nView
**CPU:** AMD64 X2 4200+
**Mem:** 2Gb [Patriot PC2-6400]("http://www.patriotmem.com/products/detailp.jsp?prodline=5&catid=2&prodgroupid=38&id=317&type=1") memcheck, checks out.
**Video:** BFG7600GT PCIe w/9692 Nvidia Drivers
**HD:** Single SATA WD 300MB HD (will do the raid thing later)
**KB:** Logitech G15
**MS:** Logitech Mx518
**Current OS:** Ubuntu 6.10 32bit

Life is great in the 32bit world with Ubuntu Edgy. BUT, I want more power! I have a 64bit system and want 64bit power.
**1st attempt:** Using the AMD64 Edgy LiveCD version. I come to realize that it doesn't like the G15 keyboard, no KB response at all. I've looked at the BIOS and eveything checks out with the USB settings (same settings works in Dapper) So, I switch to a Logitech wireless KB, and BLAM I have keyboard control. I hit F4 to change resolution to 1024x768 and the loader starts, it's a grey "Ubuntu" logo with the a non moving loading bar. It just hangs there...........forever. I've tried veriouse resolution settings including the default and it always hangs.
**2nd attempt:** AMD64 Edgy [LiveDVD]("http://ftp.funet.fi/pub/Linux/INSTALL/Ubuntu/dvd-releases/releases/6.10/release/"): I actually found a DVD version about a 3gig iso. Same freakin results. A hanging loader.
**3rd attempt:** I am currently downlaoding the alternate AMD64bit ver. I am not sure how much different it is from the rest but I'll try it.

**recap:** When using the livecd/dvd it just hangs on the loader. G15 Keyboard will not work at all, but my wireless LX710 works. I've tried safe mode and text install and they all hang. The motherboard is too new to have any bios updates.

Any help in bringing me to 64bit nirvana is greatly appreiciated.

Thanks in Advance
--ED

---

### Post by em0j on 2006-11-25
I wanted to add:

I hit the "install by text" and watched the scrolling text indicators of whats okay. It stalls on:

libata version 1.20 loaded

not sure what is after that but that seems to be where it hangs during the install proccess.

---

### Post by bronson on 2007-01-04
I'm noticing the exact same thing with a very similar setup (I only have 2x512MB Patriots and I'm using the built-in video).  The amd64 Edgy live CD hangs (although it hangs at a different point than you say).

I noticed that the amd64 Dapper LiveCD works great so I installed dapper no problem. Then I apt-get dist-upgraded to Edgy.  Now when I boot my Edgy partition using the Edgy 2.6.17 kernel, it hangs.  But when I boot Edgy using the old Dapper 2.6.15 kernel, it works great.

So, it appears to be a problem with Edgy's 2.6.17 kernel.

This isn't a regular kernel panic either.  The system is still responsive, my keypresses echo.  It's just that nothing is happening.  The last messages in the boot log are:

[33.917582] Freeing unused kernel memory: 188k freed
[33.941857] input: AT Translated Set 2 keyboard as /class/input/input0
[33.963759] vga16fb: initializing
[33.963800] vga16fb: mapped to 0xffff8100000a0000
[34.150068] Console: switching to colour frame buffer device 80x25
[34.155258] fb0: VGA16 VGA frame buffer device.

Maybe something display related?  I'm going to keep playing with it but, for now, it appears that running Edgy with Dapper's 2.6.15 kernel seems to work fine.

That should get you to a lot closer to 64 bit nirvana anyway.

---

### Post by 454redhawk on 2007-01-04
I took 4 or 5 tries for me.

---

### Post by bronson on 2007-01-05
Well, not solved so much as worked around...

Just pass "noapic" to the end of the kernel boot arguments.

To make this the default, edit /boot/grub/menu.lst.  It appears to work great.

I was wrong -- the kernel WAS panicking, immediately on boot.  I don't have a serial console hooked up so I couldn't capture the panic, but it was something about "nmi watchdog detected lockup on CPU 1."  Easy enough to reproduce if anybody would find the trace useful.

So, for now, noapic's the trick.  Hope Feisty fixes things.

---

### Post by janfsd on 2007-01-05
I got the same problem with the live CD, so I just used the alternative cd to install Edgy.

---

### Post by bronson on 2007-01-05
Looks like someone else is mentioning this on abit's forums.  Apparently this bug hits Windows too, it's just that the results aren't as catastrophic.  Looking forward to a BIOS upgrade.

[http://forum.abit-usa.com/showthread.php?t=112136](http://forum.abit-usa.com/showthread.php?t=112136)

---

### Post by asathoor on 2007-01-06
My installation also hangs with a:

[LIST]
[*]Athlon Gaming PC
[*]Dualcore AMD 64
[*]1 GB ram
[*]nvidia videocard
[*]MSI-V motherboard
[/LIST]

I have tryed the amd64 and the i386 install cd.
Ubuntu simply won't install.

SUsE 9.3 worked fine from an old magazine cover CD. 
Knoppix live cd worked
Fedora crashed
Gentoo could not load X

rgds.

Asathoor

---

### Post by skinrock on 2007-01-06
Wow, what are the odds.  I've got the same issues going on.  In fact, I was about to post about that grayscale load screen.  I decided to switch back to Dapper Drake while I try and solve it.  From the short time I was on Edgy, it looked a bit nicer overall.

But ya, I'm basically in the same exact boat as you.  I've got an AMD X2 4400, and I use the G15 keyboard as well.  I noticed that if you interact with the keyboard before Ubuntu loads, it freezes up.  I also get the gray load screen, which I knew didn't seem right.

So is it basically a matter of sticking with Dapper Drake for now, or are there fixes for Edgy?  I'd rather find out now, because I've decided to switch over completely this weekend, Ubuntu will be my main OS.  I also wanted it to setup a LAMP server, so I don't want to do all of this if Edgy is in fact stable.

---

### Post by em0j on 2007-01-07
I gave up for right now. For the New Year my goal was to be MS Windows free, and to use Ubuntu Edgy. I've read so many posts. If there is a fix for it, we can't do it cause it's probably fixed in an "update" and we can't even install it ;) 

To add, the alternate AMD64bit ver did the same for me, no KB response and Hangs.

My motherboard **Abit NF-M2 nView** finally has a new BIOS update! What sucks is that I'm running Winx64 and the flasher software only works on 32bit OS LOL. 

If I was a programmer I'd make a web-based tracker tool of some kind where Ubuntu users can enter there hardware. The software would compare data from other user hardware config to what linux version works and not. It'll take of course the community to make it work by entering there data. The data collected can point out in a graph what hardware with what version has the most problems. I guess it's kinda like registering your hardware for statistical purposes. I would be glad to register my hardware with Ubuntu if I'm using there distro. Think of it as an added step to Quality control.

Happy New Year

em0j

---

