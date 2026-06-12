---
title: "Flash slow when video maximized"
date: 2008-04-26
forum: x86 64-bit Users
---

### Post by fuzzyl0g1c on 2008-04-26
Anyone know what the problem is? I'm on intel core 2 duo and using the 64 bit version of Ubuntu 8.04. I installed the lastest nonfree flash plugin from the repos.

---

### Post by sofamensch on 2008-05-03
i have it too.. no idea yet

---

### Post by Yellow Pasque on 2008-05-03
The problem is that your video card and/or CPU cannot keep up. Fullscreen Flash is fairly resource-intensive even with the recent addition of video hardware acceleration in 9.0r115

---

### Post by bigkahuna on 2008-05-05
I recently purchased a Dell Vostro 1500 with GeForce 8400M GS graphics which I am using as a home entertainment system.  One of the things we are using this for most is to watch "Internet TV" (like Hulu.com, etc.).  I was hoping on using Ubuntu as my primary OS on this machine, but fullscreen Flash video plays much slower than the same video under Windoze XP.  Is there any hope for faster graphics drivers or full screen flash in the near future?

---

### Post by James_mtl on 2008-05-05
I have same problem too, I don't know if it's any better in 32 bits?  I know it not a fix but I use the zoom function of compiz to make the video full screen it give a better result in fact it is almost perfect !

Hope this helps.

---

### Post by enchantedsky on 2008-05-05
As I have stated in my other posts,

1) This is NOT a hardware problem. Adobe has incompetent programmers who made Flash 9 for Linux buggy with sloppy code that slows down *most* computers when videos are maximized --- no matter what your CPU/GPU speed. Video is choppy, and your CPU speed spikes. The Flash 9 code is closed source, so no one can modify Flash 9 code to fix all these problems ------ only Adobe can, and they aren't doing anything about it. Honestly, people who say that there is nothing wrong with their Flash 9 in Ubuntu.....they are a minority, and I can't explain why Flash 9 works for them. (But I do not accept having a "faster computer" as an explanation because I have a fast, modern computer)

2) It does not make a difference if you have 32-bit Ubuntu vs 64-bit Ubuntu. Trust me, the flash issue annoyed me so much I was trying out EVERY edition of Ubuntu (Kubuntu, Xubuntu, etc) in 32-bit/64-bit, and was getting the same Flash issues.

3) This is a problem with Flash 9 for Linux, because many systems I've worked with that dual-booted Ubuntu and Windows XP, Flash 9 in Windows XP works fine with maximized videos, no choppiness whatsoever, smooth video and ultra-low CPU usage. 

4) The great news from a few days ago is that Adobe will be opening up the specification (and eliminating royalty fees to them) which will pave the way for an open-source Flash player that can completely replace the Adobe Flash Player for Linux, and be equally as functional.

---

### Post by sofamensch on 2008-05-08
[http://ubuntuforums.org/showthread.php?t=756239&highlight=flash+fullscreen](http://ubuntuforums.org/showthread.php?t=756239&highlight=flash+fullscreen)

---

### Post by wilsoniya on 2008-06-06
> **enchantedsky said:**
> 
1) This is NOT a hardware problem. Adobe has incompetent programmers who made Flash 9 for Linux buggy with sloppy code that slows down *most* computers when videos are maximized --- no matter what your CPU/GPU speed. Video is choppy, and your CPU speed spikes. The Flash 9 code is closed source, so no one can modify Flash 9 code to fix all these problems ------ only Adobe can, and they aren't doing anything about it. Honestly, people who say that there is nothing wrong with their Flash 9 in Ubuntu.....they are a minority, and I can't explain why Flash 9 works for them. (But I do not accept having a "faster computer" as an explanation because I have a fast, modern computer)

Well said.  Flash on Linux is such a decroded POS that I find myself avoiding Flash-heavy sites.  Under 64bit Linux the situation is exacerbated by a hacky 32 bit workaround.  I regularly have all flash browser instances crap out simultaneously (leaving dreadful gray squares of misery), and/or errant npviewer.bin process(es) eating CPU time.  

I have a Q6600 and a 8800GT so I *highly* doubt the problem lies with my hardware.  No, I agree with enchantedsky 100% about Adobe dropping the ball.  It makes me wish flash would die a nasty death. </rant>

---

