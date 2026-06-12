---
title: "Ubuntu on AMD64 Turion X2 possible?"
date: 2006-08-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by LeMeun on 2006-08-12
Hello everyone,

I'm quiet new with Ubuntu but i'm using Debian since a while. I read all the threats and helps about installing Ubuntu and AMD64, no answer to my question:

Is it possible to install or run Ubuntu on my notebook MSI S271 megabook AMD64 Turion X2? (duo core AMD64)

I try ubuntu-6.06-alternate-amd64.iso and ubuntu-6.06-alternate-i386.iso and after loading the kernel they 
both crash (i'm not sure they compile it). I did a MD5 checksum for both iso, i check the cd for defect and i run the check RAM memory(ddr2 533 2Gig, take 30 mins!). Everything is fine. It seems the kernel can't be compile on my processor even if it's an AMD64.
 

I'm fan of live-cd, find it very handy for compiling c programs and surfing freely on the web. I discover Ubuntu and i'm planning to install the i386 on my P4 deskstop but i'll be very glad if i can use it on the road with my laptop as well ;-)

I try other live-cd (knoppix, backtrack,...) same problem stuck just after loading the kernel.
Thank you in advance for your time and interest.

LeMeun

---

### Post by Lonthong on 2006-08-12
It should install without any problem. I am writing as a total newbie that just found ubuntu world less than a week ago.
I installed live CD 6.06 64bit onto my BenQ Joybook P41: Turion x2 TL50 ATI X1100 - so it should be quite similar to yours s271.

Installation was completed in less than 1 hour. Of course, you will have to do some tweaks here and there afterwards

---

### Post by LeMeun on 2006-08-12
Yes same spectre as my MSI, you install the 64bit version, i'll try again. Thanks

---

### Post by Kilz on 2006-08-12
Sometimes the Alternate install cd works when the Desktop or live CD will not. If you still have problems installing from the Desktop CD try the Alternate. The difference is the Alternate is just an installer without fancy graphics or a live operating system, it just installs Ubuntu.

---

### Post by LeMeun on 2006-08-12
I try again and it didn't work with the desktop amd64, i think i'll follow the advise of Kilz and go for the Alternate install cd. So i'll have a dual boot system... i didn't partition my disk and i'm afraid to mess my winXP i need to backup first all my data.
let you know Thanks

---

### Post by usernamed on 2006-08-12
I can think of two things that might be causing the issue.

If the issue occurs just after you select an option from the boot menu, then there's an option you can enter at the boot prompt to disable the framebuffer device.  If the screen just goes black at booting, this may be the issue.

If the issue is occurring after the kernel has booted (when you'd expect the X Server to start) and your computer has ATi graphics, then try switching to a text console, and editing the etc/X11/xorg.conf file.  There's a line in the "Module" section that reads 'Load "int10"'

Try commenting that line out, saving and re-booting.  This issue caused the XServer to freeze on a black screen for me, but I'd thought that particular issue was specific to my brand of laptop.  If you don't have ATI graphics on your laptop, then I wouldn't even bother trying this one. 

Hope one of these two helps.

---

### Post by LeMeun on 2006-08-13
I try the boot option suggested by Usernamed to disable the framebuffer using the live cd amd64 i type this:

boot prompt: live debian-installer/framebuffer=false

Didn't work seems it can't identify the processor,one of the error message is "CPU too small"

when i use the normal boot (just enter while running the live-cd) it load the kernel, decompression kernel .... ok than come the Booting kernel and it's where it stop no further line. 

The kernel is not run therefore not access for text consol yet :(

---

### Post by LeMeun on 2006-08-13
here is the complet details of what happen:

i press enter after the splash screen from Ubuntu (30s count down)
- loading /casper/vmlinuz.......................
- loading /casper/initrd.gz.....................

loader screen appear -> loading Linux kernel 100%

go to black screen

.
decompressing Linux... done.
booting the kernel.

and everything stop no further lines.

I try many of the boot options and nothing work so far, maybe live-cd is not for my laptop yet and i need to wait the next release...:-/

---

### Post by parkash on 2006-09-03
Try booting the amd64 LiveCD with the "noapic" option.. 

I've Dapper 64 running just fine in my Turion 64X2 :)

---

### Post by tymek666 on 2006-09-03
'noapic' should help. However it's rather chipset not cpu problem.

---

