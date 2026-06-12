---
title: "64bit or 32bit"
date: 2009-05-14
forum: x86 64-bit Users
---

### Post by Narusegawa on 2009-05-14
I'm torn between 64 and 32bit versions of Ubuntu. I have a Q9300 and 4gb of ram (at the moment) so would prefer 64bit.

However I know I'll need to use 32bit applications (for gaming and multimedia) though. can the 64bit install runa 32bit app (if there isn't a 64bit version available)? I know they'd be a performance hit but can it.

---

### Post by MysticGold04 on 2009-05-14
you can get ia32-libs and force 32-bit packages to install and they will... I've done this with Avast antivirus.

[http://ubuntuforums.org/showthread.php?t=1065805&highlight=avast+64+bit](http://ubuntuforums.org/showthread.php?t=1065805&highlight=avast+64+bit)

---

### Post by Narusegawa on 2009-05-14
I use Avast on windows, didn't even know they had a linux version! Didn't even think linux needed AV software really (except on mail servers)

---

### Post by MysticGold04 on 2009-05-14
in general you don't but I keep it just incase I need to interact with Windows files.

---

### Post by WatchingThePain on 2009-05-14
I always use 64 bit and the only thing that I find a problem is getting Youtube or embedded flash video to work. 
Now I just keep 64 bit and use Totem to view the vids.

---

### Post by pixel :-) on 2009-05-14
Actually, 64 Can run, both 64 and 32 programs, the problem is that you have to install the coresponding 32 libs. Getlibs should be able to do the work for you in most cases.

What 32 apps, you need to run, we'll have a look.

---

### Post by Narusegawa on 2009-05-14
I dunno what 32 bit apps are exactly that I'll need to run. However ultimately I want this to replace my Vista 32 install.

So guessing things like MPlayer (I need a ton of codecs to work), Flash, Java and Adobe PDF are essential to me.

So are things like VMWare for my work based images (I securely dial onto sites using virtual PC's for extra security). I also intend to run things like PlayOnLinux and Wine for my gaming.

---

### Post by oldos2er on 2009-05-14
There are 64-bit versions of Mplayer, Flash, and Java. If you install Adobe Acrobat from the repositories, it should automatically enable any 32-bit libraries it needs.

---

### Post by pixel :-) on 2009-05-14
64-bit versions of Mplayer, and with almost all codecs, don't whoty only very obscure codecs aren't suported.

Flash is stll experimental, but you can use 32 bit flash with the wraper, automatic installation. 

Java 64 is a litle bit buggy, but you can install ia32-java.

Adobe Acrobat, i don't remeber what it was, i installed it from the adobe site and it worked.

from what i know wine is also basicly 32 bit configured to work on 64 bit, compatibility is identical

i use virtual box so i can comment on vmware

---

### Post by jespdj on 2009-05-14
> **pixel :-) said:**
> Java 64 is a litle bit buggy, but you can install ia32-java.
No, Java is not buggy on 64-bit Jaunty and there is absolutely no need to install 32-bit Java. In fact, the version of Sun Java 6 included with Jaunty finally has a 64-bit native browser plug-in, so that Sun Java now works just as well as on 32-bit. You just need to install the package **sun-java6-plugin**.

---

### Post by pixel :-) on 2009-05-14
can you run dbgl ? No. I have all three on my system, and only ia32-java works. And this is not exeptional

[http://members.quicknet.nl/blankendaalr/dbgl/](http://members.quicknet.nl/blankendaalr/dbgl/)

Yes it is bugy, but the good news are that you can install 32 java on 64 ubuntu. Its beater then just sitting on 32 ububtu.

---

### Post by Anubis on 2009-05-14
This horse is so DEAD.

I don't have 32bit anything on my machine, and I do 99.9% of stuff those who seem intent on believing 5 year old information, that they still MUST have 32libs. Well have at it. But please stop spreading FUD concerning running 64bit?

---

