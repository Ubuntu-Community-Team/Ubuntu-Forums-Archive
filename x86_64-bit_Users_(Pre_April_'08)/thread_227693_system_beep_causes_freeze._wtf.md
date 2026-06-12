---
title: "system beep causes freeze. wtf?"
date: 2006-08-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by ericcmi on 2006-08-02
Im running an amd64 939 3000+ winchester core.
An abit av8 with via chipset.
1 gig ram.

I had ubuntu dapper 64 running splendidly. I messed the install trying different compilations of compiz. I just so happened to receive the 3 install cd's I ordered and decided it was a good time to reformat. The liveCD ran just fine and installed like a dream, Even config'd my wireless like usual.  After rebooting and opening the console to set a root password I [TAB]'d a system beep and the whole thing just froze solid. ctrl-alt-bkspc did nothing at all. the whole system was frozen. I rebooted thinking it was a fluke and the same thing happened again and again.

I got mad and reinstall from the ISO I downloaded and burned, which I used for my first install. I thought perhaps they mailed me a bunk copy or something. After a complete reinstall it happening again. Any time the system beeps, it freezes. I can barley use the console at all, i'm too parinoid of corrupting my other partitions.

any advice would be greatly appreciated. Im tempted to try the 32bit install just for kicks.

---

### Post by hiltstck on 2007-11-23
I assume the author of this problem has found a solution, but in case you have the same problem and are disappointed that no solution has been posted...see the following link.


[http://bogdan.org.ua/?p=240&akst_action=share-this](http://bogdan.org.ua/?p=240&akst_action=share-this)

...and in case that link disappears, here is the text:


Fresh install of Debian Etch 4.0r1 hangs/freezes dead after boot: solution

Posted in: Links, *nix

Recently, I installed Debian Etch 4.0r1 onto my laptop. However, after the first boot into plain console, computer was dead-frozen after some console usage. I rebooted using the Power button - this time to gdm; and again, after some keyboard input system was hanging dead.

I found the reason here. Basically, it’s the PC speaker module (pcspr) not functioning correctly. I suspect this problem manifests itself only on some types of laptops. The solution is either to somehow reconfigure the pcspkr module, or just disable it. More on how to disable the module below.

First of all, boot into console-only mode or even single-user mode. On my install GRUB loader, configured by the Debian Installer, had an option in the boot menu to boot into single-user mode.

Remember, that any sound emission attempt will freeze your computer in this scenario. So avoid any actions, which might generate a system beep. These actions include (but are in no way limited to): using TAB filename/command autocompletion, using up/down arrows in command line when there is nothing in the history above or below the current command, etc.

After successfully booting, remove the pcspkr module: modprobe -r pcspkr (if that doesn’t work, try rmmod pcspkr). Note, that this command only removes pcspkr module for the current session, and the module will be loaded again on next boot.

To permanently disable the pcspkr module, you can blacklist it. To do so, add the line blacklist pcspkr to the /etc/modprobe.d/blacklist.local file. If this file does not exist, you can create it.

On my system I already had /etc/modprobe.d/blacklist file, so I also added blacklist pcspkr line to that file. I did not check which one actually worked for me, but on the next boot pcspkr didn’t load.

I also did one more thing - configured console not to beep. This is done in /etc/inputrc file by uncommenting the following line: set bell-style visible (or you can uncomment set bell-style none to have absolutely no bell notifications).

There’s also a method to disable IPv6 module, which can be adopted for the pcspkr module. However, I didn’t use it - methods listed above helped me.

References other than already cited: gentoo no-beep, how to disable PC speaker, how to disable PC speaker in Etch.

---

