---
title: "Emerald seems kinda crash-happy in 64-bit Ubuntu"
date: 2007-11-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by FG123 on 2007-11-01
Something I've noticed in both Feisty and now Gusty, but only with the **64-bit** version so far, is that the Emerald window manager seems to be rather unstable. It will often crash for no reason, and seem to crash mostly during alt-tab window shifts, but not always like this, and of course when it crashes all the window controls disappear. Its bad enough I've made a shortcut on the top panel of my desktop so that when Emerald crashes, I'll just click on the launcher to execute *emerald --replace* and get back to work.

If I check /var/log/messages or type *dmesg* soon after it crashes, I'll get something similar to this at the bottom:

```
[40237.779636] emerald[24153]: segfault at 000000000000001f rip 000000000000001f rsp 00007fff5ce34188 error 14
```

Any ideas? It's not really a serious issue, mainly cos I can restore Emerald with one click when it happens, but I'd prefer a little more stability, since I don't remember having the same issues with the 32-bit versions of Ubuntu.

---

### Post by drogatoo on 2007-11-01
I have the same issue on 64bit version of opensuse 10.3, i think it's related to emerald.

---

### Post by drogatoo on 2007-11-23
I can confirm that I have this problem in Gutsy 64 on the same machine as well.Plus when I am trying to launch **emerald-theme-manager** I get **Segmentation fault (core dumped)**

mi ati driver is the latest 8.43 released on Nov. 21, 2007 , and the hardware is a HP laptop nx6125

---

### Post by rune0077 on 2007-11-23
Oh gosh! So, I never had any problem with Emerald at all - it seemed to be running fine. But then, I have never used alt+tab either. And when people tell me there's something I can't do, I usually run straight out and do it, just for the heck of it. So I hit alt+tab, and lo & behold, Emerald crashed.

Anyhows, like I said, it has never happened before. I can honestly say, that this is the first time Emerald ever crashed on me, and the first time I've ever used alt+tab. So, the lesson of the day: don't use alt+tab!

---

### Post by CareyB on 2007-11-23
Same in 32-bit version of Gutsy.

I wonder if there's a conflict.  How many processes are trying to trap the ALT-TAB binding?

Note:  This started happening at the same time I started using the Avant Window Navigator (AWN).

---

### Post by rune0077 on 2007-11-24
I'm not running AWN so it can't be that.

---

### Post by steveneddy on 2007-11-24
I've never had a problem with Emerald. It has always run well with no problems. I wonder if it is a problem with the theme you are using?

Is there an update to Emerald in SVN or something that could correct this?

My Emerald comes from a git repo that I think is in the regular repos because I didn't see it in the sources.list.

emerald version 0.3.0-svn

---

