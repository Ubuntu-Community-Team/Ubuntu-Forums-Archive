---
title: "nvidia driver nightmare"
date: 2007-06-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by darknightuk on 2007-06-08
ok i give up been tryin all day to install the nvidia drivers on my new systen i've tried the nvidia-glx-new as usual doesnt work i've tried the envy script and a manual install both give api mismatch errors, i've looked round the forums n am getting nowhere, what should i be doing?
i've got a nvidia 8600gt

---

### Post by soapytheclown on 2007-06-08
go to the nvidia website and download the linux driver there i believe support for the 8000 serise has just been added in the past day or 2

---

### Post by darknightuk on 2007-06-09
fixed it followed the ubuntu/debian part of the post below to the letter and works with the latest driver
 [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

---

### Post by darknightuk on 2007-06-09
ok maybe a i spoke a little too soon but i'm a step nearer, driver works ok till i reboot then xserver fails with api mismatch error however if i reinstall the driver again works fine till i reboot, any ideas??

---

### Post by Cappy on 2007-06-09
nvidia-glx-new won't work because it only contains 9755 while your video card is only supported by the newest NVIDIA drivers. It seems it just came out of beta or alpha on the 8th! Anyway, here is the link:
[http://www.nvnews.net/vbulletin/showthread.php?t=92953](http://www.nvnews.net/vbulletin/showthread.php?t=92953)

You can also use the UNSTABLE (ONLY THE UNSTABLE!) Envy application:
[http://ubuntuforums.org/showthread.php?t=432056](http://ubuntuforums.org/showthread.php?t=432056)

The website is here:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

And here is the FAQ:
[http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)

I recommend posting any problems to the Envy thread since everyone seems to get help on it.

---

### Post by kuja on 2007-06-09
I recommend envy also, especially seeing as it'll fix that problem (I've never run into the api mismatch error problem after running envy, or when using the nvidia-glx ubuntu packages)

---

### Post by darknightuk on 2007-06-09
fixed it just hadn't purged all of the restricted driver, tried envy early on and it didn't work, i try to avoid stuff like this and automatix causes to many problems imo, besides that fact that envy doesnt use that latest driver and it does nothing other than automate what other how to's do and while it  mite make things a little easier if u cant command line stuff it can **** things up big time and make it harder to track problems

---

### Post by fakie_flip on 2007-06-09
> **darknightuk said:**
> fixed it just hadn't purged all of the restricted driver, tried envy early on and it didn't work, i try to avoid stuff like this and automatix causes to many problems imo, besides that fact that envy doesnt use that latest driver and it does nothing other than automate what other how to's do and while it  mite make things a little easier if u cant command line stuff it can **** things up big time and make it harder to track problems

I'm trying to follow those how tos and get the driver from nvidia.com, but I am running into a problem doing that. If I try to remove ubuntu's nvidia package, apt wants to remove the linux kernel also.

[http://ubuntuforums.org/showthread.php?t=469066](http://ubuntuforums.org/showthread.php?t=469066)

---

### Post by darknightuk on 2007-06-09
make sure that, that all restricted package have been removed it will not let you remove the kernel

---

### Post by fakie_flip on 2007-06-10
I found out that the linux-generic package is just a metapackage that depends on the newest kernel package in the repos, but without it, I don't know that I will receive new kernels through the updates.

---

### Post by Sockerdrickan on 2007-06-11
The new 100.14.09 supports your card [www.nvidia.com](www.nvidia.com) use my script to install it

---

### Post by Cappy on 2007-06-11
Tux0r, please stop posting unfinished/taunting/spamming comments.

---

