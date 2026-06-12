---
title: "real player issue"
date: 2006-04-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by dpw2atox on 2006-04-11
This doesnt happen on the 32bit ubuntu, only on the 64bit version. When I try and watch any real video file on real player, the audio is fine but the video skips. It stays on one still image of the video for a few sec then goes very fast and catches up and then hangs again and basically keeps doing this. It launches fine with no errors but I cant figure out how to fix this. I dont have any problems with any other media players. Any advice?

---

### Post by hajk on 2006-04-11
It also happens on my 32-bit k7-smp system, it may be smp-related.

---

### Post by flapane on 2006-12-06
> **dpw2atox said:**
> This doesnt happen on the 32bit ubuntu, only on the 64bit version. When I try and watch any real video file on real player, the audio is fine but the video skips. It stays on one still image of the video for a few sec then goes very fast and catches up and then hangs again and basically keeps doing this. It launches fine with no errors but I cant figure out how to fix this. I dont have any problems with any other media players. Any advice?

also here, audio is ok but a lot of frames skips
bump

---

### Post by napsilan on 2006-12-06
Happens here on edgy x64.  I just chalked it up to realplayer's overall crappiness.

---

### Post by milad on 2006-12-07
I'm having the same problem on Edgy 32-Bit ..

is there any alternative to Real Player in linux? Something like Real Alternative in Windows

---

### Post by Sukarn on 2006-12-07
I used to get this in the 32 bit Edgy, but not getting it any more in 64 bit.

@milad: yes, there are some codecs that can play real video/audio, though I don't remember which ones. Maybe it was the w32codecs packs, but I'm not sure.

---

### Post by flapane on 2006-12-07
i wanna see my simpson and family guy vidseos, unfortunately it seems I can't:(

---

### Post by flapane on 2006-12-08
bump

---

### Post by kleeman on 2006-12-08
Go to the helix forum and harass errr ask the developers:


[https://helixcommunity.org/forum/forum.php?forum_id=7](https://helixcommunity.org/forum/forum.php?forum_id=7)

---

### Post by flapane on 2006-12-08
I already searched on that forum it seems other ppl posted the problem but they never gave any answer there....

---

### Post by WamBamBoozle on 2006-12-14
I have this problem as well. The sound is working but the video is jerky. "top" indicates realplayer is using 17% of the cpu. I'm running Edgy on amd64

uname -a
Linux zzz 2.6.17-10-generic #2 SMP Fri Oct 13 15:34:39 UTC 2006 x86_64 GNU/Linux

realplayer version 10.0.8.805

---

### Post by flapane on 2006-12-14
what to do?

---

### Post by xnij on 2006-12-14
What about mplayer with the win32codecs? Real seem to be supported [http://www.mplayerhq.hu/DOCS/codecs-status.html](http://www.mplayerhq.hu/DOCS/codecs-status.html)

Mind you I haven't tried this on Ubuntu amd64 myself so I might be wrong (I've got it working in Gentoo tho)

---

### Post by janfsd on 2006-12-14
> **xnij said:**
> What about mplayer with the win32codecs? Real seem to be supported [http://www.mplayerhq.hu/DOCS/codecs-status.html](http://www.mplayerhq.hu/DOCS/codecs-status.html)

Mind you I haven't tried this on Ubuntu amd64 myself so I might be wrong (I've got it working in Gentoo tho)

Mplayer seems to handle .rm files without problem, but it doesn't handle .rmvb , at least on AMD64.
I am getting the same problem with RealPlayer when viewing .rmvb files.

---

### Post by Cynical on 2006-12-14
[quote=milad]is there any alternative to Real Player in linux? Something like Real Alternative in Windows[/quote]

The w32codecs package includes support for the real media and quicktime formats. So any video player that can take advantage of that should be able to. I've never tried to play an .rmvb file with it installed so I cant really say there. (besides, realplayer works fine on this system)

---

### Post by igsimon on 2006-12-15
the fix listed in attached link worked for me  - good luck:p 


[http://blogorrhoea.wordpress.com/2006/03/01/linux-realplayer-choppy-video-fix-how-to/](http://blogorrhoea.wordpress.com/2006/03/01/linux-realplayer-choppy-video-fix-how-to/)

---

### Post by janfsd on 2006-12-15
> **igsimon said:**
> the fix listed in attached link worked for me  - good luck:p 


[http://blogorrhoea.wordpress.com/2006/03/01/linux-realplayer-choppy-video-fix-how-to/](http://blogorrhoea.wordpress.com/2006/03/01/linux-realplayer-choppy-video-fix-how-to/)

Thanks a lot for that, now i can watch all that .rmvb files i had without problems! :)

---

### Post by flapane on 2006-12-15
here it says
flapane@a64:~$ aoss realplay
Warning: LD_PRELOAD="/usr/$LIB/libaoss.so"
ERROR: ld.so: object '/usr/$LIB/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.

and the video is still choppy :(

---

### Post by flapane on 2006-12-15
It worked by installing alsa-oss_1.0.11-1_i386.deb libraries in lib32 and extracting aoss and renaming it aoss32 !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! 
LOOK HERE
[[IMG]http://img226.imageshack.us/img226/6090/realxt1.th.jpg[/IMG]](http://img226.imageshack.us/img226/6090/realxt1.jpg)
and here [http://www.youtube.com/watch?v=XhrllVYZOwM](http://www.youtube.com/watch?v=XhrllVYZOwM)

igsimon, god bless you

---

### Post by janfsd on 2006-12-15
> **flapane said:**
> It worked by installing alsa-oss_1.0.11-1_i386.deb libraries in lib32 and extracting aoss and renaming it aoss32 !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! 
LOOK HERE
[[IMG]http://img226.imageshack.us/img226/6090/realxt1.th.jpg[/IMG]](http://img226.imageshack.us/img226/6090/realxt1.jpg)
and here [http://www.youtube.com/watch?v=XhrllVYZOwM](http://www.youtube.com/watch?v=XhrllVYZOwM)

igsimon, god bless you

For 64bit users there is no need for extracting the aoss version of the 32bit packet, you just only need to extract the libraries to lib32 and sudo ldconfig shoud make it work with the original aoss

---

### Post by flapane on 2006-12-15
I wanted to avoid ldconfig because sometimes it mess up the libraries

---

### Post by janfsd on 2006-12-15
I didn't know ldconfig can mess the libraries, I've always used it, and no problems till now. But, whenever a new packet is installed,which includes new libraries, doesn't ldconfig automatically run?

---

### Post by flapane on 2006-12-16
yes I mean if dealing with 32bit libraries on a 64bit system

---

