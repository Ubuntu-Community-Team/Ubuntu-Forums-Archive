---
title: "Local Zim Repository Guide"
date: 2008-10-21
forum: Zimbabwe Team
---

### Post by kthaker on 2008-10-21
Hi,

Please find details on how to connect to our local repository
below. This repository is up to date, and checks for package updates twice a day to ensure that security patches/updates are available when released internationally.

Connection to the mirror is provided free to all Zimbabweans, regardless of your ISP, so that you may experience lightning fast downloads at the maximum speed of your internet connection, without having to pay the price of international bandwidth 
on your quota.

Unfortunately, to connect to this repository, you may need to perform some old skool sources.list file editing, until we can come up with a better solution for you... (which we are looking into)

The repository is being updated constantly and will contain all the new releases...as well as ISO's. You may download Ubuntu iso's from this site:

[http://archive.ubuntu.org.zw/ubuntu/iso/](http://archive.ubuntu.org.zw/ubuntu/iso/)

[B]To connect to our Local repository, please specify the following in your sources.list file
as per below, then run "apt-get update".[/B]

[B]You may need to comment out all other entries in the sources.list with a "#", and only leave our settings. 

Please do not add deb-src, the sources still have not been added to the repository as yet. 

N.B only add the version of ubuntu that you are using to your sources.list

# Hardy Heron 8.04
deb [http://archive.ubuntu.org.zw/ubuntu](http://archive.ubuntu.org.zw/ubuntu) hardy main restricted universe multiverse
deb [http://archive.ubuntu.org.zw/ubuntu](http://archive.ubuntu.org.zw/ubuntu) hardy-updates main restricted universe multiverse
deb [http://archive.ubuntu.org.zw/ubuntu](http://archive.ubuntu.org.zw/ubuntu) hardy-security main restricted universe multiverse

# Debian Etch4.0
deb [http://archive.ubuntu.org.zw/debian](http://archive.ubuntu.org.zw/debian) etch main contrib non-free
deb [http://archive.ubuntu.org.zw/debian](http://archive.ubuntu.org.zw/debian) proposed-updates main contrib non-free
deb-amd64 [http://archive.ubuntu.org.zw/debian](http://archive.ubuntu.org.zw/debian) etch main contrib non-free
deb-amd64 [http://archive.ubuntu.org.zw/debian](http://archive.ubuntu.org.zw/debian) proposed-updates main contrib non-free

# Gutsy Gibbon 7.10
deb [http://archive.ubuntu.org.zw/ubuntu](http://archive.ubuntu.org.zw/ubuntu) gutsy main restricted universe multiverse
deb [http://archive.ubuntu.org.zw/ubuntu](http://archive.ubuntu.org.zw/ubuntu) gutsy-updates main restricted universe multiverse
deb [http://archive.ubuntu.org.zw/ubuntu](http://archive.ubuntu.org.zw/ubuntu) gutsy-security main restricted universe multiverse

# Fiesty Fawn 7.04
deb [http://archive.ubuntu.org.zw/ubuntu](http://archive.ubuntu.org.zw/ubuntu) feisty main restricted universe multiverse
deb [http://archive.ubuntu.org.zw/ubuntu](http://archive.ubuntu.org.zw/ubuntu) feisty-updates main restricted universe multiverse
deb [http://archive.ubuntu.org.zw/ubuntu](http://archive.ubuntu.org.zw/ubuntu) feisty-security main restricted universe multiverse

# Intrepid 8.10
deb [http://archive.ubuntu.org.zw/ubuntu](http://archive.ubuntu.org.zw/ubuntu) intrepid main restricted universe multiverse
deb [http://archive.ubuntu.org.zw/ubuntu](http://archive.ubuntu.org.zw/ubuntu) intrepid-updates main restricted universe multiverse
deb [http://archive.ubuntu.org.zw/ubuntu](http://archive.ubuntu.org.zw/ubuntu) intrepid-security main restricted universe multiverse
[/B]

This repository is setup primarily for Local Zimbabweans, 
therefore international users may experience severely slow connections,if not constant time outs.
 
Lastly, a big thank you to Yoafrica for their hosting and bandwidth contributions to the Ubuntu Zimbabwe Team.

Any feedback is much appreciated, and if you need help, please
contact us on [email]repo@ubuntu.org.zw[/email].

:guitar:

---

### Post by NIT006.5 on 2008-10-23
Hey Kalpesh, many thanks dude!!!

---

