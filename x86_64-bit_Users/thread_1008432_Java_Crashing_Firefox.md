---
title: "Java Crashing Firefox"
date: 2008-12-11
forum: x86 64-bit Users
---

### Post by Nintendo01 on 2008-12-11
I currently have the OpenJDK6 and Icedtea Plugin for my Java with my system fully updated. Recently, within the past couple of weeks, an online Java game I play (Arcanists on FunOrb.com) randomly crashes during games. I can be playing for hours or just a few minutes, but it will almost always crash Firefox while I'm playing.

Thinking back, the only new update that would affect it would be possibly a Firefox update, since I don't remember any recent OpenJDK updates. 

I'm running 64 bit Intrepid, 2 gigs ram, core 2 duo processor at 2.53 GHz.

Any other specs or command outputs anyone needs, just ask. I've been running Ubuntu for about a year now, but I still don't know very much about it, so any help is greatly appreciated.

---

### Post by nicholasd on 2008-12-27
I have a similar problem with Java locking up firefox.  I use the Hush Encryption Engine from [www.hushmail.com](www.hushmail.com), and I have trouble loading it consistently.  When it loads, firefox will take up most of the CPU time and will become unresponsive.  Weird!

Anyone know of this bug?

---

### Post by zika on 2008-12-27
why not install Alpha 64-bit Java plugin? on 24.12.08. they made available b03 subversion.

```
wget http://www.java.net/download/jdk6/6u12/promoted/b03/binaries/jre-6u12-ea-bin-b03-linux-amd64-22_dec_2008.bin
cd /opt
sudo sh ~/**where_You've_downloaded_it**/jre-6u12-ea-bin-b03-linux-amd64-08_dec_2008.bin
cd /usr/lib/mozilla/plugins
sudo ln -s /opt/jre1.6.0_12/lib/amd64/libnpjp2.so
```Enyou!

---

### Post by balaknair on 2008-12-28
See this thread for instructions on installing Java 64bit

[http://ubuntuforums.org/showthread.php?t=1013658](http://ubuntuforums.org/showthread.php?t=1013658)

---

