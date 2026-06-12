---
title: "WoW + Wine 1.1.7 + Ubuntu 8.10 = FPS problems"
date: 2008-11-05
forum: Wine
---

### Post by Neecapp on 2008-11-05
Alright, so I have been away from the Linux community for quite some time, but after deciding to come back I have decided to install WoW with Wine.

So, first of all it will not work with Directx AT ALL.

I turned on OpenGL in Config.wtf and also 
SET SoundOutputSystem "1"
SET SoundBufferSize "150"

So, it seems to load up WoW and run it fine, but the problem is that I get really low FPS.

I have also tried all of the stuff on [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Including the Reg tweak GL_ARB_vertex_buffer_object

The problem is that in stressful parts of the world I get around 20-30fps and it gets really choppy, where as in Windows Vista, I never go below 80ish.

Any ideas? I can turn up all of the video settings as high as possible or as low as possible and it makes no difference. My system should not have any problems running WoW on Wine.

System specs:
Intel C2d e6700
4gb ram
8800gts 512mb
64-bit Ubuntu 8.10

edit: Also, I am getting over 6kfps in glxgears, so rendering is functioning on some level.

---

### Post by Slocan on 2008-11-06
I'm having the same issue with fps, and found this thread:
[http://ubuntuforums.org/showthread.php?p=6086332](http://ubuntuforums.org/showthread.php?p=6086332)
It looks like downgrading the wine version helps. I haven't tried it yet though.

---

### Post by Neecapp on 2008-11-08
I tried that and it didn't seem to work. I am not really sure what the problem could be.

I have tried quite a bit of stuff too :-\.

---

### Post by huangweiqiu on 2008-12-03
I have same problem too. I played wow with wine on 7.04-8.04 withou no problem,but after upgraded to 8.10,I can't play WOW any more,very very low fps.

---

### Post by dre_in_ham on 2008-12-03
have you tried win 1.1.9?
are you sure you are runnning the latest drivers?

i have a radeon mobility x1600 and on 8.10 im runnning wow 1024x768 perfectly.

---

### Post by OMJD on 2008-12-03
I have this problem too. Apparently it's because the newer Nvidia drivers have a feature called "PowerMizer" which basically underclocks the graphics card, resulting in a peformance drop.

I've followed steps in order to override PowerMizer, but it's still running at "performance level 0".

---

