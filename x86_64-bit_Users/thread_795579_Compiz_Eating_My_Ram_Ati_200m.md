---
title: "Compiz Eating My Ram Ati 200m"
date: 2008-05-15
forum: x86 64-bit Users
---

### Post by jbruceca on 2008-05-15
Hey guys,

I just recently installed Hardy 64 on my dv5000. I didn't have any problems wiith the drivers installing fglrx thru ENVYNG with ease. I rebooted, and immediately the card recognized the card and driver thus enabling affects as shown below:

OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7412 Release

Now this is where it get's tricky and I cannot seem to wrap my head around this. When idling with Desktop manager enabled compiz just EATS at my ram (512mb) going at about 8 mb a min or so. When I disable this of course the issue is gone and the ram is returned. Well I did some research and apparently it is a card issue with handling OpenGL. Well I decided to test this..So I ran GLXgears for 10 minutes, the FPS was fine the whole time...Memory didn't move one inch. So my theory of this being leaky GL is now out the window...I'm not TO sure what to do next, Now I am not sure what to do, as my Video runs fine, Glxgears runs fine, Full Screen video playback is fine...Just Compiz is leaking...And It's a shame that I cant enjoy this feature. Any help or ideas will help.On a side note GLXgears does max my cpu, not really slowinganythign down just running it at 100%

---

### Post by inportb on 2008-05-15
If you don't need all of the features of Compiz, you can try a smaller composite manager like xcompmgr. Alternatively, you can use other desktop environments like XFCE and KDE4. My experience with Compiz has generally been pretty terrible. The first time I used it, it was on XGL with ATi x200m, and it was reasonably good.

---

### Post by Kilz on 2008-05-15
> **jbruceca said:**
> Hey guys,

I just recently installed Hardy 64 on my dv5000. I didn't have any problems wiith the drivers installing fglrx thru ENVYNG with ease. I rebooted, and immediately the card recognized the card and driver thus enabling affects as shown below:

OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7412 Release

Now this is where it get's tricky and I cannot seem to wrap my head around this. When idling with Desktop manager enabled compiz just EATS at my ram (512mb) going at about 8 mb a min or so. When I disable this of course the issue is gone and the ram is returned. Well I did some research and apparently it is a card issue with handling OpenGL. Well I decided to test this..So I ran GLXgears for 10 minutes, the FPS was fine the whole time...Memory didn't move one inch. So my theory of this being leaky GL is now out the window...I'm not TO sure what to do next, Now I am not sure what to do, as my Video runs fine, Glxgears runs fine, Full Screen video playback is fine...Just Compiz is leaking...And It's a shame that I cant enjoy this feature. Any help or ideas will help.On a side note GLXgears does max my cpu, not really slowinganythign down just running it at 100%

512m is about the minimum a 64bit systems have installed. Add to this the fact that you are running a 200m radon express. It is no wonder it eats ram up. The 200 express is an not a separate card, it is on your motherboard and uses system ram, it doesn't have any of its own. I used to have a 200 express, in order to run compiz I had to upgrade my graphics. Adding ram wouldn't be a bad idea either.

---

### Post by homerhomer on 2008-05-16
my Compaq laptop is very similar, you should also check the bios and see how much ram you have reserved for the graphics card.

And yes, adding at least another 512megs of ram would help

---