### Post by Jouke74 on 2008-06-06
> **wilsoniya said:**
> I have a Q6600 and a 8800GT so I *highly* doubt the problem lies with my hardware.

The problem is that Flash decoding and enlarging it to full screen takes a lot of CPU processing power under Linux. The video card won't have anything to do until the CPU is done with it... Under XP decoding goes a lot better, because decoders are original and the video card plus their much more mature direct X drivers work way better. Now if you use 64 bit there is also still the wrapper coming into play. 

Whether you have a dual core procesor at 2.4 GHz or quadcore processor at 2.4 GHz does not matter at all, because both the wrapper as well as Flash seem to use only one processor thread (read one processor). Only if you have at least two other CPU hungry applications running, then the Quad advantage comes into play, however it won't increase the speed of the single process. Real gain would be obtained from having more GHz at a single core.

---

### Post by fuzzyl0g1c on 2008-06-12
Thanks for all of the informative posts, I should have read this sooner. Haha. :guitar:

---

### Post by philinux on 2008-06-12
If you have compiz enabled. the zoom function works better than full screen. Workaround yes.

---

### Post by | MM | on 2008-06-12
Here's my workarounds:

If you are just watching youtube you should watch flash clips in Totem.

ALso another way is to start the stream with your browser, then navigate in nautilus to your tmp folder.  There the flash file will be cached until the webpage is closed.  Then just watch the file using your favourite media player in full screen bliss (i prefer vlc for its superior picture quality).

Or if you anticipate that you will re-watch the particular stream.  Try download the flash video using a website such as KeepVid.  Then just play it like a regular video file, it'll even thumbnail in nautilus.

Or merge the two above suggestions.  For instance, i devoured the dexter series in a couple of days by watching the episodes online, before they got to my country.  I would start the stream, wait a minute or two for it to 'buffer', then i would watch the file from by /tmp with vlc in fullscreen smoothness.  Then when it was over i copied the cached file in /tmp to My Video for fututre re-watching.

No point complaining for too long.  Where there is a will there is a way.

---

### Post by mayfer on 2008-06-19
funny part is i've seen friends' computers where they have flawless fullscreen flash for youtube, etc. with their shitty intel graphics cards, whereas my 8800gt and x2 5200+ can't keep up with a fullscreen youtube.

i've been using the compiz zoom function, and i'm happy with it, but it annoys my friends when they try to watch a video on my computer.

---

### Post by multisimple on 2008-06-19
> **philinux said:**
> If you have compiz enabled. the zoom function works better than full screen. Workaround yes.

GREAT IDEA!!!! 
works like a charm!!!!

---

### Post by wry on 2009-05-08
This fixed it for me
[http://spoilt.blogsite.org/wordpress/index.php/2008/07/04/flash-player-for-linux](http://spoilt.blogsite.org/wordpress/index.php/2008/07/04/flash-player-for-linux)

---

### Post by Arup on 2009-05-09
> **bigkahuna said:**
> I recently purchased a Dell Vostro 1500 with GeForce 8400M GS graphics which I am using as a home entertainment system.  One of the things we are using this for most is to watch "Internet TV" (like Hulu.com, etc.).  I was hoping on using Ubuntu as my primary OS on this machine, but fullscreen Flash video plays much slower than the same video under Windoze XP.  Is there any hope for faster graphics drivers or full screen flash in the near future?

Are you using the latest nvidia drivers from the nvidia site? I have tested full screen with a Nvidia 8400GS and it runs fine. I use the latest nvidia drivers though on Jaunty x64.

---

### Post by collinp on 2009-05-09
Flash has always been slower on Linux than on Windows, much less maximized :). Even on a Core 2 Duo, it can be slow. Lets hope for better support in the future.

---

### Post by Yellow Pasque on 2009-05-09
[http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html](http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html)

---

### Post by mikeric on 2009-05-09
I used this post from the how to install flash thread and have no fullscreen flash issues that I have noticed so far. My computer has a 9300m video card and dual core t5800. 

 > Originally Posted by lesmcd  View Post
Here is a link to the best discription for getting the alpha AMD64 bit Adobe Flash Player to function in either Ubuntu 8.1 or 9.4.

