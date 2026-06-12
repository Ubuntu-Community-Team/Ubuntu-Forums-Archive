---
title: "dual booting OS 9/Breezy"
date: 2006-02-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by nib on 2006-02-16
I created two Volumes on my 80GB hard drive, formatted as HFS+.  I installed Mac OS 9.2.2 on the 60GB volume.  I then booted from Ubuntu Breezy and installed that onto "the largest unused block" , letting Ubuntu set it up automagically, I presume on the other volume.
I don't know how/when to choose which system to start up on a restart.  If I'm using OS 9 a reboot starts OS 9, but I can't get back to an Ubuntu boot up.  I thought Yaboot was supposed to give me this option, like the BootX preference pane in Old World Macs.  I hope this is simple, I have too much software on the OS 9 Volume to start over.
TIA

---

### Post by jdp on 2006-02-16
What machine is this on?  YaBoot should present a boot menu befoer OS 9 loads.  Is the PRAM (clock) battery dead?  If so then it can lose the boot settings if the machine is unplugged.

---

### Post by Ptero-4 on 2006-02-16
If you don't see yaboot just use the alt bootloader to get there again.

---

### Post by SectionThree on 2006-02-16
[quote=nib]
I don't know how/when to choose which system to start up on a restart. If I'm using OS 9 a reboot starts OS 9, but I can't get back to an Ubuntu boot up. I thought Yaboot was supposed to give me this option, like the BootX preference pane in Old World Macs. I hope this is simple...
TIA[/quote] 
Yes it is simple.

First boot into your open firmware. You do this by holding down cmd-opt-o-f while you start up. It'll take you to a command-line. Now type: *boot hd:##,yaboot *(## is the partition number you've got Ubuntu installed on).

Now, the machine should start booting up with Ubuntu.  Once you're all booted up, crank up your terminal and *sudo apt-get yaboot* and then *ybin*.  When you restart your machine, the bootloader screen will then be restored.

If you keep having these problems whenever you restart from OS 9, you should look into upgrading to OS X 10.2. It plays well with Ubuntu and you can get it for a coupla bucks on eBay.

Of course, I'm assuming you have a New World machine. If not, it's completely different.

This is assuming that you're running a NewWorld Mac, otherwise it's completly different.

---

### Post by engla on 2006-02-16
[QUOTE=SectionThree]
Of course, I'm assuming you have a New World machine. If not, it's completely different.

This is assuming that you're running a NewWorld Mac, otherwise it's completly different.[/QUOTE]
If you have a New World machine, you should try the Alt trick first: Hold Alt (Option) while you boot. 

It's a bootloader that will give you an icon for each bootable disk -- it works fine but slow on my apple and even displays a tux on the linux disk. If you select the correct disk here once, you don't have to do it again.

If that doesn't work, try the above.

---

### Post by nib on 2006-02-16
OK, thanks to all of you.  Holding the Option key gave me two square icons, one with the friendly Mac guy and the other the friendly Penguin ummmm guy :-).  So far, I've had to use this method to boot into Ubuntu.  Mac is the one  that the button is depressed and automatically selected to boot of the two "icons".
Is it OK to continue to use this method?  It's perfectly acceptable to me, since the boot time isn't that bad.  I used the Terminal to do apt-get, but was told I already had the latest version.
Oh, BTW, yes this is a G4 AGP.
Again, thanks!

---

### Post by nib on 2006-02-17
Is the PRAM (clock) battery dead?  If so then it can lose the boot settings if the machine is unplugged.[/QUOTE]
There is something going on here.  The time won't set correctly.  I see a warning "failed" for NTP when the system is starting up.  I can't get it to set the right time, even by contacting a time server.  Even setting it manually, it fails to set the computer to the correct time.  I have my time zone set correctly, also.  Something is wrong here. :???:

---

### Post by linear on 2006-02-17
Time to replace that PRAM battery.
 
Also have a look at the contents of /etc/yaboot.conf. Information on what to do with it here:
 
[https://wiki.ubuntu.com/YabootConfigurationForMacintoshPowerPCsDualBoot](https://wiki.ubuntu.com/YabootConfigurationForMacintoshPowerPCsDualBoot)

---

### Post by 3rdalbum on 2006-02-19
If, like me, you have someone else in the family who wants to use Mac OS and doesn't want to use a bootloader, you could consider setting the computer to always boot Mac. Then, if you want to boot Linux, use the Open Firmware directions given earlier. That's what I do.

---

### Post by SectionThree on 2006-02-20
[quote=nib]OK, thanks to all of you. Holding the Option key gave me two square icons, one with the friendly Mac guy and the other the friendly Penguin ummmm guy :-). So far, I've had to use this method to boot into Ubuntu. Mac is the one that the button is depressed and automatically selected to boot of the two "icons".
Is it OK to continue to use this method?[/quote]

The one absolute rule is that if it works, then it's OK :cool: (no damage is being done, if that's what you mean).

But, if you want to boot up Ubuntu and not have to hold the option key (i.e. with yaboot), run *ybin* in your terminal and that'll do the trick.

---

