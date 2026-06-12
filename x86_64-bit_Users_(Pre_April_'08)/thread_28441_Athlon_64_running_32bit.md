---
title: "Athlon 64 running 32bit?"
date: 2005-04-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by janesy on 2005-04-20
Im running in to a few problems with ubuntu 64bit. such as cedega and some others.

Question is, can i install the 32bit version from scatch on a 64bit system.

will there be any problems? will it run slow?

thanks

---

### Post by endy on 2005-04-20
I had a few compatability problems too so I switched to the 32bit ubuntu, you will have no problems with an AMD64 running in 32bit mode. The games I play like Enemy Territory is really cpu intensive and it runs great. Doom3 also runs great but still puts my system to the test ;)

So far the best distro I've used for full 64bit support is gentoo, but even on gentoo there are lots of apps that don't work in 64bit mode, so if you want 100% linux compatabilty and dont mind a decrease in power (trust me AMD64 in 32bit mode are still very fast) then go for it :)

---

### Post by mthaddon on 2005-04-20
I'd just like to mention that it is possible to do both: run a 64 it system and also run a 32 bit chroot so that you can run any 32 bit apps. I'm using it to run Mozilla with Realplayer and Macromedia Flash plugins, as well as Quake3.

Check out crad's excellent thread for more info:

[http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

I think it's worth staying with 64 bit if you can, as the more people that are using it, the better support for it there will be. 

Cheers, Tom

---

### Post by wmcbrine on 2005-04-20
[QUOTE=janesy]will there be any problems?[/quote]
No.

[quote=janesy]will it run slow?[/QUOTE]
Slower than the 64-bit version, but not slow per se. 32-bit code is also considered "native" on the AMD64. It's possible to completely ignore the 64-bit side of it, and just treat it as a (very fast) x86 / ia32 / whatever you wanna call it. Most people with Athlon 64's -- Windows users -- are doing just that, for now.

Otherwise, I agree with Tom. Run 64-bit and set up a chroot.

---

### Post by endy on 2005-04-20
I agree, the reason why I shied away from it right now was other people who use this PC will have no idea what I'm talking about if I say 'chroot' and there were some mp3 or ipod apps missing from the amd64 release, I forget whic. However ubuntu amd64 was lightning fast and considering gnome isn't exactly known for being streamlined right now that's great!

---

### Post by wmcbrine on 2005-04-22
[QUOTE=endy]there were some mp3 or ipod apps missing from the amd64 release, I forget whic.[/QUOTE]
I think the mp3 apps are omitted from all versions of Ubuntu by default, due to patent issues -- you have to enable the universe and/or multiverse repositories to get them. But once that's done, there are AMD64 versions available.

I'm not denying that there might be an unported app in those categories, but if there is, I haven't noticed; I've got full functionality with AMD64 code. For mp3, there's xmms, mpg321, vlc, grip, lame, etc.; for the iPod, I installed gtkpod, and could also have installed gnupod-tools if I wanted to.

---

