---
title: "problem with disk space"
date: 2008-10-01
forum: x86 64-bit Users
---

### Post by tesla.coil on 2008-10-01
[IMG]http://i36.tinypic.com/fog9ch.jpg[/IMG] here is the snap. i installed ubuntu on a 20 GB partition the prblm is i have ran out of space for /usr,as a result i cannot update or install anything since it has no disk space.hw can i increase the disk space for it ?sda 1 sda 5 and sda6 are my windows ntfs partition.

---

### Post by ajgreeny on 2008-10-01
Is there a particular reason for having such a complicated partition arrangement on your machine?  There is seldom a need to have 8 separate partitions for an install of a linux distro, and with such a small space available (20GB) it would appear to be very wasteful.  I suggest you backup, and then reinstall usingb a separate /home, /(root) and swap, and leave it at that, not worrying about the separate /usr,  /var, /opt, /tmp, /srv and /boot.

---

### Post by tesla.coil on 2008-10-01
hmm so u suggest i do a fresh install by selecting / /boot ,/home and /root and swap manually and leave rest for the OS to do it automatically? well i get that still is there any way i can extend that the disk space for /usr? isnt 20 GB hdd nuff for ubuntu? i have dual booting winxp and ubuntu on a 80 GB hdd where 20 GB is alloted to ubuntu. rest of 60 GB for win

---

### Post by cariboo on 2008-10-02
I have use 15GB for / and have never run out of space, I always keep an eye on /var/cache/apt/archives, as all those .deb files do take up a lot of room. You have to remember that /usr is where all the documentation, library and applications are stored, if anything /usr and /var should be larger than any of the other directories except for /home.

You have a really complicated setup, I would also suggest  with only 20Gb you should only need /, /home and /swap

Jim

---

### Post by tesla.coil on 2008-10-02
well ill try installating again i wanna knw how much diskspace shud i allot for / /home /boot and /usr and /var? wihtout reinstallating the OS is there anyother alternative?

---

### Post by tesla.coil on 2008-10-02
well am abt to freshly install ubuntu i just wanna knw hw much diskspace shud i allot for / /root /home /usr /var

---

### Post by ajgreeny on 2008-10-02
> well am abt to freshly install ubuntu i just wanna knw hw much diskspace shud i allot for / /root /home /usr /var 	OK, I'll ask again.  Why do you need a separate /var and /usr partition?  With 20GB to play with go for about 6GB for /, max of 1GB for swap and the rest for /home.  Forget about /var and /usr, it just makes things too complicated.

---

