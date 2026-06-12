---
title: "[SOLVED] Adobe flash (no 64-bit support?)"
date: 2008-12-18
forum: x86 64-bit Users
---

### Post by Moonfrost on 2008-12-18
Hi, I'm trying to install Adobe Flash but it turns out that in this day and age they don't support 64 bit architectures!

Anyway, I was wondering if there's some way of installing it without me having to install a 32 bit browser (which also would be troublesome)?

I have Kubuntu 8.10 64 bit and last time (my previous hard drive died on me so I replaced it, I only use one HDD) I installed it I didn't have this problem at all so I figured that Adobe already had 64 bit support, if I install it through Adept it just doesn't work on Firefox at all no matter what...anybody know? I've been using 64 bit Linux for quite some time and never had this problem, I didn't even know Adobe didn't yet support 64 bit since I never had the problem.

A little bit out of topic:

How is Gnash doing these days? with the all the improvements they were trying to do these past few months how is it doing now? is it still any good?

---

### Post by lonniehenry on 2008-12-18
see the link [http://ubuntuforums.org/showpost.php?p=6196594&postcount=451](http://ubuntuforums.org/showpost.php?p=6196594&postcount=451)
it is 64 bit flash and works perfectly with intrepid and jaunty.

---

### Post by stchman on 2008-12-18
Install the flashplugin-nonfree package.  That is Flash 10.  Works in 32 or 64 bit.  The package has nspluginwrapper as a dependency which allows you to run 32 bit Flash in a 64 bit environment.

---

### Post by SeePU on 2008-12-18
> **lonniehenry said:**
> see the link [http://ubuntuforums.org/showpost.php?p=6196594&postcount=451](http://ubuntuforums.org/showpost.php?p=6196594&postcount=451)
it is 64 bit flash and works perfectly with intrepid and jaunty.

Yeah, his link is a good one.  

Also, check this one out:

[http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html]("http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html")

---

### Post by Moonfrost on 2008-12-18
> **lonniehenry said:**
> see the link [http://ubuntuforums.org/showpost.php?p=6196594&postcount=451](http://ubuntuforums.org/showpost.php?p=6196594&postcount=451)
it is 64 bit flash and works perfectly with intrepid and jaunty.

Thanks! that works flawlessly!

---

### Post by lonniehenry on 2008-12-18
you are welcome.  It solved my problems. They should update the sticky for the 64 bit people.  Please mark solved so others can use this solution.

---

