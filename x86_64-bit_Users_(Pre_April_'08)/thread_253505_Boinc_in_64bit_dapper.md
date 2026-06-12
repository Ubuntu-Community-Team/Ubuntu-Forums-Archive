---
title: "Boinc in 64bit dapper"
date: 2006-09-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by KhaaL on 2006-09-08
Today when I was running BOINC, i recieved the following error:

2006-09-08 19:19:06 [[http://setiathome.berkeley.edu/]](http://setiathome.berkeley.edu/]) Requesting 8640 seconds of new work
2006-09-08 19:19:08 [[http://setiathome.berkeley.edu/]](http://setiathome.berkeley.edu/]) Scheduler request succeeded
2006-09-08 19:19:08 [SETI@home] Message from server: platform 'x86_64-pc-linux-gnu' not found


I also tried this with world community grid... Is there a known workaround for this?

---

### Post by gammagoat on 2006-09-10
four or five down, looks to me that these guys have a amd64 client.([http://boinc.berkeley.edu/download_other.php)](http://boinc.berkeley.edu/download_other.php)). I have not tried any of these yet, so I dont know if they work or not.

---

### Post by psyncho on 2006-09-12
Actually, if you install the 64 bit OS then the package management supplies a 64 bit boinc client. The problem is finding a project that works with one.  So far, I read that the einstein project works with it
[http://einstein.phys.uwm.edu/](http://einstein.phys.uwm.edu/)
however not the default one you can install through aptitude, at least not without some tweaking.  I saw some postings online about compiling.  There's a posting here on getting one running:
[http://einstein.phys.uwm.edu/forum_thread.php?id=4522](http://einstein.phys.uwm.edu/forum_thread.php?id=4522)


also, the climateprediction.net project claims to be o.k. with 64 bit though it doesn't utilize the extra power.  I haven't tried that one yet.

---

### Post by KhaaL on 2006-09-12
thank you all for your help, but i've taken the decision to "downgrade" to the i386 ubuntu since it does less hassle...

---

### Post by orthopod on 2007-10-20
BOINC was running fast for me on Feisty - Setiathome runs were taking 3-4 hours.  Now after the Gutsy upgrade they are taking 12 - any ideas?

---

### Post by LO Matt on 2007-10-20
I believe SETI will send a 32 bit application to a 64 bit OS.  I crunch einstein and they just recently started doing the same.  However, you need a newer version of the boinc client to do so.  Gusty comes with 5.10.8 in the repos, which works, but I had the same issue on einstein w/ feisty (which was 5.4.9 or something).  I'd assume dapper has an even older version.

The fix, download the latest x64 client from the boinc website and replace the dapper provided client with the new one.  It should work.  

And regarding gusty being slower than feisty, it's probably more the workunits than the OS, check that.

EDIT:  While you're downloading a boinc client, you should also look at using an optimized app on seti, they give a boost. Read their forums for which app would be best for your system.

---

### Post by orthopod on 2007-10-24
after installing gutsy, the power scaling option became turned on, and my cpu was set at 1000 MHZ instead of 2800.

I added to the gnome panel the CPU scaling monitor
typed this in the console
sudo chmod +s /usr/bin/cpufreq-selector

and now I could left click the applett and set my cpu speed
SET/Boinc runs are back to speedy self

---

