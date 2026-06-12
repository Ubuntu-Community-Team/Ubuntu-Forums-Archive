---
title: "Real Player"
date: 2008-01-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by ibizatunes on 2008-01-16
Hello
I want to be able to install real player, its not in the syptmatic source.....
when i go to the realplayer site [http://www.real.com/linux](http://www.real.com/linux) and u download doesnt do anything.....

so i found this website [https://player.helixcommunity.org/2005/downloads/](https://player.helixcommunity.org/2005/downloads/)
I can download both .bin and rpm, but i cant seem to install either of them
Please could someone tell me how to

I have download them to the desktop
the file names are
HelixPlayer-1.0.9.816-20070818.i586.rpm
RealPlayer-10.0.9.809-20070726.i586.rpm
hxplay-1.0.9.816-linux-2.2-libc6-gcc32-i586.bin
realplay-10.0.9.809-linux-2.2-libc6-gcc32-i586.bin

I dont need all of them install preferable the real player version, but as long as the bbc website plays audio again i will be happy!

---

### Post by Kilz on 2008-01-16
> **ibizatunes said:**
> Hello
I want to be able to install real player, its not in the syptmatic source.....
when i go to the realplayer site [http://www.real.com/linux](http://www.real.com/linux) and u download doesnt do anything.....

so i found this website [https://player.helixcommunity.org/2005/downloads/](https://player.helixcommunity.org/2005/downloads/)
I can download both .bin and rpm, but i cant seem to install either of them
Please could someone tell me how to

I have download them to the desktop
the file names are
HelixPlayer-1.0.9.816-20070818.i586.rpm
RealPlayer-10.0.9.809-20070726.i586.rpm
hxplay-1.0.9.816-linux-2.2-libc6-gcc32-i586.bin
realplay-10.0.9.809-linux-2.2-libc6-gcc32-i586.bin

I dont need all of them install preferable the real player version, but as long as the bbc website plays audio again i will be happy!

Ok, first off those packages (bin) are installable. if you place one on the desktop, open a terminal, and type in these commands.

```
cd ~/Desktop
./realplay-10.0.9.809-linux-2.2-libc6-gcc32-i586.bin
```

But it will only install the stand alone real player, not the browser plugin.
The mozilla-plugin-vlc package will install a plugin that should play things on the bbc website. You may get (no video) as its downloading, and it may take a few minutes to start. But it should play.

---

### Post by timzak on 2008-01-17
Is this installable on Gutsy 64bit?  Anything special need to be done?

Thanks.

---

### Post by oldos2er on 2008-01-17
> **timzak said:**
> Is this installable on Gutsy 64bit?
 Anything special need to be done?


 Yes, it's installable; no, nothing special needs to be done.

---

### Post by timzak on 2008-01-17
One more question, is there a difference between:
realplay-10.0.9.809-linux-2.2-libc6-gcc32-i586.bin from Real's website and

[http://archive.canonical.com/ubuntu/pool/partner/r/realplay/realplay_10.0.9-0feisty1_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/r/realplay/realplay_10.0.9-0feisty1_i386.deb)

Is one preferable over the other for Gutsy 64bit?

---

### Post by oldos2er on 2008-01-17
I don't know. Why not just get the one at [http://www.real.com/linux/](http://www.real.com/linux/) ?

---

### Post by Kilz on 2008-01-17
> **timzak said:**
> One more question, is there a difference between:
realplay-10.0.9.809-linux-2.2-libc6-gcc32-i586.bin from Real's website and

[http://archive.canonical.com/ubuntu/pool/partner/r/realplay/realplay_10.0.9-0feisty1_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/r/realplay/realplay_10.0.9-0feisty1_i386.deb)

Is one preferable over the other for Gutsy 64bit?

One is a deb file , the other an installer. Both will install real player stand alone player, no browser plugin. The deb file can be forced in. It really doesn't make any difference what install format you use in this instance because forced in 32bit deb files will not be automatically updated since they are not in the amd64 repositories.

---

### Post by ubuntu-freak on 2008-01-17
There is a plugin cos I'm using it. Gets installed into /usr/lib/firefox/plugins
 
Try my how-to
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
There is a fix for RealPlayer in my how-to if it stutters and freezes while playing also. 
 
Enjoy!
 
Nathan

---

### Post by balagunner on 2008-01-22
> **Kilz said:**
> Ok, first off those packages (bin) are installable. if you place one on the desktop, open a terminal, and type in these commands.

```
cd ~/Desktop
./realplay-10.0.9.809-linux-2.2-libc6-gcc32-i586.bin
```

But it will only install the stand alone real player, not the browser plugin.
The mozilla-plugin-vlc package will install a plugin that should play things on the bbc website. You may get (no video) as its downloading, and it may take a few minutes to start. But it should play.


This is still not working 

the systems seems to go numb

Please help

---

### Post by ubuntu-freak on 2008-01-22
> **balagunner said:**
> This is still not working 

the systems seems to go numb

Please help

Why don't you just use my how-to? There is a link to RealPlayer and it's an easy to install deb package. I'm using it on my system and streaming BBC sites with it and some radio streams.

[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

Nathan

---

### Post by MikeSz on 2008-02-26
> **Kilz said:**
> Ok, first off those packages (bin) are installable. if you place one on the desktop, open a terminal, and type in these commands.

```
cd ~/Desktop
./realplay-10.0.9.809-linux-2.2-libc6-gcc32-i586.bin
```

But it will only install the stand alone real player, not the browser plugin.
The mozilla-plugin-vlc package will install a plugin that should play things on the bbc website. You may get (no video) as its downloading, and it may take a few minutes to start. But it should play.

This doesnt seem to work for me??? I get the following.....

zer0cool@zer0cool-laptop:~$  cd Desktop
zer0cool@zer0cool-laptop:~/Desktop$ ./realplay-10.0.9.809-linux-2.2-libc6-gcc32-i586.bin
bash: ./realplay-10.0.9.809-linux-2.2-libc6-gcc32-i586.bin: Permission denied
zer0cool@zer0cool-laptop:~/Desktop$ sudo ./realplay-10.0.9.809-linux-2.2-libc6-gcc32-i586.bin
[sudo] password for zer0cool:
sudo: ./realplay-10.0.9.809-linux-2.2-libc6-gcc32-i586.bin: command not found
zer0cool@zer0cool-laptop:~/Desktop$ sudo ./realplay-10.0.9.809-linux-2.2-libc6-gcc32-i586.bin
sudo: ./realplay-10.0.9.809-linux-2.2-libc6-gcc32-i586.bin: command not found
zer0cool@zer0cool-laptop:~/Desktop$

---

### Post by ubuntu-freak on 2008-02-26
You don't need to install the bin. See part 2 of my [how-to](http://ubuntuforums.org/showthread.php?t=661833).
 
Nathan

---

### Post by shadmy on 2008-02-28
> **timzak said:**
> One more question, is there a difference between:
realplay-10.0.9.809-linux-2.2-libc6-gcc32-i586.bin from Real's website and

[http://archive.canonical.com/ubuntu/pool/partner/r/realplay/realplay_10.0.9-0feisty1_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/r/realplay/realplay_10.0.9-0feisty1_i386.deb)

Is one preferable over the other for Gutsy 64bit?

thanks for this 
:lolflag:

---

