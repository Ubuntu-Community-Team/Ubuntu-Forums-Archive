---
title: "WMA for 64-bit"
date: 2005-12-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by MenZa on 2005-12-03
I have a huge heap of .wma files I've ripped from misc. CDs in Windows Media Player when I was still using Windows - and now want to play them.
Because I have the 64-bit, I guess w32codecs won't run on my machine - what do I do? I've tried downloading vlc, but with no luck.

-Lasse Nielsen

---

### Post by mlomker on 2005-12-03
You'll want to take a look at the Hoary forum and/or do a search.  I use to run 64-bit Hoary and there was a way to install mplayer and point it at 32-bit libraries so that it could use the win32codecs.

This is strictly my opinion, but running 64-bit is more trouble than it is worth.  If you're doing it for educational reasons then that's cool.

---

### Post by MenZa on 2005-12-04
Nope, I'm actually doing it because I thought I'd benefit from it, seeing as this is the first time I'm on any Linux distro.


-Lasse Nielsen

EDIT: I couldn't find the thread, even though I tried multiple queries and tried browsing the Hoary forum.

Care to link it?

---

### Post by yesplease on 2005-12-04
When you are new to linux, I would recommend the 32 bit version too. 

To answer your question, I found this: [http://ubuntuforums.org/showthread.php?t=76882&highlight=codecs](http://ubuntuforums.org/showthread.php?t=76882&highlight=codecs)

Not all drivers are 64 bit yet, so you need a 32 bit environment in 64 bit (search for 32 bit chroot howto). That is what makes it complicated. I saw that there a some recent  solutions where you apparently do not need the chroot. 

I use the 32 bit version, because it is much easier and 64 bit doesnt give increased performance.

---

### Post by mlomker on 2005-12-04
[QUOTE=MenZa]EDIT: I couldn't find the thread, even though I tried multiple queries and tried browsing the Hoary forum.
[/QUOTE]

[Here it is]("http://www.ubuntuforums.org/showthread.php?t=62685").  Didn't have time to look earlier.

---

### Post by vgrisham on 2006-11-15
:???: Bump. I have an AMD64 based desktop, and I'm about to take the plunge from XP to Ubuntu64. Are the concerns you expressed in this post from nearly a year ago still relevant? Has the situation improved? I have a kid and I do a lot of video editing and I've read that a 64-bit environment makes that process a lot less choppy. Is Ubuntu 64 still a bad way to go? If not, does anyone know if the WMA codecs vacuum still exists? Thanks.

> **yesplease said:**
> When you are new to linux, I would recommend the 32 bit version too. 

To answer your question, I found this: [http://ubuntuforums.org/showthread.php?t=76882&highlight=codecs](http://ubuntuforums.org/showthread.php?t=76882&highlight=codecs)

Not all drivers are 64 bit yet, so you need a 32 bit environment in 64 bit (search for 32 bit chroot howto). That is what makes it complicated. I saw that there a some recent  solutions where you apparently do not need the chroot. 

I use the 32 bit version, because it is much easier and 64 bit doesnt give increased performance.

---

### Post by pissedoffdude on 2006-11-15
> **vgrisham said:**
> :???: Bump. I have an AMD64 based desktop, and I'm about to take the plunge from XP to Ubuntu64. Are the concerns you expressed in this post from nearly a year ago still relevant? Has the situation improved? I have a kid and I do a lot of video editing and I've read that a 64-bit environment makes that process a lot less choppy. Is Ubuntu 64 still a bad way to go? If not, does anyone know if the WMA codecs vacuum still exists? Thanks.

You shouldn't have to many problems running the 64 bit version.  I installed Vlc media player through automatix and so far it has been able to play everything that ive throw at it.  The release candidate of mplayer should also be able to play your audio files with ease.  If you get errors saying wrong architecture you can just sudo dpkg -i --force-architecture packagename_i386.deb.  You can also use programs like simple64, automatix, and easyubuntu to get everything you need up and running.  I recommend using a 32 firefox or you can use swiftfox to get your plugins such as flash and java working properly.

---

### Post by RFScheer on 2006-11-15
I have been using Linux now for almost 3 years and have just recently migrated from 32b to 64b.  Ubuntu for about a year.  

I strongly recommend that you do not start with 64b!!!!!!!

The moderate amount of extra performance will come at the cost of many many hours of your time as you learn how to fit many of the still-32b apps into the 64b environment.  This is not a good idea.

32b Ubuntu is great!!!  Use Automatix to configure everything that would take you a lot of personal time to learn about and you won't regret it.  Make sure you establish a separate partition for your /home directory on your first install.  That way you can install new OS again later on the first partition and not have to replace all your documents, songs, etc which are all on the second partition.  It's recommended to allow 5GB for the OS partition but I'd recommend 10G so you have lots of room for apps.

Hope it helps.

---

### Post by RFScheer on 2006-11-16
Well, hmmm, ahhh, I'm revising my recommendation.  Based on pissedoffdude's post, I decided to try a new install but this time use Automatix2 to take care of installing all the 32b stuff in the 64b environment.  

At this point, I have to agree with him.  Basically everything works.  You may have some learning curve just to figure out what some programs are for and what to avoid and how to do partitioning and so forth but that's all relatively straightforward.  

Thanks pissedoffdude.

---

### Post by artik on 2006-11-16
The official Edgy VLC supports WMV3 without problems 
The unofficial mplayer build also supports WMV3 from [http://ubuntu.moshen.de](http://ubuntu.moshen.de)

About performance - go on 64, there are 50% performance improvement in average.

---

### Post by xstaticxgpx on 2006-11-16
download mplayer 1.0rc1 and install the win32codecs from the mplayer site into /usr/lib/win32 and you should have full compatibility

---

### Post by vgrisham on 2006-11-16
> **artik said:**
> The official Edgy VLC supports WMV3 without problems 
The unofficial mplayer build also supports WMV3 from [http://ubuntu.moshen.de](http://ubuntu.moshen.de)

About performance - go on 64, there are 50% performance improvement in average.

Thanks for the reply (and to RFScheer and pissedoffdude). Here are a couple of noob questions:

1. What is VLC? 
2. Is WMV3 a video format? 
3. Do you know if there is a decent player for 64 that is able to handle WMA music files and to work with MP3 players?
4. Is it true that Wine does not run in 64? 
5. Is there a 64-bit compatible version of firefox? Does it come preloaded?
6. Is firestarter available for 64 bit? I must share my internet connection with my wife's XP laptop.

I appreciate your help. I'm very excited to be dumping windows, but I'm a little worried about what I'm getting into with the 64-bit version of Ubuntu. I've installed 32 bit on an old laptop to try things out, and I like it a lot; so far, every hurdle I faced has been fairly easy to overcome (with the help of this forum and the wiki). How much more difficult will it be for a noob to get rolling in 64?

Thanks Again,
Vaughn

---

### Post by xstaticxgpx on 2006-11-16
> **vgrisham said:**
> Thanks for the reply (and to RFScheer and pissedoffdude). Here are a couple of noob questions:

1. What is VLC? 
2. Is WMV3 a video format? 
3. Do you know if there is a decent player for 64 that is able to handle WMA music files and to work with MP3 players?
4. Is it true that Wine does not run in 64? 
5. Is there a 64-bit compatible version of firefox? Does it come preloaded?
6. Is firestarter available for 64 bit? I must share my internet connection with my wife's XP laptop.

I appreciate your help. I'm very excited to be dumping windows, but I'm a little worried about what I'm getting into with the 64-bit version of Ubuntu. I've installed 32 bit on an old laptop to try things out, and I like it a lot; so far, every hurdle I faced has been fairly easy to overcome (with the help of this forum and the wiki). How much more difficult will it be for a noob to get rolling in 64?

Thanks Again,
Vaughn

1. A Media Player
2. WMV3 is basically Windows Media Player 9 video files
3. Banshee or Amarok work with .wma don't they?
4. Wine does run in 64, I just recently compiled it on my 64bit edgy - theres a post with a 64bit .deb file [URL="http://ubuntuforums.org/showthread.php?t=297280"]here
[/URL]
5. The preloaded version of firefox is 64bit, but the 64bit version of firefox doesn't have compatibility with java or flash. Use [this]("http://www.ubuntuforums.org/showthread.php?p=1174435") thread to solve that, I don't personally recommend that method, but it's the easiest for new users.
6. firestarter 64bit is in the repos.

---

### Post by vgrisham on 2006-11-16
Thanks again!

> **xstaticxgpx said:**
> 1. A Media Player
2. WMV3 is basically Windows Media Player 9 video files
3. Banshee or Amarok work with .wma don't they?
4. Wine does run in 64, I just recently compiled it on my 64bit edgy - theres a post with a 64bit .deb file [URL="http://ubuntuforums.org/showthread.php?t=297280"]here
[/URL]
5. The preloaded version of firefox is 64bit, but the 64bit version of firefox doesn't have compatibility with java or flash. Use [this]("http://www.ubuntuforums.org/showthread.php?p=1174435") thread to solve that, I don't personally recommend that method, but it's the easiest for new users.
6. firestarter 64bit is in the repos.

---

### Post by RAOF on 2006-11-16
> **artik said:**
> The official Edgy VLC supports WMV3 without problems 
The unofficial mplayer build also supports WMV3 from [http://ubuntu.moshen.de](http://ubuntu.moshen.de)

About performance - go on 64, there are 50% performance improvement in average.

You also might want to check out the US mirror: [http://ubuntu.systemadministrator.org](http://ubuntu.systemadministrator.org).

Also, do you have benchmarks to back up the 50% figure?  The last set I saw suggested about 30% on average on audio/video encoding/decoding, and that was about average for other loads.

---

### Post by artik on 2006-11-17
> **RAOF said:**
> 
Also, do you have benchmarks to back up the 50% figure?  The last set I saw suggested about 30% on average on audio/video encoding/decoding, and that was about average for other loads.

The benchmarks I've did once:
[http://www.geocities.com/artyomtnk/bench-amd-64-32.pdf](http://www.geocities.com/artyomtnk/bench-amd-64-32.pdf)

In video encoding I've got less then 50% gain but in image processing and math I've got up to 100% gain. So it depends on your tasks (and I think SW also)

---