[http://www.myscienceisbetter.info/20...-on-linux.html](http://www.myscienceisbetter.info/20...-on-linux.html)

I send my most cincere thanks to the author. This fixed my flash player problems in Firefox and Opera.

Les McDermott

---

### Post by Marlboro666 on 2009-05-10
I am using Xubuntu 64bit 9.04 (XFCE 4.6), Mozilla 3.0.10 and Flash 10 Alpha ver. For 64bit. and works almost perfectly, only what bugs me its it performance in full screen but if I change resolution from 1280x800 to 1024x768 then videos are smooth on any site including YouTube. On windows xp youtube vids where smooth in 1280x800, this is due to Adobe Flash Player not the system itself so dont talk BS that on suse or any other distro flash got better performance and if you have better performance on other distro then becouse you are using other video driver or 32bit distro maybe. dont blame ubuntu. So far Ubuntu is the best system ive tried. We must wait till Adobe realese the final version - maybe performance will be better. now flash for Linux is fat pig: [http://www.adobe.com/products/flashplayer/systemreqs/index.html](http://www.adobe.com/products/flashplayer/systemreqs/index.html)

if still doesn't help then try some lower resolutions like 640x480, if thats the case and you want to surf YouTube then use zoom-out function in your browser.

this method is more convenient than going to /tmp directory and launching it from vlc player every time you click vid on youtube.. for longer vids ok but not every 3min. tiring..

---

### Post by turok40 on 2009-07-11
I run Gentoo with no desktop environment, like Gnome, KDE, etc., with pcmanfm for desktop + file manager and cairo-dock for a dock/panel. Compiz-fusion is my window manager. 

I KILL compiz, emerald decorator, cairo-dock and pcmanfm to simply leave a suspended Firefox window running a flash video. It still behaves terribly, especially when I select it to run in fullscreen. I've heard often that it's Compiz and Flash together. It's a bad mix. But my experience is that it has nothing to do with compiz. If anything, it's Nvidia driver, Xorg, Firefox, or Flash. 

I tried in Opera and it ran nice. hmm... Funny enough, it all came together when I came across some Adobe Flash on Linux blog postings about GPU capability detection problems as well as stumbling upon a macromedia.mplug.org post that mentions the /etc/adobe/mms.cfg file.

In this file, I changed it to override detection and just do HW accel:
```
# Lets you override GPU validation checks to force hardware acceleration
# Warning: This may make your player (more) unstable!
#  0 = Check GPU (default), 1 = Skip checks
# More details:
# http://blogs.adobe.com/penguin.swf/2008/08/secrets_of_the_mmscfg_file_1.html
OverrideGPUValidation = 1

```

I have a Intel quad core with an Nvidia 8600GTS, of course I can handle HW acceleration. It worked! It ran smooth-like. It seems the problem was that Flash incorrectly interpreted my hardware and assumed I actually cannot. Perhaps running inside of Firefox causes it to do this.

Hope this solves it for others.

---

### Post by freackout on 2009-07-13
> **fuzzyl0g1c said:**
> Anyone know what the problem is? I'm on intel core 2 duo and using the 64 bit version of Ubuntu 8.04. I installed the lastest nonfree flash plugin from the repos.
try this encouraging link [http://juliensimon.blogspot.com/2008/12/howto-compiling-vlc-with-all-major.html](http://juliensimon.blogspot.com/2008/12/howto-compiling-vlc-with-all-major.html)
i know its not quite flash related but there somewhere.

---

### Post by freackout on 2009-07-13
> **freackout said:**
> try this encouraging link [http://juliensimon.blogspot.com/2008/12/howto-compiling-vlc-with-all-major.html](http://juliensimon.blogspot.com/2008/12/howto-compiling-vlc-with-all-major.html)
i know its not quite flash related but there somewhere.

i only have two programmes flash related on this 64 mint install they are mint-flashplugin-x64 and flashplugin-nonfree but system works a treat.

---

### Post by freackout on 2009-07-13
> **freackout said:**
> i only have two programmes flash related on this 64 mint install they are mint-flashplugin-x64 and flashplugin-nonfree but system works a treat.

i believe youtube site informs of not working, leads you to a source file 64 so try that too.

---

### Post by freackout on 2009-07-13
> **freackout said:**
> i believe youtube site informs of not working, leads you to a source file 64 so try that too.

also check why/what's going on with ./configure make sudo make install. i had to get the source on last system for 64 bit.

---

