---
title: "release candidade hangs"
date: 2005-04-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by carlossousa on 2005-04-05
Hi there,

I finished installing the release candidate of hoary (2005-03-30) and a few minutes after logging in, the system simply hangs and only continues with a reset.  It's happened a few more times but always in different places. I never get a hang doing the same thing. Is a flat install without a internet update. My machine is a AMD64 3500+ and a standard bios load on a Asus A8N-SLI, 512mb ram, 120gb IDE disk and one MSI GT6600NX SLI capable.
Any ideas?

Thanks

PS: The AMD64 version boots to a login screen in 30seconds while the i386 flat install takes 1'45s to get to the login screen, on the same machine...

---

### Post by orion_114 on 2005-04-08
Try getting the full release its out now ....
[http://www.ubuntulinux.org/download/](http://www.ubuntulinux.org/download/)

What is your machines temperature doing.
After a reset go into your bios and check out your systems temperature.
Overheating can cause hangs and reboots pretty randomly.

---

### Post by c_dog on 2005-04-09
[QUOTE=carlossousa]Hi there,

I finished installing the release candidate of hoary (2005-03-30) and a few minutes after logging in, the system simply hangs and only continues with a reset.  It's happened a few more times but always in different places. I never get a hang doing the same thing. Is a flat install without a internet update. My machine is a AMD64 3500+ and a standard bios load on a Asus A8N-SLI, 512mb ram, 120gb IDE disk and one MSI GT6600NX SLI capable.
Any ideas?

Thanks

PS: The AMD64 version boots to a login screen in 30seconds while the i386 flat install takes 1'45s to get to the login screen, on the same machine...[/QUOTE]
 Second that on getting the full release. It has, or I should say at least the DVD release has, the Nvidia debs for the new driver version 1.0.7174 and xorg 6.8.2; which takes care of a bunch problems and kicks up the video speed a little. It's been pretty darn stable so far my A8N-SLI w/6600GT. As orion_114 mentioned, the preview release had broken APM and APIC. My laptop was getting hot enough to fry eggs on even though fan would spin like a fiend. Had to force the cpu into max speed to keep things cooled down.

---

### Post by lokojones on 2005-05-31
EXACTLY same problem here.. but I have an ABIT AN8 instead of Asus A8N. Same MSI 6600gt. I have been several years using gentoo on my oldest athlon xp... when I switched to gentoo 64bit, I started having this problem.. after 2 weeks googling, I decided to move to ubuntu AMD64..and I get the same here :( I think I've tried everything.. it MUST be a kernel bug or a NVIDIA bug (heard some older nvidia drivers made some computers crash randomly)

---

