---
title: "Help With Installing Ubuntu on Ibook G4"
date: 2006-03-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by coreyrandom on 2006-03-13
I'm currently using Mac OS X 10.4.5 on my ibook and I also have another pc which is running on breezy badger. I'm pretty happy with the performance of ubuntu on my pc, so I decided to install ubuntu on my ibook too. But I use Mac OS X for lots of my school stuff and it also has got some applications I usually need so I'm not planning to delete Mac OS X from my computer. So I want something like multiboot session on my notebook, which was like on my pc for a while ago (before the times I got rid of Windows :rolleyes: ). So which steps should I take for installing ubuntu side by side with my current Mac OS X installation? Any advices for creating a new partitions? I'm waiting for your answers. thanks :)

---

### Post by spaceballl on 2006-03-13
Hi there,

well you've come to the right place for help with this kind of thing. I did exactly the same thing you did on my iBook G4 a month or so ago.

So the first thing you need to do is repartition your hard drive, search the forums for "parted." That's the program you use and you'll just shrink your OS X partition a bit. Then you'll boot up the install CD and just let Ubuntu automatically repartiion the free space on your hard drive. It will install 3 partitions and automatically configure yaboot to load up and ask you which OS you want to boot into.

Once you have that set up, you're going to want to get Airport Extreme working (which is definitely beta at this moment, but it does work!). I wrote a quick how-to for that right here:
[http://ubuntuforums.org/showthread.php?p=820495#post820495](http://ubuntuforums.org/showthread.php?p=820495#post820495)

Then search the forums for a program called "mouseemu". It gives you right click functionality.

At this point, you should be ready to go w/ your Ubuntu / OS X dual boot machine. I'd let you know how to get XGL working, but i'm still working on that myself...

-Kevin

I'm pretty new to linux myself, but I enjoy helping out and being helped out by fellow OS X / Ubuntuers out there so let me know if you have any other questions!

---

