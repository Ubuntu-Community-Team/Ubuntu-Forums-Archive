---
title: "&quot;GRUB&quot; hangs after Karmic 9.10 AMD64 Install"
date: 2009-11-06
forum: x86 64-bit Users
---

### Post by RugeUKG on 2009-11-06
Hi Folks,

I downloaded the Live Disc last night and installed Karmic on my machine. I wiped out all my drives and made 2 partitions:

Ext4 - Mount Point \ - 50GB
Ext4 - Mount Point \home - 200GB

No swap space as I have 5.5GB RAM.

However when I reboot my machine at the end (or in any instance of booting) my system hangs with the text "GRUB" on the bottom left corner and I cannot do anything.

In my noobness I tried to reinstall Karmic and got the same issue.

If anyone can help me it would be greatly appreciated as my system is rendered useless now as I cannot boot to it. Not sure why this would happen, all I did was burn the ISO and install Ubuntu and it doesnt work :/ (but im learning!)

---

### Post by Jive Turkey on 2009-11-06
One of the things I tried before giving up on karmic was to make a separate /boot partition ~100MB is more than enough.  Also, if you have multiple HDDs make sure the bootloader is installed to the right one.  

On the last page of the installer before it starts installing there is a button in the lower right that says "advanced" or something like that.  It gives you the option of selecting which drive the bootloader is written.  The drive naming is the older hd0, hd1 format.  Make sure that agrees with your bios setting on which HDD to boot.

[edit] I just reread your post and I think you should try changing the boot device order in you bios first.

---

### Post by RugeUKG on 2009-11-06
You champion! Yeah I reinstalled Ubuntu, set a 1000MB Boot actually (I have the space heh), and by default it was installing the bootloader on the wrong drive! 

Fixed, here's a proverbial beer for you!

---

### Post by bonestonne on 2009-11-06
my advice for situations like this is to unplug unnecessary drives during the install process. i have a separate OS and data drive setup, so to prevent problems i unplug the data drive when installing an OS.

---

