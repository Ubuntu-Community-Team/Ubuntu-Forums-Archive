---
title: "Have you considered switching to 32bit?"
date: 2006-09-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by toykilla on 2006-09-13
I am on the verge of reinstalling Ubuntu because of all the small 64bit annoyances. There is not any one huge problem, but enough smaller ones that I don't really see a reason not to any more. I am sure I dont have to explain further, but wanted to know if you have considered switching (or have already). If so what were your reasons and was the switch beneficial?

---

### Post by tymek666 on 2006-09-13
Well, I've considered once aftert release 5.10. Under Hoary my wifi worked out of the box, but none under 5.10. ith AMD64 i couldn't use ndiswrapped, because i hadn't 64bit winxp drivers. But Dapper works great with my wifi :)

---

### Post by John.Michael.Kane on 2006-09-13
toykilla why not try posting what issues your having with 64bit ubuntu before changing? maybe they can be sorted out.

**Note:** Your only changing architectures. For the most part the same issues one would have with 64bit could be seen under 32bit aswell.

---

### Post by kuja on 2006-09-13
My reply to the post title: No.
My reasoning: Any 64-bit specific issues I have can be worked around in less than five minutes from a fresh setup.

---

### Post by hajk on 2006-09-13
I have installed both 32-bit and 64-bit Dapper, am using only the 64-bit version, and am planning to install 64-bit Edgy in place of 32-bit Dapper. I have found enough ogg radio streams (that work fine in 64-bit) to suit my taste.
I can see where there would be a problem for people wanting to play a lot of Real video streams (and other exclusively 32-bit codec stuff), but there are various solutions. My own solution to those issues is a cop-out of sorts: I watch that stuff on my MacBook laptop. ;)

---

### Post by Kilz on 2006-09-13
> **toykilla said:**
> I am on the verge of reinstalling Ubuntu because of all the small 64bit annoyances. There is not any one huge problem, but enough smaller ones that I don't really see a reason not to any more. I am sure I dont have to explain further, but wanted to know if you have considered switching (or have already). If so what were your reasons and was the switch beneficial?

To tell the truth I did try to install 32bit by accident when I had a graphics card upgrade problem a few months ago. I picked up the wrong cd by mistake. I have 2 32bit machines on my home network so I have both versions. But it didnt see my cdrom drive once installed. It was slow and not as responcive as 64bit, so I wiped it and put 64bit in.

---

### Post by toykilla on 2006-09-13
> **SD-Plissken said:**
> toykilla why not try posting what issues your having with 64bit ubuntu before changing? maybe they can be sorted out.

**Note:** Your only changing architectures. For the most part the same issues one would have with 64bit could be seen under 32bit aswell.

a) having to install 32bit firefox to use flash
b) sound not always working. When I play mp3s, sound in flash disappears. I have to always use "killall esd" before launching Firefox. 
c) unsuccessful at getting XGL/Compiz installed. Seems it is harder on the 64bit platform. I have followed several tutorials and they always end up not working in some manner. 

Those are the first three off the top of my head. I am sure there are others as I go back through the past month or two using Ubuntu.

---

### Post by Kilz on 2006-09-13
> **toykilla said:**
> a) having to install 32bit firefox to use flash
If you install 32bit Ubuntu you will be using 32bit firefox anyway.
> **toykilla said:**
> b) sound not always working. When I play mp3s, sound in flash disappears. I have to always use "killall esd" before launching Firefox.  Thats something to do with your hardware. It may continue to happen on 32bit. You could add this to the firefox startup script, open a terminal and type in ```
sudo gedit /usr/local/bin/firefox32
```
add killall esd above ```
linux32 /usr/local/firefox32/firefox $@
``` and save.
> **toykilla said:**
> c) unsuccessful at getting XGL/Compiz installed. Seems it is harder on the 64bit platform. I have followed several tutorials and they always end up not working in some manner. 

Those are the first three off the top of my head. I am sure there are others as I go back through the past month or two using Ubuntu.Xgl/compiz is experimental still. It gives fits to everyone regardless of version. Upgrade mess it up all the time for both versions.
The grass isn't always greener on the other side. Sometimes its from the same seed.

---

### Post by Pinoy915 on 2006-09-13
I've tried both and I prefer the 64bit. With these tutorials around, I have no problems getting things up and running. For viewing most flash videos and running shockwave, I just install the Firefox Windows version with wine.

---

### Post by kuja on 2006-09-13
Hey Kilz, I don't know Firefox as well as I used to, and when I did use it I didn't play with the startup script, but couldn't it also be possible to run Firefox through an esd wrapper of some sort? I know I have to do something similar with opera to get the sound to play nice with flash. Something along the lines of "artsdsp opera" in the script is what I use and it seems to magically fix things.

---

### Post by Kilz on 2006-09-13
> **kuja said:**
> Hey Kilz, I don't know Firefox as well as I used to, and when I did use it I didn't play with the startup script, but couldn't it also be possible to run Firefox through an esd wrapper of some sort? I know I have to do something similar with opera to get the sound to play nice with flash. Something along the lines of "artsdsp opera" in the script is what I use and it seems to magically fix things.

To be honest I dont know firefox all that well myself. I just noticed it was a big problem when I started using Ubuntu and tried to fix it. I have just banged my head into a wall enough times to get it to work. ](*,) Thanks for the suggestion, Ill try it.

---

### Post by toykilla on 2006-09-14
One more annoyance. My computer goes into sleep or hibernate even though I have those turned off (or set to "never"). It will not wake up. I have to cut the power and turn it back on. Pressing the reset button just turns all of the fans on full blast and it does not restart.

---

