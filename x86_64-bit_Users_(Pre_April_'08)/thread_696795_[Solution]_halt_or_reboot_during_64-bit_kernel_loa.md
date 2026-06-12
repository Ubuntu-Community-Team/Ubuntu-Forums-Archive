---
title: "[Solution] halt or reboot during 64-bit kernel load"
date: 2008-02-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by YourMothersAnAstronaut on 2008-02-14
Hello all, I've been a longtime Ubuntu user and just now decided to join up here. But I'll cut to the chase.

I re-installed Ubuntu on my machine about a week ago, the 32-bit version. Worked great, no issues. Then when I got my RAM back from a Mushkin RMA (long story short, all 4 sticks died and they replaced them for me). I changed nothing but adding those 4 new sticks back in, and decided to go back to 64-bitland. 

I aways use the alternate installation disc because I use a special bootloader configuration and I need the installation flexibility. Anyhoo, I booted with the disc and it halted after the progress box came up for loading the kernel. Got a message that said:

```

Kernel alive
Direct mapping tables ..........

```

Tried rebooting several times, nothing. Vista x64 installed and boots fine, so my CPU (Core 2 E6600) didn't lose 64-bit OS support suddenly. Was running the same BIOS revision I'd been running the last time I ran 64-bit Ubuntu. Tried checksumming the disc, nothing. Couldn't test the media with the tool on the disc because it has to boot the kernel first. 32-bit disc worked fine, so it's a 64-bit kernel issue only.

Where my issue differs from others is that instead of halting, my system restarts completely. Though I have a hunch my solution will work for both issues because we halt at the same error.

***** Solution *****
The solution for me was twofold. To get into the installer, I told it to run in 1024 x 768 resolution. Installed fine after that. Once Ubuntu was installed, it ran great. Upon reboot, it halted at the same place.

Some other threads on here have suggested that editing the GRUB boot options to remove the splash screen and boot in "noapic" mode have worked for them. Didn't work for me. What worked for me was editing the section for a normal boot to read:

```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=47aadd87-813d-44f5-a9ab-e95135af79da ro vga=771
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault

```

After adding vga=771, the system went black (which worried me) then a few seconds later I was at the Ubuntu login screen. In my native resolution (1680x1050) with full Desktop Effects working. Rumor has it the splash screen is to blame, so forcing it not to be shown seemed to fix the problem. What's interesting is that neither removing the splash screen with "nosplash" or just removing the "splash" parameter fixed it. The "savedefault" line makes sure the changes you make persist through a reboot so you don't have to edit the menu.lst file every time you boot Linux.



Hope it helps!


System specs:

Core 2 Duo E6600 @3.15GHz
eVGA 8800GTX
4 x 1GB Mushkin DDR2-1066
Gigabyte GA-G33M-DS2R

---

### Post by gsmanners on 2008-02-14
I would assume the video card is partly to blame (too new).

Did you try other modes?

[http://easylinux.info/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen](http://easylinux.info/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen)

---

### Post by MystikIncarnate on 2008-02-14
I ALWAYS have a multitude of problems getting linux up and running on my PC (whether live-disk or fully-installed)... my solution has been a boot switch of "irqpoll" .  i don't know why it works, but it does.

usually while i'm modifying the startup, i also add the nosplash option (or change the splash to nosplash), and remove "quiet" if it's there... giving me a verbose text-mode startup summary.

my pet peeve, is that everytime my kernel changes, gets updated or i have to rebuild anything that requires a reboot, it rebuilds the grub menu.lst file.  when it does so, the irqpoll option gets removed, the nosplash goes to splash, and the quiet option also returns, resulting in my computer locking up at a black screen shortly after the bootloader.

annoying, but such is life.

---

### Post by audacity on 2008-04-24
THANK YOU! This was the only solution that worked reliably. It's definitely a problem with newer NVIDIA cards not responding/supporting certain queries, but changing the video mode and getting rid of the splash screen worked for me. Much obliged.

now to see about getting a video mode that works and still lets me see the boot progress.

---

