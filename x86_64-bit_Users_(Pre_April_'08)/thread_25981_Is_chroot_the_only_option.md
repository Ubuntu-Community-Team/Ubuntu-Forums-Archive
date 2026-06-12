---
title: "Is chroot the only option?"
date: 2005-04-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by raid517 on 2005-04-11
Hi, I am curious, I thought that X86/64 bit code execution was supposed to be transparrent in Linux - just Like it is in Windows 64Bit? I read the sticky section about creating a chroot environment in order tro run 32Bit apps - but this seems a bit like cheating to me - in that you have to install a full base 32Bit environment to get 32bit apps to run. (This feels more like emulation than real and transparrent 32/64bit code execution. Isn't there any way to run and install 32Bit apps (albeit the limited few that I need) just as easily in 64Bit Linux as I could in 32Bit Linux (or indeed as I can in 64Bit MS Windows) without the need for a chroot environment?

GJ

---

### Post by wmcbrine on 2005-04-11
You don't *have* to set up a chroot. Most 32-bit apps will run with the provided libraries in */lib32. The biggest advantage of chroot is the way it allows you to conveniently add i386 packages -- you can't do that with the 64-bit tools. (You can install packages with 32-bit binaries, but they still have to be repackaged for the AMD64 system. Ubunutu's OpenOffice packages are an example.)

I believe the RPM-based AMD64 distros are set up in such a way that you can add 32-bit packages as easily as 64-bit. Debian (and therefore Ubuntu) chose to go a different way, for complex reasons. For the future, they're planning to adopt a "multiarch" system that will allow mixing 32-bit and 64-bit packages, but that's not here yet.

Anyway, a chroot is really not that hard to set up; and no, it's not "emulation", either.

---

### Post by raid517 on 2005-04-11
Oh well I guess I will have to look into chroot then. One thing I'm curious of though... I use Kaffeine to watch my digital TV and this uses certain codecs - which I think possibly (although I can't confirm this) only exist in 32bit form.

However in order to watch TV Kaffeine has to use drivers supplied by the kernel. So the question is, is it somehow possible to run a 32bit version of Kaffeine with 32 bit drivers in a 64 Bit environment? Or can I somehow use a 32Bit version of Kaffeine that will be able to use my 64 bit digital TV drivers? Or am I just not going to be able to watch digital TV at all?

Right now I have virtually zero multi media support as all my apps crash when I try to play any kind of multi media file - which all in all seems like a bit of a pain really. I mean why supply kaffeine, or any other multi media software for that matter?

GJ

---

### Post by wmcbrine on 2005-04-13
32-bit apps can call 64-bit kernel functions, no problem. Drivers are part of the kernel (even if they're modules).

You might want to elaborate on your multimedia problems. I have no trouble here, but I did have to make some changes to get everything working optimally.

---

### Post by Gianni Exile on 2005-04-13
[QUOTE=wmcbrine]32-bit apps can call 64-bit kernel functions, no problem. Drivers are part of the kernel (even if they're modules).

You might want to elaborate on your multimedia problems. I have no trouble here, but I did have to make some changes to get everything working optimally.[/QUOTE]
What kind of changes were required?

---

### Post by wmcbrine on 2005-04-13
Enabling DMA, disabling ESD, that sort of thing. I've posted about it elsewhere... sorry, I don't want to retype it all (check my post history if you like). But if you have a specific problem, I may be able to give you a specific answer.

---

### Post by sjansen on 2005-04-29
[QUOTE=raid517]So the question is, is it somehow possible to run a 32bit version of Kaffeine with 32 bit drivers in a 64 Bit environment?[/QUOTE]
You can run 32 bit apps on a 64 bit kernel, provided you have all the needed 32 bit  libraries. You can not load 32 bit modules into a 64 bit kernel. If by "driver" you meant plugin, the answer is yes. If you meant kernel module, the answer is no.

---

### Post by floogy on 2005-05-09
[QUOTE=wmcbrine]32-bit apps can call 64-bit kernel functions, no problem. Drivers are part of the kernel (even if they're modules).

You might want to elaborate on your multimedia problems. I have no trouble here, but I did have to make some changes to get everything working optimally.[/QUOTE]

Hello,

Does that mean, that I can install the w32codecs and firefox flashplugin on amd64 without building a chroot. In other words: Does the  32bit flashplayer plugin work for firefox-amd64? And can I expect, that the win32codecs from marillat are working in my mplayer-amd64?

And if so, is there a Howto on this topic too?

The other question: if it's not possible can I then use at least my mplayer-amd64 with the win32codecs installed in the chroot environement? Sorry, I'm a bit confused about these things.

Thank you in advance

regards

Gerhard

---

