---
title: "Ubuntu Live CD fails to boot on iMac G5."
date: 2006-03-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by megabenman on 2006-03-31
Hi, I have an iMac G5 20" 2.0 GHz. When I try to boot ubuntu off a live CD, this is what happens:

1. Computer starts up. I hold the C key and it goes to a grey screen, which flashes black twice.

2. I get a black screen with white text in the top left corner, asking how I want to boot. I type live-powerpc64.

3. It goes to a white screen with black text, for about 1.5 seconds. Then, white text with black around it goes slowly throughout the screen.

4. I get a blue background while kubuntu asks me various settings. To be safe, for my monitor, I didn't change anything. Starting at the network configurination, the fans blast extremly loud, louder than any time in Mac OS X. I will tell you when this stops later.

5. I get a black screen with white text, performing tons of checks. All of them are ok, except synchronizing my clock with ubuntulinux.org.

6. I then get a kubuntu logo in the middle of my screen, with a loading bar. The checks are shown in a tiny area below. When the bar reaches about 25%, the fans go back to normal.

7. I then get a black/grey background with an X in the middle. Eventually, the background turns blue and the X turns into a white cursor. I can't move it. Again, the fans blast loudly again and they don't stop, because my computer is now frozen. It just stays at this point and does nothing until I hold the power button.

---

### Post by dmb on 2006-03-31
Sounds like xorg is crashing, and causing a permanent loop or something, and cpu makes heat while the loop is going so the fans spin faster.

---

### Post by ASJ on 2006-03-31
I have the same problem but I don't even get that far.  I get upto number 3 of yours and it just stays there while the fan is blasting out.  I have made sure that my CD is OK but it just keeps on freezing.  I'm typing in 'live-powerpc64' to boot that and I think thats rite but when I just press enter it carries on but then says 'Release keys to continue!' and above that, 'type 'mac-boot' and hit enter to continue booting but that does nothing.

---

### Post by megabenman on 2006-03-31
dmb
Is there any solution?

ASJ
Type live-powerpc64 for G5. For G4 or G3, type live-powerpc.

---

### Post by ASJ on 2006-03-31
I have just found that it's not just Ubuntu that I cant boot, my iMac G5 will officially not boot anything other that Mac OS X.  It keeps on freezing at the same point on each boot up and the fans come on at the same point aswell.

---

### Post by dmb on 2006-03-31
[QUOTE=megabenman]dmb
Is there any solution?

ASJ
Type live-powerpc64 for G5. For G4 or G3, type live-powerpc.[/QUOTE]
No, sorry, i was just diagnosting and maybe explaining in detail what was happenning. I do not own any g5, so I can't help you.

---

