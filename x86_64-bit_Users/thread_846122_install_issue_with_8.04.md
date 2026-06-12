---
title: "install issue with 8.04"
date: 2008-07-01
forum: x86 64-bit Users
---

### Post by hogi on 2008-07-01
I am running a desktop with an AMD Athlon 64 4000 San Diego processor on an ASUS A8v-XE motherboard with 2 gb of ram.HP 160gb sata hard drive. I am currently running Ubuntu 7:10 as the OS.This set-up works great. 

The problem is that I can not upgrade or do a clean install of Hardy Heron. On an upgrade,the program stalls at the partioning stage saying that the root can not be found. On a clean install the dvd will load and then stay at a prompt that says "initramfs"

I downloaded a new iso this morning from a different mirror and got a new message about 10 seconds after the "initramfs" flashed on my screen.. It is a lot of info which to it looks like it means that my hardware  does not like this new Ubuntu 8.04.

This is the message that I am now receiving: (150.350301)   8139 cp 000.0a.0   This(id 10ec 8139 rev 10 is not an 8139C+ compatible chip)   150.350.360 8139 cp  0000:0a 0d 0   Try the "8139 too driver" instead.

I have also tried installing the Linux Mint OS. As long as I stay with the Darnya version my system works just fine. If I try to install the Elyssa 5 version I get a repeat of the Ubuntu Hardy Heron install problems.

Thank you to any and all Unbuntu people who can help me with this install "scenario".

Hogi
New to Linux and loving it better than windows.

---

### Post by Yellow Pasque on 2008-07-01
> (150.350301) 8139 cp 000.0a.0 This(id 10ec 8139 rev 10 is not an 8139C+ compatible chip) 150.350.360 8139 cp 0000:0a 0d 0 Try the "8139 too driver" instead.


It's referring to your Ethernet/LAN chip (Realtek 8139C+). However, I don't think this should halt the whole install. Just to see if it is, try disabling your onboard LAN in the BIOS (usually under 'integrated peripherals' or 'onboard devices' menu).

---

