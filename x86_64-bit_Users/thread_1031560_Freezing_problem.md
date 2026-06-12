---
title: "Freezing problem"
date: 2009-01-05
forum: x86 64-bit Users
---

### Post by galojze on 2009-01-05
Hello

Ive been using ubuntu for aprx. 2 months, constantly upgrading and trying to resolve my freezing and slow perfomance problem. 
My Ubuntu is freezing constantly (working in slow motion) it is present also when playing music, watching movies, flash videos (ive installed x64 flash)...
The freezing is more noticable, when using torrent software (to load torrents).
Ive checked my system monitor and there is _always_ 50% of my memory used, and about 43% swap memory used in idle (no programs running).
It seems like there is problem with HD but its kinda wierd, couse on winxp i had no problems, OS was running smoothly, now even 1 program started slows down my computer terriebly

My comp, specs:
AMD Athlon 64bit 3000+
MB: ASrock 939dual-sata2
GC: Geforce 6600GT
RAM: 1000MB DDR2
Hd: 250GB

I really like whole system but,  im stepping on the edge... couse there is no solution to this problem...

Please, very please someone help me :)
I will be very gratefull

If you need anything else please reply

---

### Post by Paul S on 2009-01-05
> **galojze said:**
> 
Ive checked my system monitor and there is _always_ 50% of my memory used, and about 43% swap memory used in idle (no programs running).

AMD Athlon 64bit 3000+


Try using  the command "top" in a terminal to get more detail about your system performance.

I'm not familiar with AMD chip speeds, but suspect the 3000+ could be getting overloaded.  With "top" you can see the cpu consumption of each process as well as the memory usage.  If you want a gui monitor on all the time, I use gkrellm.  It will show the % usage for the cpu constantly.

If you're cpu is maxed out, then you just have to get used to doing less tasks at the same time.  If firefox is maxing out, you can install adblock-plus which will allow you to kill some of the flash ads that consume a lot of cpu.  You can also use less tabs to consume less.

hth,

---

### Post by galojze on 2009-01-05
> **Paul S said:**
> Try using  the command "top" in a terminal to get more detail about your system performance.

I'm not familiar with AMD chip speeds, but suspect the 3000+ could be getting overloaded.  With "top" you can see the cpu consumption of each process as well as the memory usage.  If you want a gui monitor on all the time, I use gkrellm.  It will show the % usage for the cpu constantly.

If you're cpu is maxed out, then you just have to get used to doing less tasks at the same time.  If firefox is maxing out, you can install adblock-plus which will allow you to kill some of the flash ads that consume a lot of cpu.  You can also use less tabs to consume less.

hth,



Hello there

Thanx for fast reply!

Well this is a ss of top, gkrellm and system monitor with torrents, flash running..
It is also wierd that the problem occours when the process level is low, but not so noticible. 

[[IMG]http://img522.imageshack.us/img522/9553/screenshotzl6.th.png[/IMG]](http://img522.imageshack.us/my.php?image=screenshotzl6.png)

---

### Post by 2hot6ft2 on 2009-01-05
Had the same problem and this worked for me. AMD 64 bit, nvidia card.

Believe it or not the freezes seemed to tie into the sound Pulse Audio (when not configured properly) can send the cpu to 100% causing the freeze. This has been reported by several people and the solution is here for that.
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

I was having freezes too and since completing the how to have not had a freeze at all.

This may or may not be your particular issue but it's where I would start after reading everything I have.

Later I went this way for audio but it had nothing to do with freezes it was for a stutter when surfing and playing mp3's.
Disabling pulse and using alsa (Before deciding to remove pulse you should read the warning here as to what the result could be).
[http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a](http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a)

---

### Post by galojze on 2009-01-06
> **2hot6ft2 said:**
> Had the same problem and this worked for me. AMD 64 bit, nvidia card.

Believe it or not the freezes seemed to tie into the sound Pulse Audio (when not configured properly) can send the cpu to 100% causing the freeze. This has been reported by several people and the solution is here for that.
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

I was having freezes too and since completing the how to have not had a freeze at all.

This may or may not be your particular issue but it's where I would start after reading everything I have.

Later I went this way for audio but it had nothing to do with freezes it was for a stutter when surfing and playing mp3's.
Disabling pulse and using alsa (Before deciding to remove pulse you should read the warning here as to what the result could be).
[http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a](http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a)

Hello

Thanks for reply

I tried first pulseaudio configuration - no changes. Then I disabled pulseaudio and used alsa.
It is working slightly better, but flash videos from youtube are still freezing. I have the latest flash updates. The sound stutter problem is not present anymore.
I still have no idea why 50% of my ram is used in idle (cpu aprx. 20%, swap  0%)

any hints?? :)


thanks again

---

