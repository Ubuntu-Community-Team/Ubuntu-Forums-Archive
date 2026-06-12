---
title: "WOW crash."
date: 2012-09-13
forum: Wine
---

### Post by amikot on 2012-09-13
Hi,
Im using  wine 1.5.12, and playing WOW.
Everything works perfect until i upgraded my kubuntu from 12.04 to 12.10.

With new system i get new nvidia driver.
With new driver WOW is really fast 50% faster than before.
Now i can play on Ultra settings, 

But, there is one huge problem. After few minutes, screen freezes and only what i can do is hardware reset (by key on computer case). Its total hang/crash. Not working CTRL+ALT+F1 ... Not working CTRL+ALT+DEL ... 

I noticed that on lower quality settings i could play more time until screen freeze (arount 30min).
On high quality settings i could play maybe 5-10 minutes. 

Im sure there is bug in nvidia drivers or in kernel (maybe leaking memory).

Im writing here because i want to check is there anyone with similar problem ?

---

### Post by opensshd on 2012-09-13
I went back to 12.04 because of video issues...

It sounds like you're overheating. You can check this with:

sudo apt-get install lm-sensors && sudo sensors-detect

That program will offer to add lines to your conf file, go ahead and add those. Then you can check heat sensors with typing:

sensors

I think it may be something to do with automatic overclocking? just a shot in the dark, but I did prefer 12.04 to 12.10 with either nvidia or nouveau drivers.

Could be a leak, wild pointer or something yeah...

---

### Post by amikot on 2012-09-13
Im sure its not overheating, checked this first.

Fan working, radiator clean, new thermal between GPU and Radiator.

Not matter is that only desktop or WOW with high quality, GPU temp is always between 50°C and 55°C.

On nouveau quality and performance are lower than on nvidia, but its realy stable.

---

### Post by opensshd on 2012-09-13
Ok. There is an nvidia Xserver settings program you can check out, if you haven't already.

nvidia-settings

In my settings you can change overclocking modes, sync to Vblank and other modes that may help.

---

### Post by amikot on 2012-09-13
Nothing to change in nvidia-settings

I have no overclocking options here. Only infos about temp, clocks, some options about colors, quality etc.

I think i will wait for update ... maybe something will change.

---

### Post by opensshd on 2012-09-13
What video card?

---

### Post by amikot on 2012-09-14
Its only GeForce 8600GTS,

NVidia settings displays that there is only one performance profile, so i cant change frequencies.

On higher quality more amount of data (better textures, higher view distance) is coming to memory, and if memory controller is broken (memory leaks) higher quality will effect faster crash.
Is that good point of view ?

I really don`t believe that`s hardware issue. 
Becuse :
On 12.04 (kernel 3.2) with Nvidia driver version 285 (or something like that)  there was no problem.
With Nouveau driver there is crash no problem,  except bad performance - but cannot expect better, because its RE.
Problem exists only on Nvidia v304 under kernel 3.5.

---

### Post by opensshd on 2012-09-18
Have you tried with 3.2? I found 3.5 and nvidia graphics using either nv or nvidia drivers a very buggy combination.

Have you tried monitoring memory preceding a crash?

---

### Post by regor210 on 2012-09-19
I was having the same issue. I went in to Nvidia x Server settings and unchecked Sync to Vblank and Allow Flipping. I also unchecked Sync to Vblank in WOW's Video settings. I still get momentary freezes sometimes but WOW dose not lockup.

---

### Post by amikot on 2012-10-15
Nvidia driver 304.48 changes:

> Changes since 304.43:
• Fixed RandR per-CRTC gamma persistence across modeswitches and
  VT-switches.
[B]• Fixed a bug that caused the X server to sometimes hang in response
  to input events.[/B]
• Fixed a reduction in rendering performance for core X11 rendering on
  certain GPUs that occurred in the 290.* series of releases.
• Fixed a bug that prevented PowerMizer from working correctly on some
  boards with GDDR5 memory, such as some GeForce GT 240 SKUs.
• Added support for the following GPUs:
   • GeForce GTX 660
   • GeForce GTX 650
• Fixed a bug that caused OpenGL applications to not animate properly
  when a rotation or a transformation was applied on some older X
  server versions.
• Enabled FXAA with Unified Back Buffers.
• Fixed a bug that prevented the "Reset Hardware Defaults" button in
  the Display Settings page of nvidia-settings from being activated.



It seems that was driver issue.

---

