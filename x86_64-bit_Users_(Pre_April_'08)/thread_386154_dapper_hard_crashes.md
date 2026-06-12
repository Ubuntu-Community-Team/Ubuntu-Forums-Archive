---
title: "dapper hard crashes"
date: 2007-03-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by N7DR on 2007-03-16
Hardware:
  mobo: ASUS A8N-SLI Premium
  CPU: AMD 64 X2 3800+
  video: NVIDIA e-GeForce 6200

OS: dapper with all updates

video driver: 
  1.0.8776+2.6.15.12-28.1 (dapper security)

History:
  This hardware ran Mandriva 2006 64-bit without any issues for about 8 months.

Now that I am running dapper I am seeing hard freezes. Sometimes several weeks go by without a freeze; sometimes there are several in a single day (like today).

I have re-seated all memory and cabling.
The temp of the CPU and the mobo are very cool (below 90 degrees F)
The memory has passed memtest86 (several times)

When I experience a freeze, it is without warning and hard: averything stops; I can't even ping the machine from another machine; all keyboard, mouse and video freezes. I have to power off and back on.

This is driving me crazy. I had two crashes today (so far).

PLEASE can anyone point me to something that would help me debug (or, better, fix) this problem?

---

### Post by encompass on 2007-03-16
Pay attention to what programs, if any are on when the crash occures.
I would also check for bios updates.  Helped me.

---

### Post by Kilz on 2007-03-16
> **N7DR said:**
> Hardware:
  mobo: ASUS A8N-SLI Premium
  CPU: AMD 64 X2 3800+
  video: NVIDIA e-GeForce 6200

OS: dapper with all updates

video driver: 
  1.0.8776+2.6.15.12-28.1 (dapper security)

History:
  This hardware ran Mandriva 2006 64-bit without any issues for about 8 months.

Now that I am running dapper I am seeing hard freezes. Sometimes several weeks go by without a freeze; sometimes there are several in a single day (like today).

I have re-seated all memory and cabling.
The temp of the CPU and the mobo are very cool (below 90 degrees F)
The memory has passed memtest86 (several times)

When I experience a freeze, it is without warning and hard: averything stops; I can't even ping the machine from another machine; all keyboard, mouse and video freezes. I have to power off and back on.

This is driving me crazy. I had two crashes today (so far).

PLEASE can anyone point me to something that would help me debug (or, better, fix) this problem?

Id bet on the video driver. You might want to install the proprietary one from nvidia.

---

### Post by N7DR on 2007-03-17
The video drivere IS the proprietary one from nvidia:
>  1.0.8776+2.6.15.12-28.1 (dapper security)
That, I believe, is the 1.0.8776 driver from nvidia.

ISo I have done the opposite of what you suggest, and switched out the nvidia one and am now using the open source one, nv. So I'll see if that improves things.

One of the problems is that sometimes the crashes will be a couple of weeks apart, so it's very difficult to know when the problem is fixed. I have been fooled at least twice into thinking that I've fixed it, and then had another rash of crashes :-(

---

