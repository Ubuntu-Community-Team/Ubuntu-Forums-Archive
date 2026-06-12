---
title: "New to linux. Not booting."
date: 2006-03-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by mneofreek on 2006-03-12
I wanted to try out a linux operating system for my new computer and a friend had recommended Ubuntu for me and gave me a Ubuntu 5.10 disk to try it out and see how I like it. During the booting it would freeze up on the screen saying "Loading module 'isofs' for 'Linux' ISO9660 filesystem..." I searched the forums here and really found nothing of the sort dealing with this issue. Maybe you guys can help me out.

BTW is it normal for Ubuntu to not support wireless USB keyboards and mice? I tried loading it in expert mode but the keyboard didn't work in the boot menue screen.

Thanks,
Neil

---

### Post by kittycatsexycat on 2006-03-12
maybe you should just get it working before adding bits on...

not being cheeky but i tried to do it and it just didnt work.. make sure your comp boots from the cdrom....

find out in the setup screen before it boots by pressing esc...

:D

---

### Post by mneofreek on 2006-03-12
I can get the CD to boot just fine. Its just that while Ubuntu is loading it freezes up or takes forever. My terminology might not be right I think. I was able to get it past the screen that said "Loading module 'isofs' for 'Linux' ISO9660 filesystem...", but it took forever. Should it take over 45 minutes to load the OS? I gave up and shut it down cause thats just to darn long to be waiting. I know it will boot faster because my friends laptop loaded this exact same cd in less than 5 minutes.

---

### Post by DRF on 2006-03-14
Have you tried a 32bit version of the live CD in case it's just a 64bit issue?

Also have you checked the CD image to see if it's corrupt at all?

The bootup screen should have some documents on specifc problems with some hardware and have some options you can enter at the command line.
Often on some hardware using the option noapic helps with some problems, so when it says 'press enter to boot' type in:

live noapic nolapic

and that might help (had to use those arguments a few times myself)

Pressing F1 will give you some help documents and there is a page there with other boot options that might help if you have certain hardware combinations.

Daniel

---

