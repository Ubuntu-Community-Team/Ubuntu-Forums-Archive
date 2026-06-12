---
title: "Various newbie questions"
date: 2009-05-31
forum: x86 64-bit Users
---

### Post by da404lewzer on 2009-05-31
Hola,

I am a newbie to Linux and have finally made the switch to using Ubuntu as my primary OS. I'm quite pleased with Ubuntu and have been using it for a month now and just upgraded to jaunty. As for my machine I'm running an Athlon 64 3800+ with a giggle of ram and a sata drive. I have additional ntfs drives from my still needed windows install.

I only have a couple issues with my install and figured I might get some assistance.

**My Sound Skips**
The sound skips ever so often, but is quite annoying as DJing seems out of the question. Is there any way to put some priority on the sound?

I use RhythmBox and most of my music comes from my ntfs drives. I know my machine is more than capable of playing music. Windows has no issues with it.

**My Secondary Display Kills my Desktop Effects**
When I installed, I had only one monitor setup. Later, I added a second using the same hardware. I had to do quite a bit of searching to get it working, and honestly cannot remember what I did. Doing so effectively killed my 3D Cube. I do not by any means nead graphical stimulation, but I should be able to, so why not.

How do I check to see what flavor/ver/whatever of compiz i'm running?

Is there an easy (ha) way to restore the original settings of Compiz from when I installed Ubuntu?

I have already done quite a bit of searching on the matter and have tried quite a few of the examples. I'm not sure I'm pro enough to be tweaking the xorg.conf or anything without some guidance. I have tried "uninstalling" compiz and re-installing the packages. Still no bueno.


*sigh* heh. I still love Ubuntu :D


Any help is appreciated.

Thanks,
Charlie

---

### Post by expelledboy on 2009-06-01
> 
**My Sound Skips**
The sound skips ever so often, but is quite annoying as DJing seems out of the question. Is there any way to put some priority on the sound?

I use RhythmBox and most of my music comes from my ntfs drives. I know my machine is more than capable of playing music. Windows has no issues with it.

In rhythmbox go Edit > Preferences > Playback (Tab) and increase the *Network Buffer Size.*

> How do I check to see what flavor/ver/whatever of compiz i'm running?

```
apt-cache show compiz
```

---

