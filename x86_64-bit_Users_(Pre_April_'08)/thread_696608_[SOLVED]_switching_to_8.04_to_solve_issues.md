---
title: "[SOLVED] switching to 8.04 to solve issues"
date: 2008-02-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by littletinman on 2008-02-14
i'm going to give hardy haron a shot on my acer aspire 5520. So far with 7.10 i have no sound at all. Everything else works though. Can someone tell me if this is a good idea?

---

### Post by njparton on 2008-02-14
I guess it depends on what sort of onboard sound chip you have on your laptops motherboard and whether that's supported by linux?

---

### Post by Kilz on 2008-02-14
> **littletinman said:**
> i'm going to give hardy haron a shot on my acer aspire 5520. So far with 7.10 i have no sound at all. Everything else works though. Can someone tell me if this is a good idea?

It might be a good idea to run the livecd of Hardy to see if your issue will be solved before installing it over a working Gutsy install. 
Also be aware that Hardy (8.04) is still in ALPHA testing. You may end up with a lot of things broken as the developers work on the release. You may end up with an unusable system that no one can help you fix because not a lot of people are using it.
If you feel you want to anyway, you may consider just installing the Hardy kernel to see if it will fix your issues.

---

### Post by ZapalacX on 2008-02-14
sound is an easy fix on the 5520. 

```
sudo apt-get install linux-backports-modules
```

then restart.

---

### Post by littletinman on 2008-02-14
I did that and still nothing. I've tryed a ton of other stuff so i might end up starting from scratch. are you using 64 or 32 bit?

---

### Post by ZapalacX on 2008-02-14
i use the 64-bit version. that's what i've always done on this machine. what chipset do you have?

---

### Post by Kilz on 2008-02-14
This problem is cross posted by the original poster in multiple parts of the forum.

[http://ubuntuforums.org/showthread.php?t=696786](http://ubuntuforums.org/showthread.php?t=696786)
[http://ubuntuforums.org/showthread.php?t=696210](http://ubuntuforums.org/showthread.php?t=696210)
[http://ubuntuforums.org/showthread.php?t=696608](http://ubuntuforums.org/showthread.php?t=696608)

---

### Post by khensucat on 2008-02-14
For what it's worth, I have Hardy Alpha 4 installed in a *seperate* (very important to do, if you care about your data) partition, and I must say that even in it's *Alpha* state, on my machine (your mileage may vary), I've found it MUCH more reliable and stable than Gutsy. No lockups, everything works, no strange freezes, none of the plethora of issues I experience with Gutsy.

Of course, as I said, your experience may be completely different, and I use Dapper until Hardy is release, but if I, personally, had to choose between only Gutsy or Hardy for a daily environment, I would choose Hardy Alpha 4 as the more stable at this point in time ;)

---

### Post by Yellow Pasque on 2008-02-14
First off, stop rapidly cross-posting. All that does is sh!t up the forum.](*,)

If sound is your only problem, I would first recommend upgrading to the latest version of ALSA instead of upgrading your entire distribution. Here's a post with some scripts that make it real easy.
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

Then you have to set ALSA up, here's a thread i found on yahoo while trying to figure out what kind of sound hardware you had:
[http://www.suseforums.net/index.php?showtopic=45415&pid=227478&st=0&#entry227478](http://www.suseforums.net/index.php?showtopic=45415&pid=227478&st=0&#entry227478)

There you go. In the future, try and provide more information in a **single** post. And if you want **instant** help, a forum is not the place for that. Try IRC.

---

### Post by littletinman on 2008-02-15
I'm SOOOO sorry!!!! :( I didn't mean to mess anything up. I'm sincerely sorry if anyone was inconvenienced. I'll keep in mind not to mulitpost. Well here's the excellent news. I installed the 64 bit version of 7.10 and everything works after i installed the backports. Thank you all so much for the help. And i'm really really sorry for messing up the forum in any way.

  Phil W. R.

---

### Post by SunnyRabbiera on 2008-02-15
For me even if you have issues with 7.10 it still might be better to use it instead of Hardy as its alpha.

---

### Post by khensucat on 2008-02-15
Agreed. If you're *not* having problems, there's *no* reason to change ;-) I only suggested it because it actually solved alot of mine. But if my Gutsy were running fine, the *last* thing I would do would be to switch to an Alpha for stability :lolflag:

---

