---
title: "Which BusyBox command should I use to start Xubuntu 64-bit?"
date: 2009-04-04
forum: x86 64-bit Users
---

### Post by crossx14 on 2009-04-04
Hi,
I downloaded a Xubuntu 64-bits live-cd .iso image and burned it in a CD, but it does not start.
Suspecting of my CD/DVD drive, I tried to start it right from the .iso image file by using grub4dos.
I copied to the root of drive C: the .iso file renamed it as linux.iso, and the file grldr, and the file menu.lst, edited to look like this:

color blue/green yellow/red white/magenta white/magenta
timeout 30
default /default

title Linux
fallback 1
find --set-root --ignore-floppies /linux.iso
map /linux.iso (hd32)
map --hook
chainloader (hd32)
rootnoverify
boot

I also edited boot.ini to add the line C:\grldr="Linux".

Grub4dos worked OK.
Xubuntu seem to start at first, but after saying "Loading, please wait", it appears the BusyBox v1.10.2 ..., wiht the prompt (initramfs).
I do not what to do there.
I just use the reboot command to restart in Windows XP 64-bits.
So, this is my question:
What should I do at BusyBox's prompt (initramfs)?.
Best regards.

---

### Post by tinybit on 2009-04-12
Hello, crossx14,

I have a working menu.lst for starting Ubuntu LiveCD:
```

title Ubuntu LiveCD

find --set-root /ubuntu-9.04-beta-desktop-i386.iso

map /ubuntu-9.04-beta-desktop-i386.iso (0xff)

map --hook

root (0xff)

kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=/ubuntu-9.04-beta-desktop-i386.iso quiet splash locale=zh_CN.UTF-8 --

initrd /casper/initrd.gz
boot

```
This works well with the ISO in my thumbdrive. You may replace "locale=zh_CN.UTF-8" with your locale, or simply strip it out for the default English locale.

---

