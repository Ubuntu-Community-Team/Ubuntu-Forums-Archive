---
title: "[SOLVED] corrupt or inexistant vmlinuz kernel"
date: 2008-11-03
forum: x86 64-bit Users
---

### Post by linuxuser12901290 on 2008-11-03
First off, I'm new to the forum but not to linux nor ubuntu. In fact, I consider myself to be at least a higher intermediate user.

About my problem now: since my money-back warranty finally invalidated, I decided to install ubuntu on my new computer, a HP a6518f with an AMD64 5400+ x2 (2.8 GHZ), 3GB ram, nVidia 8600GTS and a 465W power supply (if that has anything to do with things...)

First thing I did: I opened the Vista disk manager and freed as much space as I could (merely 15% total, while I've got over 75% free, wtf!?) 

Then, I went to the ubuntu.com website and started direct downloadig Ubuntu 8.10. Then, when it was completed, I downloaded and ran unetbootin, with which I used to be able to install without problem ubuntu 8.04 on another computer.

After it told me everything was complete, I rebooted and started installing Ubuntu.

**Problem 1:**
Ubuntu wouldn't recognize any partition until I umount -l /dev/sda1 'd (sda1 being my main (and only) drive (C:\), Vista partition). Then, it detected all partitions and I manually set out of the available space a 5GB swap partition and a 110GB ext3 root (/) partition. Once this was done, Ubuntu installed everything for me and prompted me to reboot. So did I.

**Problem 2:**
Ubuntu's grub menu would only let me boot in either Vista's recovery partition (wft??) or Ubuntu's memtest.

I used the edit command and then "dir /boot/" to check its content, hoping I could change to the vmlinuz kernel instead of the memtest kernel. Guess what? There was **no vmlinuz file in any directory, including /boot.**

After editing the vista partition to boot into vista, I reinstalled Ubuntu from a torrent, this time, and used EasyBCD to reinstall the vista boot loader. I re-unetbootin'd the new file (I know its 100% new since I deleted the corrupt one first), and retried the procedure, leading me to the exact same problems. 

Could anyone help me solve this? I really like Ubuntu and each minute passed in vista, I tend to learn a whole bunch of new words. Any help/thought/comment appreciated greatly.

---

### Post by bwhite82 on 2008-11-03
Hmmm..this all seems more complicated than it needs to be. Why are you using unetbootin?

---

### Post by linuxuser12901290 on 2008-11-04
Well, obviously because I lack any CD/DVD/USB with enough space to put it on. My last CD-R got wasted on trying to install 8.04 on another computer a while back. That's when I tried unetbootin and was finally able to install it.

Because of the lack of CD, also, I can't use the alternate ISO (just tried that, it complains that there is no CD in the drive) and Ubuntu doesn't recognize my Wireless USB key or lack the drivers to make it work, so no network install for me.

---

### Post by linuxuser12901290 on 2008-11-08
Ok, I solved my problem by downloading and installing 8.04 and then upgrading.

---

