---
title: "Installing Ububtu x86-64 on Mac Pro"
date: 2007-01-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by zbittner on 2007-01-15
I've been using some programs for school on Linux machines, so I decided to try to install it on my own machine.

I'm trying to get Ubuntu to work on my Mac Pro, and I was successfully able to boot Ubuntu x86-64 using a live cd, and the installer worked until it got to the GRUB bootloader, which, from what I've read isn't supposed to work. I then installed rEFIt in Mac OS X, and it doesn't see the linux partition. so I found instructions for getting Ubuntu to work on Intel Macs at [/bin/false]("http://bin-false.org/?p=17"). Those instructions worked until I got to the part about installing lilo. The instructions say to type into terminal 

"apt-get install lilo lilo-doc linux-686-smp linux-restricted-modules-2.6.15-23-686 linux-kernel-headers"

I noticed the instructions were from June 2, which was before the 64 bit MacBooks were released, so the version being used was the 32 bit version. Does that have anything to do with the problem? If so, how do I get around it.

Thanks

I wasn't sure whether to post this in the PPC Mac forums, because my computer is a Mac, or in the x86-64 forum because that is my processor architecture. I apologize if this is the wrong forum.

Edit: In case this effects anything, I have 2 hard drives, and Ubuntu was installed on hd1, not hd0

---

### Post by RAOF on 2007-01-15
You could just "apt-get install lilo lilo-doc".  The other things on that line are either wrong (linux-686) or things you probably don't need (linux-headers).

Actually, you probably **will** need linux-headers because you'll probably be building drivers from source to try to wrest some functionality out of Apple's proprietary system :p

---

### Post by kvapil on 2007-01-16
Im trying the same thing but i dont get that far. DO i have to use bootcamp etc? i whant to have a singel boot no osx at all in my mac pro.

/martin

---

### Post by AntonioRubio on 2007-01-16
> **kvapil said:**
> Im trying the same thing but i dont get that far. DO i have to use bootcamp etc? i whant to have a singel boot no osx at all in my mac pro.

/martin

I haven't seen a way to do it without some kind of Mac utility (I use rEFIt + lilo).  You would probably want to keep a minimal OS X install to access the BIOS.

The instructions I followed were [http://bin-false.org/?p=17](http://bin-false.org/?p=17) (the same as you tried).  What error message did you get when installing lilo?  I went through the process less than a week ago.

---

### Post by zbittner on 2007-01-19
I ended up using the 32 bit version, and was able to install lilo, except when I rebooted after installing linux, and I got the Operating System not found message for both Linux and Windows.

---

### Post by bernardfrancois on 2007-01-21
I just read [here]("https://wiki.ubuntu.com/IntelMacSupport") that grub has been patched to support intel-based macs:

> 
Of the available boot loaders, none currently boots Intel-based Macs smoothly. The  grub2 specification should deal with this; if it does not, we will make use of refit, which is known to work. [As it turns out, grub has now been patched to deal with Intel-based Macs, so we no longer need this step.]


---

### Post by sjatkins on 2007-03-02
What are people installing for X86-64 on a Mac Pro?  The AMD 64 distribution objected to my attempt to install it on a Mac Pro.  Is there a mode or something I missed on the installation?  If so please kindly point it out.  Thanks.

---

### Post by sjatkins on 2007-04-28
Edgy install fine or at least the alternate disk does.  But when X attempts to start I get a orange screen and no login dialog.  The screen sort of pulsates it is not stable.  Installation installed the nv driver.  The sync parameters look ok.  Ideas?  Tools I can run from recovery command line?  Should I just pull the nvidia driver and use that instead?  Any idea why the installation installs X in a way that it will not come up?  This is a standard Mac Pro and thus has a GeFroce 7300 GT.  Monitor is Apple 23 inch.

---

