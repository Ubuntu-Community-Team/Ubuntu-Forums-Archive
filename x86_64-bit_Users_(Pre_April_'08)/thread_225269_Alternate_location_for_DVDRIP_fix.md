---
title: "Alternate location for DVD::RIP fix?"
date: 2006-07-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by NetJumper on 2006-07-29
Hi all.
DVD::rip is one of those apps I have to have working, but so far, I have been completely unable to access the bombazine.mine.nu site to get dvdrip_0.52.5-0.1_amd64.deb

Anyone know of another site with this fix?

---

### Post by jamesford on 2006-07-29
i struggled with dvd:rip for ages myself with no luck, and discovered acidrip instead, its in the repos, much better application in my opinion

---

### Post by Kilz on 2006-07-29
> **jamesford said:**
> i struggled with dvd:rip for ages myself with no luck, and discovered acidrip instead, its in the repos, much better application in my opinion

K9copy is another good DVD copy application. But But you need version 1.0.4 for best results.

---

### Post by temna on 2006-08-02
Can anyone give the location of the fix?  I am interested in trying DVD::Rip.  And no, I do not want another suggestion of another piece of software to try, thank you.  I do not want to sound rude, but the guy asked where the fix was.  Not what else to use.

---

### Post by patbuntu on 2006-08-02
I installed dvd::rip through synaptic and then:

```
Tip of the day: if you encounter problems with dvd::rip 0.52.5 on your system (e.g. Gentoo, or AMD64 architecture) while 0.52.3 works try disabling the Workaround transcode NPTL bugs switch in dvd::rip's Preferences  and restart dvd::rip. 
```

From [the dvd::rip website]("http://www.exit1.org/dvdrip/index.cipp").

This stops it complaining about missing dependencies.  It works fine for me.

Is there a different problem you are having, or will this solve it?

Hope ths helps

-Pat

---

