---
title: "firefox 3.0.11 youtube fullscreen slow"
date: 2009-07-18
forum: x86 64-bit Users
---

### Post by psycho5 on 2009-07-18
Hi, I guess the title says it all. I never installed flash on my own I would let the OS take care of it, and it works just fine except when I go fullscreen the frame rate drops and the video is choppy and in frames. It even happens for youtube hd videos. If I don't maximise then everything is fine, which is pretty annoying. Comming back from full screen takes a second or two where the video stops playing, youtube window goes grey (not responding or busy I guess) and then the window is restored then the video continues. Any fix for this? 

I do have compiz running and don't think it is a resources problem.

I have AMD Athlon X2 3600+ 
Asus M2A-VM Mobo
Nvidia 8600GTS PCI-E card
2gb Ram 

Anything other data that can help I would be happy to post if there is a workaround.

---

### Post by khelben1979 on 2009-07-18
When you look at YouTube videos in fullscreen it takes much more power as I think you understand, however, there is another way to do this:

Use ```
ctrl alt -
``` to zoom in to a lower screen resolution.

This way you will also save system resources. I can't even look at YouTube in fullscreen on my system although I have flash 10 installed, unfortunately.

---

### Post by stmiller on 2009-07-18
Is this checked:

Right click on the flash element, and choose 'enable hardware acceleration.' 

That check box is for helping full screen flash playback.

---

### Post by khelben1979 on 2009-07-18
For myself, this has always been activated on my system (enable hardware acceleration).

---

### Post by 0pul3nce on 2009-07-18
I had a glitch on one video, otherwise it's been good for me. I really haven't noticed the merits of running a x86 so far...
yet i've not found any cons apart from Skype and flash installations

Is your computer capable of handling the video, i can't think of any 64 bit CPU having problems. Whats the graphic card you've got

---

### Post by khelben1979 on 2009-07-19
Apparantly I can look at YouTube in fullscreen over here with good playback if I use [the Opera web browser]("http://en.wikipedia.org/wiki/Opera_web_browser"). It just crashes with Firefox (version 3.5).

---

### Post by Yellow Pasque on 2009-07-19
I believe Compiz running means no GPU acceleration in Flash: [http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html](http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html)

---

### Post by Thelasko on 2009-07-20
Try installing libflashsupport.  Some people say it makes things worse, but for me it makes things better.

---

### Post by Yellow Pasque on 2009-07-20
> **Thelasko said:**
> Try installing libflashsupport.  Some people say it makes things worse, but for me it makes things better.

Are you using Flash 10 or Flash 9?

---

### Post by Thelasko on 2009-07-21
> **Temüjin said:**
> Are you using Flash 10 or Flash 9?

Flash 10 64-bit Alpha.  I noticed that Flash 10 didn't utilize Pulseaudio without it.  Once I installed it, Flash 10 worked with Pulseaudio and I noticed an improvement in performance.

---

### Post by m4lte on 2009-07-21
I've  got the same problem.

I'm runing Firefox 3.0.11, Flash 10.0.22

I'm running ubuntu 9.04 on an 1.8 GHz core 2 duo (T5670) with 1GB RAM and Intel GMA X 4500.

Installing flashplugin-nonfree-extrasounds in the package manager did not help.

Any suggestions??

---

### Post by HeWhoE on 2009-07-24
I just noticed that playing video through the flash player suddenly became slow after recent Firefox updates.


Ubuntu 8.04

Firefox 3.0.12

Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by HeWhoE on 2009-07-24
Just kidding.  I just installed Firefox 2 to see if it really is a change in the browser that made the video slow.  It wasn't.  Flash video in Firefox 2 exhibits the same behavior.

---

### Post by AmyRose on 2009-08-17
Same problem here. I have an "Intel(R) Pentium(R) Dual  CPU  T2390  @ 1.86GHz" and "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)" for my graphics chip. Full screen used to work perfectly a few Flash releases ago, but now it's pathetic on here.

It works fine on my nVidia-based desktop system with the same versions of all software involved.

---

### Post by sammyboy0707 on 2009-09-07
> **khelben1979 said:**
> For myself, this has always been activated on my system (enable hardware acceleration).
 
i had the the same proplem as the original problem, but this was cause all flash player software to run slow, simply open the settings on the right-click button whilst watching the video, then uncheck the 'enable hardware acceleration' box and close, open in full screen and worked perfecttly

---

### Post by vishyc88 on 2009-10-14
hi guys,... i too had the same problem. Flash was running too slow on ubuntu 8.10 and above. All i did was go back to hardy heron(8.04) and its all working fine now. My flash is not slow anymore & youtube videos runs in full screen without any problem.
it could be a kernel campatibility issue.:guitar:

---

### Post by Thelasko on 2009-10-15
> **vishyc88 said:**
> hi guys,... i too had the same problem. Flash was running too slow on ubuntu 8.10 and above. All i did was go back to hardy heron(8.04) and its all working fine now. My flash is not slow anymore & youtube videos runs in full screen without any problem.
it could be a kernel campatibility issue.:guitar:

Hardy has a more stable Intel graphics driver.

---

