---
title: "Hibernate crashed, now wont even boot up, please help!!"
date: 2008-11-02
forum: x86 64-bit Users
---

### Post by Purple_Potato on 2008-11-02
I was running a game in the AMD64 ubuntu when apparently some weird button pressing made ubuntu 8.10 go into hibernate, but it crashed while going into hibernate, and now the computer wont even boot up, normally, in safe mode, or even from the install CD. It just gives me an unending stream of each slightly unique error messages like this:

{initramfs)   
[81.840658] ata9.00: exception Emask 0x0 Sact 0x0   action 0x2 frozen
[81.840700] ata9.0: cmda0/00:00:00:00:20/00:00:00:00:00/a0 tag 0 cdb 0x12 data 36 in

(and so on, and on...)

I really need help, I cant boot up at all, get to my files! Please help!

---

### Post by PatrickVogeli on 2008-11-02
when you are in grub, press e in the kernel you want to boot, then you enter the grub edit mode. Go to the second line and after quiet splash type noresume, then press enter an then b.

let's see if it boots

---

### Post by homerhomer on 2008-11-03
Sounds like you have the same issue I have

[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/292515](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/292515)

---