### Post by megabenman on 2006-03-31
:(
Do you know anybody who can?

---

### Post by megabenman on 2006-03-31
Ok I found this:
[http://ubuntuforums.org/showthread.php?t=118282](http://ubuntuforums.org/showthread.php?t=118282)
But the ctrl+alt+F6 command didn't work. And apple+alt+F6 just skips parts of the installation.

---

### Post by Torrance on 2006-03-31
This is the thread you want: [http://ubuntuforums.org/showthread.php?t=89712](http://ubuntuforums.org/showthread.php?t=89712)

Its a sound driver issue on iMac G5s, and I'm afraid it can only be fixed with a bit of tinkering with an installed system only - the live CD is a write-off.

Fingers crossed this bug will be fixed with the next release - a lot of other distributions have got round the problem but testing for and then disabling sound during installation - hopefully Breezy will do this too.

---

### Post by megabenman on 2006-03-31
*Cries continuosly*
Well do you know of a good tutorial to dual boot Mac OS X and Ubuntu. One thats easy to understand so an idiot like me doesn't screw up his harddrive and have to reinstall Mac OS X.
Also, does linux void your warranty, like it does on your iPod? Cuz my warranty ends August 3rd.

---

### Post by Tipo on 2006-03-31
Probably a dumb question now, but are you trying to boot a PPC cd on a Intel iMac G5? As of now, there is no Ubuntu distro that will work on an Intel iMac...

---

### Post by megabenman on 2006-03-31
Lol no it's an iMac G5.

Ok I think I kinda found a solution to running a ubuntu live CD on an iMac G5. It's slow as hell, but the emulator Q can run .iso linux files in emulation. It's only at 33 MHz. If you want to do it, make sure you select it so you use a .raw harddirve, and you boot off a .iso file as a CD-Rom.

---

### Post by ASJ on 2006-04-01
Sorry, I'm not brilliantly technical even though you probably don't need to be to know this lol, but whats a .raw hard drive.  Is it a disk image?

---

### Post by megabenman on 2006-04-01
No idea, but you can make special disk images for Q.
UPDATE: It didn't work. Kubuntu froze at configuring language at 21% and Ubuntu froze at Installing modules at 91%. I'm going to try the x86 version on Q.

---

### Post by dmb on 2006-04-01
There is no such thing as an intel G5. G5 refers to the ibm power pc, and the powerpc only.  Intel's proccesor would be a duo proc.

---

### Post by megabenman on 2006-04-01
Listen. I am on an iMac G5. Q can emulate different processors, allowing you to run windows and other x86 OS's on it.

---

### Post by jdp on 2006-04-01
I think dmb was replying to the comments Tipo made about an "Intel iMac G5" and "Intel iMac".  Offically it's an Apple iMac, but they're listed with "Intel Core Duo" CPUs.  Intel is not a part of the official Apple name for them at all.

[http://www.apple.com/imac/](http://www.apple.com/imac/)

---

### Post by linear on 2006-04-01
[quote=megabenman]Well do you know of a good tutorial to dual boot Mac OS X and Ubuntu.[/quote] If you do decide to dual boot, you'll find various tutorials in the forum. Here's my short version:

First read these:
 
 [https://wiki.ubuntu.com/Installation/PowerPC]("https://wiki.ubuntu.com/Installation/PowerPC")
 [http://www.askdavetaylor.com/how_do_..._mac_os_x.html]("http://www.askdavetaylor.com/how_do_i_dual_boot_ubuntu_linux_mac_os_x.html")
 
 0. Read up in the PPC forums on any model specific quirks. (Err... I guess you know these already.)
 1. Back up OS X partition. ([Carbon Copy Cloner]("http://www.bombich.com/software/ccc.html") works well.)
2. Repartition disk. Make two partitions, leave first as free space and second for OS X. Disk Utility is destructive (another reason for the back up), or there is a howto [here]("http://ubuntuforums.org/showthread.php?t=89960") on using **parted** to resize non-destructively (though that may be a chicken-and-egg problem for you). Make the partition at least 5GB, but bigger is better if you really plan to use it.
 3. Boot from the Ubuntu install disk. When you get to the partitioning step, tell the installer to use the largest free space. It will take care of the rest.
4. In your case, disable esd as described in other posts.

---

### Post by megabenman on 2006-04-02
Yeah, I don't think I will be able to use parted because I can't boot up from a live CD.

---

### Post by jdp on 2006-04-02
From what I've used, **parted** is on the Install CD, **gparted** is on the LiveCD.  I've tried booting a LiveCD and getting to a command line/terminal and **parted** wasn't available.  If you get far enough in the LiveCD to start up the WM somewhat, you might be able to use the Install CD to get Ubuntu installed on the HDD.  I don't know if that would be a good idea right now or not, as G5s seem to be having alot of trouble with Ubuntu lately, esp. with the sound bug and the constant full speed fans bug.

---

### Post by mindhammer on 2006-04-20
:-k 

Have you tried using (K)**Ubuntu 5.04 PPC** ?

If my memory serves me well, that one should work with G4s and G5s (of course using the appropriate options for 32 and 64 bit kernels, respectively).

At least that version (5.04) _works_ 100% with eMacs (G4s). I think I tried it on a iMac G5 once and it worked, but I mainly work with eMacs, so I can't recall for sure. I use Ubuntu mainly on PCs, but also the  live version at work, where we have only eMacs.

Good luck!

---

### Post by megabenman on 2006-04-21
[QUOTE=mindhammer]:-k 

Have you tried using (K)**Ubuntu 5.04 PPC** ?

If my memory serves me well, that one should work with G4s and G5s (of course using the appropriate options for 32 and 64 bit kernels, respectively).

At least that version (5.04) _works_ 100% with eMacs (G4s). I think I tried it on a iMac G5 once and it worked, but I mainly work with eMacs, so I can't recall for sure. I use Ubuntu mainly on PCs, but also the  live version at work, where we have only eMacs.

Good luck![/QUOTE]
I've tried kubuntu 5.10 and it doesn't boot... do you have a link for 5.04?

And I've decided to dual boot ubuntu and OS X. The problem now is..... how am I going to make another partition on my harddrive? Is there anyway I can acess parted? I've heard a gentoo PPC live CD has it, but that is from 2004, and I doubt it will support my iMac G5.

---

