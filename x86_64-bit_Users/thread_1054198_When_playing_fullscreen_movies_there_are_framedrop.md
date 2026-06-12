---
title: "When playing fullscreen movies there are framedrops (Nvidia)"
date: 2009-01-29
forum: x86 64-bit Users
---

### Post by marcelkoopman on 2009-01-29
I've noticed that when i'm going fullscreen on a youtube or local movie I get framedrops / performance issues. 

I am using the latest NVIDIA-Linux-x86_64-180.25-pkg2.run driver. Kernel is custom 2.6.28.2

Anyone experience the same on AMD64 ubuntu?

---

### Post by Noo on 2009-01-30
I used to have severe visual tearing while playing video in Ubuntu 8.10 but I fixed that by enabling Sync to VBlank in CompizConfig (enabling VSync in the nvidia drivers seemed to have no effect).

I really think VSync should be enabled by default in ubuntu because watching videos was nearly impossible without it on my PC.

The reason I put this here is because visual tearing in video looks a bit like frame dropping and some people might confuse those.

---

### Post by marcelkoopman on 2009-01-30
> **Noo said:**
> I used to have severe visual tearing while playing video in Ubuntu 8.10 but I fixed that by enabling Sync to VBlank in CompizConfig (enabling VSync in the nvidia drivers seemed to have no effect).

I really think VSync should be enabled by default in ubuntu because watching videos was nearly impossible without it on my PC.

The reason I put this here is because visual tearing in video looks a bit like frame dropping and some people might confuse those.
I dont think its a compiz issue. Even though there might be one. 
I'm referring to a normal X setup with the nvidia driver. Whenever I go fullscreen I get framedrops. It's so slow I can hardly view it.
Do I need to put some options in Xorg.conf?

---

### Post by marcelkoopman on 2009-02-02
I'm suspecting that the codecs for playing videos might be using software decompression instead of hardware decompression. Is this something that could be the problem? Should i check my codecs?

---

### Post by shadowhacker on 2009-02-02
> I'm referring to a normal X setup with the nvidia driver. Whenever I go fullscreen I get framedrops. It's so slow I can hardly view it.

I have the exact same problem.

> I'm suspecting that the codecs for playing videos might be using software decompression instead of hardware decompression. Is this something that could be the problem? Should i check my codecs?

I'm leaning towards codecs as well. I use many free TV streaming sites, and half of the streams just stay black after loading, despite the fact that the sites' plugin checkers say I have all required plugins. I have installed every codec for 8.10 x64 I could find, to no avail. I've also installed the restricted extras, libdvdcss?, and everything else I could find in various media guides.

---

### Post by norwoods on 2009-02-03
nvidia has designed the VDPAU (Video Decode and Presentation API for Unix) to enable GPU hardware support for video codecs on newer nvidia chips. 
[http://en.wikipedia.org/wiki/VDPAU](http://en.wikipedia.org/wiki/VDPAU)
[http://http.download.nvidia.com/XFree86/vdpau/doxygen/html/index.html](http://http.download.nvidia.com/XFree86/vdpau/doxygen/html/index.html)
when this works its way into codecs things will improve for users of newer nvidia chips.

---

### Post by ethoxyethaan on 2009-02-04
My experience with Gstreamer xine and totem is not that great, i recommend Smplayer, it plays everything allot better,

VLC is my second choice.

---

### Post by shadowhacker on 2009-02-05
> **norwoods said:**
> nvidia has designed the VDPAU (Video Decode and Presentation API for Unix) to enable GPU hardware support for video codecs on newer nvidia chips. 
[http://en.wikipedia.org/wiki/VDPAU](http://en.wikipedia.org/wiki/VDPAU)
[http://http.download.nvidia.com/XFree86/vdpau/doxygen/html/index.html](http://http.download.nvidia.com/XFree86/vdpau/doxygen/html/index.html)
when this works its way into codecs things will improve for users of newer nvidia chips.

Thanks for that. It took some doing, but I finally got 180.22 installed with the new VDPAU feature. It really makes a noticeable difference. Not only does Ibex fly now (even more than before), but full screen videos are way smoother.

---

