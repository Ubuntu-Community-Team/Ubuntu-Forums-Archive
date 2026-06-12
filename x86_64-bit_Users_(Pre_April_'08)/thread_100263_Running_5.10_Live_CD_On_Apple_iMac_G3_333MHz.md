---
title: "Running 5.10 Live CD On Apple iMac G3 333MHz"
date: 2005-12-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by dmwillis2000 on 2005-12-07
Hi, I do not have much experience with Macs or Ubuntu on them. I have a Rev D 333MHz with 160Mb of RAM. I have no hard disk drive attached as it is cooked. This meets the spec needed. I have tried to burn ISO's and that failed so I ordered the 'real' cd-roms. The CD Boots fine and gets through to Preparing for Live Session and sometimes it freezes whilst loading at 91%. Other times it gets through to Loading Please Wait... Does anyone know how to get it to boot. I am truely puzzled by this.

Dean

---

### Post by kalin on 2005-12-07
You'll have a hard time using the Live CD with so little RAM, I've tried that on an 500MHz iMac with 192MB RAM, and it's very slow. I did get it running fine at some point, by forcing it to use a swap partition on a HDD. I would recommend getting a cheap HDD instead and installing Ubuntu on it.

The Live CD literally builds a virtual filesystem in RAM, representing an installed Ubuntu, pulling and caching static files from the CD, and keeping dynamic files (things like log files) into RAM. This consumes a lot of space, which would otherwise be left free for use when running an installed on the HDD system.

---

