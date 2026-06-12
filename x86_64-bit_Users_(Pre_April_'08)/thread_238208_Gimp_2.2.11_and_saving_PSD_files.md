---
title: "Gimp 2.2.11 and saving PSD files"
date: 2006-08-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by tomdkat on 2006-08-17
Has anyone here had problems with saving PSD files in Gimp 2.2.11 that neither Gimp or PhotoShop can open?

I created a PSD file using Gimp 2.2.11 on Windows and was able to open it using Gimp 2.2.11 on Linux (Ubuntu on AMD 64) just fine.  Then I made a minor change (hid a layer) and saved the PSD and now Gimp can't open it, nor can PhotoShop.  :(

I'm trying to determine if there's an issue with Gimp 2.2.11 and PSD files on Linux in general or if it's unique to a 64-bit Linux environment.

Thanks!

Peace...

---

### Post by tomdkat on 2006-08-17
Well, I found the answer to my question.  According to the [Gimp 2.3.x changelog](http://developer.gimp.org/NEWS), Gimp 2.3.8 has "64bit clean" PSD load/save plugins.

Oh well, I guess I'll have to wait to Gimp 2.4 to come out unless I get my [glib issue](http://ubuntuforums.org/showthread.php?t=237549) resolved.  :)

Peace...

---

### Post by fyo on 2007-08-12
This is completely f*ing ridiculous. Gimp 2.2.14 (and later) fixes this MASSIVE bug in Gimp. Why is the Gimp in the official Feisty repository still the broken-*ss 2.2.13???

This is a critical error and a complete DATA LOSS bug. I've worked hours, diligently saving my work at regular intervals, and everything is lost because 2.2.13 saves corrupt PSD files.

**THIS BUG IS EIGHT (8) MONTHS OLD!**

Why on Earth hasn't Gimp for Feisty been upgraded to fix this critical dataloss bug????

It's unf*ingbelievable.

---

### Post by Kilz on 2007-08-12
Most likely because no one has filed a bug report in launchpad about it. Most people are unaware of the fact that simply posting problems to the forums is not enough. The developers seldom look at the forums.

---

### Post by fyo on 2007-08-13
Considering that Gimpy is in the CORE, one would think (hope) that the devs actually kept a tab on any critical (security and data loss) bugs in those packages. Having to wait for someone to file a bug report in launchpad about it is stupid.

As can be plainly seen from this thread, tomdkat posted about it almost 12 months ago! Yet no one had filed a bug report in launchpad about it until I did just now. The conclusion is simple: Pretty much no one files launchpad reports, especially if it isn't a crash bug where the user is actually PROMPTED to do so.

However, this bug is more serious than a simple crash, since the user can continue to work even though the saved file(s) are corrupt - thus massively increasing the potential work lost. Ironically, if Gimp just crashed out, the loss of data would likely be extremely limited.

Thus, had the bug been less serious (crash), launchpad would likely have seen a bug report 12 months+ ago. Instead, no one has reported it (until now).

That's one reason why it's critical for the core packages to be updated when critical fixes are applied.

---

### Post by fyo on 2007-08-13
[https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/132143](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/132143)

That last line should have said "all **64bit** Ubuntu users", of course.

---

### Post by Kilz on 2007-08-13
> **fyo said:**
> Considering that Gimpy is in the CORE, one would think (hope) that the devs actually kept a tab on any critical (security and data loss) bugs in those packages. Having to wait for someone to file a bug report in launchpad about it is stupid.

As can be plainly seen from this thread, tomdkat posted about it almost 12 months ago! Yet no one had filed a bug report in launchpad about it until I did just now. The conclusion is simple: Pretty much no one files launchpad reports, especially if it isn't a crash bug where the user is actually PROMPTED to do so.

However, this bug is more serious than a simple crash, since the user can continue to work even though the saved file(s) are corrupt - thus massively increasing the potential work lost. Ironically, if Gimp just crashed out, the loss of data would likely be extremely limited.

Thus, had the bug been less serious (crash), launchpad would likely have seen a bug report 12 months+ ago. Instead, no one has reported it (until now).

That's one reason why it's critical for the core packages to be updated when critical fixes are applied.

No one files bug reports, because either they 
1. Expect someone else to do it - They are to lazy.
2. They expect the developers visit the forums - Never going to happen.
3. They dont know about launchpad - probably the most popular answer.

Sadly we get users who try the 64bit version, have some problem, give up , never file a bug report. They then install the 32bit version and report the 64bit version has problems. But they never do report it on launchpad. IMHO part of being a good Ubuntu user is reporting the bugs in the free software you receive so they can be fixed.

---

### Post by fyo on 2007-08-13
Kilz, I don't necessarily disagree with you. However, that doesn't obviate the need for package maintainers to keep an eye out for critical (security and data loss) bugs - especially CORE package maintainers.

---

### Post by Kilz on 2007-08-13
> **fyo said:**
> Kilz, I don't necessarily disagree with you. However, that doesn't obviate the need for package maintainers to keep an eye out for critical (security and data loss) bugs - especially CORE package maintainers.

Feel free to suggest it to them on their mailing list. The only place they seem to be contactable, They dont even look at the development section of the forum (Gutsy) [look at its disclaimer]("http://ubuntuforums.org/forumdisplay.php?f=238").
I wish you luck, I truly do, but I also know what you will be dealing with. My limited experience with the developers is that getting them to do anything is like pulling teeth.

---

