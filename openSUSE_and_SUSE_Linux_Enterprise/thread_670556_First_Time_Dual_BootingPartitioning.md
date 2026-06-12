---
title: "First Time Dual Booting/Partitioning"
date: 2008-01-17
forum: openSUSE and SUSE Linux Enterprise
---

### Post by kiisu on 2008-01-17
I would like to give Suse a try without losing all the hard work I've put into this Ubuntu setup.

 Note, I'm only a couple months into Linux and have never tried any partitioning before.

In the Suse liveCD I started to go ahead with installation but chickened out. Ubuntu is on sda1, so when the installation says under "partitioning' that it will format that drive, I am clueless as to whether that means it will automatically partition, or wipe it clean and leave me with only Suse. 

What should I be doing here wise people?

---

### Post by kiisu on 2008-01-17
to be clear, it is automatically set to install this way:

PARTITIONING
-Format partition /dev/sda1 (108.9 GB) for / with ext3
-Use /dev/sda5 as swap


Will I lose my current system this way?

---

### Post by Incense on 2008-01-17
Yeah, you'll lose your current setup. You'll need an extra partition for SUSE if you want them both installed at the same time. I would run the Ubuntu live disc, and use gparted to resize your partition so you'll have an extra to use for SUSE or what ever you want. While your at it, you may want to set up a home partition for the distros to share.  

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

As always though **BACKUP YOUR DATA BEFORE YOU DO ANYTHING LIKE THIS!** You never know what will go wrong. Let us know how it goes!

---

