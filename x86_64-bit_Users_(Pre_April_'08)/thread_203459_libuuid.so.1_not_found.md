---
title: "libuuid.so.1 not found?"
date: 2006-06-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by gratefulfrog on 2006-06-25
I've got a "file not found" error for an app that needs libuuid.so.1. This file is in fact in /lib but the app (opencroquet) can't find it on the 64bit platform.

In the same place, the same app finds it ok under a 32bit dchroot.

Looking over the forums, it seems that others have had similar problem.  

Anyone have a solution?

Cheers,
GF

---

### Post by Kilz on 2006-06-25
[QUOTE=gratefulfrog]I've got a "file not found" error for an app that needs libuuid.so.1. This file is in fact in /lib but the app (opencroquet) can't find it on the 64bit platform.

In the same place, the same app finds it ok under a 32bit dchroot.

Looking over the forums, it seems that others have had similar problem.  

Anyone have a solution?

Cheers,
GF[/QUOTE]
I have a solution. [The package that contains that lib is available here]("http://packages.ubuntu.com/dapper/libs/libuuid1") 
If you are trying to add this lib so a 32 bit application you have forced in or inslalled to  works here is what you do.
First download the file for i386 if its a 32 bit program. Second make sure this package is installed
```
sudo apt-get install dpkg-dev
```
After that package is installed you will be able to use your archive program to extract the contents of the .deb file. When you extract the contents of the .deb file you will see the data.tar.gz, extract the contents to your desktop. Then copy the lib into /usr/lib32
```
sudo cp -r -p ~/Desktop/usr/lib/* /usr/lib32
```
If you find you need other libs [you can go here]("http://packages.ubuntu.com/") and do a package contents search and do the same thing.

If on the other hand this is a 64 bit application. [This link also]("http://packages.ubuntu.com/dapper/libs/libuuid1") contains a download for a 64 bit package that Gdebi can install.

---

### Post by gratefulfrog on 2006-06-26
Hey thanks to Kilz!

And I did check out your site! Great that you put the firefox 32 flash howto back up!

Have you ever tried and/or got the nswrapper to work to make the 64bit firefox work with 32bit plugins?  I tried to follow some links but ... oh well! I'm still using your solution!

Cheers,
GF.
[http://gratefulfrog.net]("http://gratefulfrog.net")

---

### Post by Kilz on 2006-06-26
[QUOTE=gratefulfrog]Hey thanks to Kilz!

And I did check out your site! Great that you put the firefox 32 flash howto back up!

Have you ever tried and/or got the nswrapper to work to make the 64bit firefox work with 32bit plugins?  I tried to follow some links but ... oh well! I'm still using your solution!

Cheers,
GF.
[http://gratefulfrog.net]("http://gratefulfrog.net")[/QUOTE]
Glad you like the site, its just starting out. I paid for 5 years of the domain 3 years ago when it was a bittorrent tracker. Since it has 2 years to go I figured id put it to use. I have tried the nswrapper and couldn't get it to work. I'm using 32 bit firefox setup like my howto. To bad the doc team had to take down the original, but I think I have improved it a little.

---

### Post by alexcj on 2008-06-19
Thanks a lot! 

It helped me to get my stuff working!

Cheers,
Alex

---

