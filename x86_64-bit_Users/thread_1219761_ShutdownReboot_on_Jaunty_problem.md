---
title: "Shutdown/Reboot on Jaunty problem"
date: 2009-07-22
forum: x86 64-bit Users
---

### Post by glowplug61 on 2009-07-22
If I have overlooked an appropriate solution then I apologize but I have speant quite a number of hours searching and trialing.
All I have found on this subject are laptop wifi related solutions, things that either don't work or broke my system.
I have just had to do a fresh install because it was starting to lose settings a get file errors on reboot.
I assume that is because I was powering down from stall - if I simply powered down a lot of my settings were ignored or gone on reboot.

It did the post installation auto reboot fine.
It did the post updates auto reboot fine.
I then tried manual reboots that failed - firstly by menu then terminal (-r -P -h) with no success.

The hardware is MSI K9N, AMD 4000+, nvidia 6800gt, 2g ram, seagate sata
Ubuntu 9.04, x86 64

Thanks in advance for any help
Regards,
Greg

---

### Post by brucewestfall on 2009-07-22
I'm not sure exactly what you mean, but I also had startup problems with 64bit 9.04 and nvidia gfx card.  What fixed it for me was installing lilo.

We are always warned about upgrading too soon, but somebody has to!

Does this cover your problem?

---

### Post by glowplug61 on 2009-07-22
Hi thank you for your reply.

To clarify I just added the other stuff to save people posting what I've already tried.

I've searched on "lilo chainload windows", "lilo ubuntu windows", "lilo ubuntu xp32", "lilo ubuntu xp32 configure manually", etc, etc.
To cut a long story short I've had bad experiences with installers/configurers for boot loaders - especially when leaving my windows drive in.

Could somebody please confirm that lilo 1.22.8 installation that comes with synaptic 
1. does NOT include anything that will write to another disc/partition's windows MBR, install, boot or post-install.
2. accepts a chainloader statement written to lilo.conf as...

title Windows XP
map (hd0) (hd3)
map (hd3) (hd0)
rootnoverify (hd0,0)
root (hd3,0)
makeactive
chainloader +1

...OR something like...

other=/dev/hda1
	label=windows
	table=/dev/hda
	map-drive=0x80
	   to=0x81
	map-drive=0x81
	   to=0x80

...OR ?

My plan is to disconnect all other drives, install lilo, configure dual boot, reconnect other drives.

---

### Post by glowplug61 on 2009-07-24
I apologize if I seem narky in the following but it is seriously eating at my time, patience and energy.

Great, I'm now back to multi booting through the bios.
I have to do this a lot at the moment to develop/test my themes for Firefox.
I try to support linux, bsd, mac, windows, solaris.

I've had requests to support some portable devices which I'd like to follow up on ONLY I'M TOO BUSY TRYING TO REBOOT REINSTALL UBUNTU!
Reinstalling Ubuntu takes out almost THREE DAYS of my spare time!!

As far as upgrading prematurely Jaunty has been the stable release longer than since I purchased my motherboard, processor and ram.
Of course my videocard is old but it supports a lot of compiz features so I can't see it being a shutdown inhibitor.
 
I disconnected all other drives - I am not going to risk other mbr being tarnished.
Installing lilo went into a permanent loop - removing chainloaders from /boot/grub/menu.lst rectified the problem - I'm flabergastered that it looks there juxtaposed the horses mouth.
Running liloconfig resulted in...
"This doesn't look to me like an "ordinary" block device. Either your fstab is broken and you should fix it, or you are using hardware (such as a RAID array) which this simple configuration program does not handle."

I uninstalled lilo in preference of seeking advice here.
After this I powered down, reconnected all drives. booted Ubuntu and found all drives visible but did not mount any.
I then replaced the chainload statements.
After that I reset rebooted (due to problem) and found that grub can no longer chainload windows.

I did not know that at that stage and missed a few heart beats.
Each of my bootable drives HAS to be STAND ALONE.

I swapped drives in bios and it's just a squashed grub!!

With all this said I was already resigned to doing yet another reinstall but now I have no choice.
If I am going to do this and nobody is going to provide a solution can you at least point me in the direction of the source code I need to edit because I am not sure where that is!!

---

### Post by glowplug61 on 2009-07-27
Installing lilo was a disaster.
Due to a number of reasons I've reinstalled Ubuntu.

Doing that install/configure progressively showed that the third line of the following causes the problem...

title Windows XP
rootnoverify (hd1,0)
map (hd0) (hd1)      <-----THIS LINE
map (hd1) (hd0)
makeactive
chainloader +1

...the problem is, black screen 1-2 seconds on shutdown/reboot or gdm stop/restart.
That block of instructions do however boot windows.

Using the chainloading example from grub( 8 )...

title		Windows XP
root		(hd1,0)
makeactive
chainloader	+1

...shuts down etc but does not boot anything.
I don't see how it's going to map up anyway.
Not unless something was added such as "(hd0,0) /dev/hda" which is in  /boot/grub/device.map
I tried putting "(hd1,0) /dev/hdc" underneath that line but encountered serious problems.

Between developing/testing my Firefox themes and other things, constant dual booting through bios is too much of a problem.
I'll simply reinstall Ubuntu every 1-2 weeks as it becomes too unstable from not shutting down properly.

---

### Post by glowplug61 on 2009-07-31
Sorry to bump this again but in my frustration I have failed to ask a straight forward question in my previous post(s).

Problem:
Since changing to Ubuntu 9.04 I have found that any chainloader blocks for XP in /boot/grub/menu.lst cause a /etc/init.d/gdm stop and restart freeze - therefore shutdown and reboot freeze.

Findings:
I have found a number of posts here and elsewhere that say to install lilo.
* Every tutorial on installing lilo I've found state that the windows must be installed first and connected.
* No tutorial states whether the windows mbr will be written to or not
* No tutorial shows how to manually configure a windows chainloader - eg. post lilo installation.

I can NOT allow the windows mbr to be written to.

My questions:
1. Could somebody please tell me whether using the synaptic install of lilo and then it's configuration process will/not write to the windows mbr.
2. If the configure process is going to write to the windows mbr, is it possible to disconnect that drive, configure linux then manually add a chainloading block after reconnecting the windows drive.

---

