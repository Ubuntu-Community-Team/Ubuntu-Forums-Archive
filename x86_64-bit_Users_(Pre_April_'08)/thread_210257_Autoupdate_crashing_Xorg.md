---
title: "Autoupdate crashing Xorg"
date: 2006-07-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Beamerboy on 2006-07-06
OK so Ubuntu AutoUpdate just seriously crashed Xorg.  Nothing in the error file but it wrote a bunch of junk to the video device.

This happened to a friend of mine minutes before it happened to me, and also others have had this problem (based on a discussion in the #ubuntu irc channel).

It has only started happening since the update for xserver-xorg-input-mouse package the other day.

Has anyone investigated this and got a solution?  Has a bug report been filed yet?

Thanks

Beamerboy

---

### Post by VirtuAlex on 2006-07-06
I have the same problem. Posted a [thread]("http://ubuntuforums.org/showthread.php?t=210266&highlight=update") in Desktop support forum. Have someone with 32 bit amd with the same issue, so I guess it is not about 64-s, but guy has the same video card as me. What video card do you have?

---

### Post by Beamerboy on 2006-07-06
I have a pair of nvidia geforce 6600GT PCI-E cards.

---

### Post by VirtuAlex on 2006-07-06
Yeah, it seems to be nvidia driver problem. There is [another thread]("http://ubuntuforums.org/showthread.php?t=210030") about this issue.

---

### Post by Beamerboy on 2006-07-06
[QUOTE=VirtuAlex]Yeah, it seems to be nvidia driver problem. There is [another thread]("http://ubuntuforums.org/showthread.php?t=210030") about this issue.[/QUOTE]

I don't think it is fair to blame the nvidia drivers at this stage.  I have had the nvidia-glx driver installed since I installed Ubuntu and have never had a problem with it crashing xorg until these 3 updates today.

I think we need a lot more information before we start blaming drivers.

For example, it could simply be a case that only nvidia users have experienced -and- reported the problem on the forums.  Nvidia is used much more than any other graphics card with linux, because there are official drivers for nvidia devices.  Simply dismissing it as an nvidia driver issue with such little information is a very poor assessment.

---

