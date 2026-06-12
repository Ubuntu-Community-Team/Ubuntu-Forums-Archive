---
title: "Problems with HDD"
date: 2006-12-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by alex109 on 2006-12-19
Here is my problem. I have pc with two hdds. On first (maxtor ata, 7200, 120gb) I have couple of partititions, and winXP and Ubuntu 6.06 (64b) instaled. Because I keep lots of media files on my PC, i had to buy another hdd, and I bouth maxtor, 160gb, sata. Now, I've store my media files on it, and I've been using them completly normal in xp. Ubuntu, however, recognise that hdd, but he won't let me mount it. Any ideas what should I do?
btw, I am an absolute beginner in Ubuntu, so please don't laugh if this is some common thing, that everybody knows how to solve...
Thanks in advance  ;)

---

### Post by tszanon on 2006-12-19
Have you run mount with sudo? For example:
```
sudo mount /dev/sda1
```

(I assume you're trying to mount the partition using the Terminal...I don't know any other way to do it)

And you can also alter /etc/fstab to automatically mount it every boot, but I don't remember how to do it.

---

