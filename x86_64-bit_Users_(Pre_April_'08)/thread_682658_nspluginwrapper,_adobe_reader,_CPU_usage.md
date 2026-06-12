---
title: "nspluginwrapper, adobe reader, CPU usage"
date: 2008-01-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by chrism66 on 2008-01-30
All right document viewer was not printing my school pdf's, so I installed acrobat and used nspluginwrapper to get it to work in Swiftweasel. I did this on both my laptop, and my desktop. Both now have at least both cores roughly pegged at 50% at all times. Does any one have a clue at what is going on? Thanks in advance for any help.

---

### Post by Kilz on 2008-01-30
> **chrism66 said:**
> All right document viewer was not printing my school pdf's, so I installed acrobat and used nspluginwrapper to get it to work in Swiftweasel. I did this on both my laptop, and my desktop. Both now have at least both cores roughly pegged at 50% at all times. Does any one have a clue at what is going on? Thanks in advance for any help.

Sounds like the plugin is running at all times. open a terminal and type in ```
top
``` and see whats running. There is a cpu column, it should tell you whats eating up the processing.

---

### Post by chrism66 on 2008-01-30
All right ran "top" and the big hog was "ld-linux.so.2" I killed it and the CPU usage went down to normal. Is there a way to fix this?

[EDIT:] Well top says "ld-linux.so.2" is using 50% cpu usage, and "XORG' is using another 50%. When "ld-linux.so.2" is killed the "XORG' drops done to 0-1% usage.

---

### Post by daniix on 2008-03-24
It happens to me as well. I tried adobe reader because it was quite better than evince, but now seams it doesn't work fine.

My processor is x86 32bit. I know this thread is for 64bits but the sympthomes are the same.

I hope anyone could help us.

---

### Post by daniix on 2008-03-24
In addition, it increases memory usage until 100%.

---

### Post by firecrow8 on 2008-03-27
I had this issue as well but in reverse.

when I installed ubuntu it was increably slow until I configured nspluginwrapper to work with the proper broadcom driver for my WLAN card.

when that was set up my computer became twice as fast.

---

