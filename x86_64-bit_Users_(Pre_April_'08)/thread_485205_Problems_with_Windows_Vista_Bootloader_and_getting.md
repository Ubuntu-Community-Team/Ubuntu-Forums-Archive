---
title: "Problems with Windows Vista Bootloader and getting Ubuntu 7.0.4 to load on restart"
date: 2007-06-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by ian.wax on 2007-06-26
My machine came preloaded with Vista and I want to get a dual boot to choose between Vista and Feisty Fawn upon start up.    I have tried to use a copy of Feisty Fawn 7.0.4 burned onto a DVD to install itself, but the only thing that comes up is the bootloader showing Vista, with no option of installing Feisty Fawn.   I have partitioned my drive and I have read many posted threads on how to load Feisty Fawn, but I cannot seem to get passed this problem of the already installed bootloader.  

I am fairly new to Linux, any suggestions on how to remedy this without compromising Vista?

---

### Post by Yoooder on 2007-06-26
Have you gotten your machine to boot from your burned DVD?  Or when you restart does it just go and load Vista right away?

If it's going straight to Vista, then either the CD you burned isn't bootable, or (probably more likely) your machine isn't configured to boot from CD/DVD.

Here's what to try:  Right after you turn on your machine, keep your eye's peeled for a message that says something to the effect of "Press F1 to enter setup, Press F2 to Select Boot Device"

If the message appears do what it says (either option will work for your needs).  If you don't see a message then try tapping Esc, F1, F2, and F12 (all separately, these are the most common keys for Setup/Boot options).

If you get into Boot Options: it should be a fairly short list consisting of things like "boot from first hard drive, boot from CD, boot from USB drive" -- make sure your Ubuntu DVD is in your drive, and select "Boot From CD"

If you get into Setup, there could be half a dozen different menus.  **Firstly, be careful--this is where the machine's most basic settigns are configured** -- so don't play with things you don't understand.  Look for a "Boot Order" or "Boot Options" screen, and when you find it make sure that "Boot from CD" is above "Boot from first hard drive" (these are all paraphrasing, each machine's Setup is a bit different).

Now, your computer should boot from the DVD, and present you with a menu to Start/Install Ubuntu or do a variety of other tasks.  Choose "Start/Install" (the 1st choice) and let Ubuntu load.  You will soon see a fully functional desktop with an "Install" icon on the desktop...  follow your tutorials from here

---

### Post by ian.wax on 2007-06-26
> **Yoooder said:**
> Have you gotten your machine to boot from your burned DVD?  Or when you restart does it just go and load Vista right away?

If it's going straight to Vista, then either the CD you burned isn't bootable, or (probably more likely) your machine isn't configured to boot from CD/DVD.




The machine has never booted from my burned DVD.  I checked the boot priority, the DVD drive is listed first, but if I leave the machine to load with DVD in, the machine reads the DVD and goes right VISTA.  If I choose the Boot Menu, it only demonstrates Vista.

---

### Post by Yoooder on 2007-06-27
It sounds like your DVD isn't bootable.  Here's how the quick & dirty process to burn a bootable CD...

1) Get a CD-image (also known as an ISO).  Here's the 7.04 ISO straight from Ubuntu:
[http://releases.ubuntu.com/feisty/ubuntu-7.04-desktop-i386.iso]("http://releases.ubuntu.com/feisty/ubuntu-7.04-desktop-i386.iso")

2) Follow this walkthough:
[https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

Also, if you have trouble with the process, feel free to PM with a mailing address.  I'd be glad to burn a copy for you and get it in the mail.

---

### Post by xseraph on 2007-06-27
Yeah. The logical conclusion would be just that, that the DVD was not originally bootable. I tried to burn the Ubuntu CD image to a DVD for booting on my laptop just an hour ago, but my burning app would not let me burn the CD ISO to the DVD. 

Which really is quite annoying. I dont have any blank CDs but desperatly need to get a bootable disc for my laptop. Any alternatives? Can anyone tell me if it is at all possible to make a bootable DVD out of the avalibale ubuntu cd images? Or if I can boot the image in some other way? 

@Mods: Feel free to part this reply into it's own thread if this qualifies as a thread hijac. I just though the asnwer to this problem might assist the thread op in case her/his problem actually was the fact that he tried to boot with a dvd.

EDIT: Just found an Ubuntu dvd image file now, so think my problem is solved. Not sure about the source though, so if anyone could link to an Ubuntu 7.04 desktop dvd image they know is safe, that would rock

---

