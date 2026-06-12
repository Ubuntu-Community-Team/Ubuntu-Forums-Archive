---
title: "amarok slow on startup"
date: 2005-10-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by negatory on 2005-10-17
Whenever I start amarok the CPU usage goes to 100% for a few seconds and then it starts and acts normally.I've just compiled amarok 1.3.3 and this never happened in the earlier versions.From the console I can see that the cause of this (long) waiting time is this:
```
GStreamer-WARNING **: pushing data on non-negotiated pad dvddemux0:current_audio, not allowed.

```
It gets repeated for a few times and then starts normally.
A google search has not come up with any results that could solve this problem.
Thanks

---

