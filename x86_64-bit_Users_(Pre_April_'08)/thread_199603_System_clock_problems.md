---
title: "System clock problems"
date: 2006-06-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by thebasti on 2006-06-19
Hello,

I have a problem with my system clock - it gains anywhere between 5-20 minutes for each hour.

I have turned on 'Periodically synchronize clock with internet servers' but it doesn't seem to do that. When I turn it off and click 'Synchronize Now' it does successfully update time. So, I guess it's not a problem with NTP problem, since manual sync does work.

I think that this has something to do with the fact that I have Dapper 64-bit installed, because on all other computers (which have 32-bit version installed) clock sync works.

Also, it's worth mentioning that some days the clock doesn't move forward, i.e. it's ok whole day. But mostly it's going fast forward.

Regards,
Basti

---

### Post by dtfinch on 2006-06-19
I don't have any 64 bit systems, but my first suggestion would be to try booting with the noapic kernel option, as clock drift seems to be a sign of APIC problems. I had a system where the APIC timer would completely stop at times, taking the system down with it, and while researching it I noticed many reports of it running fast, but usually a full 2x as fast in those cases.

---

### Post by handy on 2006-06-19
I'm on 32bit Dapper, & my clock gains hours.

I have the correct location set, It messes itself up whether I'm manually or automatically syncing on the web.

I just put my Dapper drive in, for the first time in about 3 days, & it was 2am (the minutes were correct) tomorrow's date!!

Any ideas?

---

### Post by zapcojake on 2006-06-19
the default Dapper kernel cured that same problem on my sempron 2800+.  Also if your ok with compiling your own kernel the ck11 patchset works too.

---

### Post by handy on 2006-06-19
Thanks for the reply.

Today I booted & the time is correct!

I'll just keep my eye on it at this stage, I expect that it's a bug that will dissapear soon...

I downloaded a new kernel today, so with luck it's dissapeared allready! :KS

---

### Post by handy on 2006-06-20
I had some problems with the new kernel, like many others.  They are sorted now, but noticed after a reboot that the clock was into tomorrow land again!?

---

### Post by thebasti on 2006-06-20
I still have same problem with drifting clock, although I have (at least I think I have) the latest kernel: 2.6.15-25-amd64-generic #1 SMP PREEMPT Wed Jun 14 11:28:03 UTC 2006 x86_64 GNU/Linux

I still haven't tried to turn off APIC like dtfinch suggested, I have to find out how to do it first.

---

### Post by handy on 2006-06-20
I think you add the line **APIC=off** or similar in the ***/boot/grub/menu.1st*** file.

Someone more knowledgable will confirm this for you I am sure.

---

### Post by thebasti on 2006-06-29
I still haven't figured out a proper way to fix the clock drift, but I did manage to get my clock in sync using cron to update time from NTP servers more frequently . I used the small script that I found on [Debian site under "Setting Time using NTP"]("http://www.debian.org/doc/manuals/system-administrator/ch-sysadmin-time.html#s16.4.2") and I simply put it to run as root's cron every 15 minutes.

Not the best solution, but at least I have correct system clock.

---

### Post by victor_c26 on 2006-06-30
What's are the downsides of turning off APIC?

Are there any system features that I'll lose if I turn APIC off? The System clock bug is killing me.

---

