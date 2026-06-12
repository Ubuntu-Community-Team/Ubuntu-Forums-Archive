---
title: "google sketchup 7 doesnt work on ubuntu 8.10"
date: 2008-11-18
forum: Wine
---

### Post by tuga3d on 2008-11-18
Any idea how to put this thing running?

installs ok, but gives segmentation fault when i try to run it.

here's the backtrace, dont know if helps.

```
Backtrace:
=>1 0x7c251000 (0x0032f4f4)
  2 0x7ed6c6ba WINPROC_wrapper+0x46a() in user32 (0x0032f534)
  3 0x7ed70622 CallWindowProcW+0x52() in user32 (0x0032f574)
  4 0x78311e4a in mfc80u (+0x31e4a) (0x0032f5e8)
  5 0x7ed6c26a WINPROC_wrapper+0x1a() in user32 (0x0032f618)
  6 0x7ed6c6ba WINPROC_wrapper+0x46a() in user32 (0x0032f658)
  7 0x7ed719cd in user32 (+0xb19cd) (0x0032f698)
  8 0x7ed31f97 in user32 (+0x71f97) (0x0032f6f8)
  9 0x7ed36ec5 in user32 (+0x76ec5) (0x0032f758)
  10 0x7ed373dc SendMessageW+0x4c() in user32 (0x0032f798)
  11 0x7ed123b0 in user32 (+0x523b0) (0x0032f868)
  12 0x7ed12565 in user32 (+0x52565) (0x0032f908)
  13 0x7ed12647 SetForegroundWindow+0x47() in user32 (0x0032f938)
  14 0x7ed677bf in user32 (+0xa77bf) (0x0032fa88)
  15 0x7ed67ed8 SetWindowPos+0xa8() in user32 (0x0032faf8)
  16 0x7ed6858d BringWindowToTop+0x4d() in user32 (0x0032fb28)
  17 0x78319b41 in mfc80u (+0x39b41) (0x0032fb98)
  18 0x7833eb59 in mfc80u (+0x5eb59) (0x0032fc40)
  19 0x00499b60 in sketchup (+0x99b60) (0x0032fc64)
  20 0x7833b54e in mfc80u (+0x5b54e) (0x0032fc70)
  21 0x7833b71e in mfc80u (+0x5b71e) (0x0032fc8c)
  22 0x0049afdc in sketchup (+0x9afdc) (0x0032fca8)
  23 0x7834a705 in mfc80u (+0x6a705) (0x00000001)
  24 0x00000000 (0x00000000)
Segmentation fault

```

thanks for taking the time to read.

---

### Post by dankegel on 2008-11-23
That's 
[http://bugs.winehq.org/show_bug.cgi?id=16164](http://bugs.winehq.org/show_bug.cgi?id=16164)

Sketchup 7 is working fine for me once I follow the tips in [http://wiki.winehq.org/GoogleSketchup](http://wiki.winehq.org/GoogleSketchup)
but I'm no expert.  
If after following the tips there, you still have
problems, please report them to the wine appdb or bugzilla
and I'll try to get them fixed, if I can.
Thanks!

---

### Post by tuga3d on 2008-11-23
thanks it worked!

I've set the reg keys of HW and snapyinstrutor to 0 and now at least it starts, going to further testing.

Thanks

---

