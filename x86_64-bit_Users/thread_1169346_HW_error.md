---
title: "HW error?"
date: 2009-05-25
forum: x86 64-bit Users
---

### Post by Lerxst on 2009-05-25
I think I may have a hardware error on my system. I have before upgrading to 9.04 (from 8.10) experienced complete lockups where my PC was unresponsive (the frequency was about once per week). Nothing was logged nor in the usual places or on the console if I left it running there, so I never found out what was causing it, other than that some programs started segfaulting at first.
I replaced the memory modules but that didn't help.

Now after upgrading to 9.04, my system is almost completely unusable. I can boot it, start Firefox (or something else) and all of a sudden everything will segfault and the computer eventually locks up. This can happen after a minute or hours or at most a day. I have a dual core (E2200) and have tried disabling core 1 - no dice.

Now, everything is logged, and this is what I usually see:

> May 11 16:59:34 superunknown kernel: [368292.095134] deluge[21585]: segfault at 7fc958f6cb30 ip 00007fc958c3986a sp 00007fff61bfdea0 error 6 in libc-2.9.so[7fc958bbf000+168000]
May 11 17:00:02 superunknown kernel: [368319.925163] pam-foreground-[21650]: segfault at 40008 ip 0000000000402343 sp 00007fffc2a1f3b0 error 4 in dash[400000+19000]
May 11 17:00:02 superunknown kernel: [368320.178009] ntpdate[21663]: segfault at 1ffff8 ip 00007fa60e7f8225 sp 00007fff1729d4d0 error 4 in libc-2.9.so[7fa60e77e000+168000]
May 11 17:21:39 superunknown -- MARK --
May 11 17:40:02 superunknown kernel: [370720.123675] landscape-sysin[28953]: segfault at 7feaf85e11c8 ip 000000000045a290 sp 00007fff00901028 error 4 in python2.6[400000+216000]

Especially error 4 in python2.6 occurs frequently before I need to reboot.

For instance, during this night my pc locked up again and I rebooted it this morning. here's from messages.0:

> May 25 06:41:11 superunknown dhcdbd: Started up.
May 25 06:41:14 superunknown kernel: [   25.721765] ppdev: user-space parallel port driver
May 25 06:41:18 superunknown kernel: [   29.623335] ip_tables: (C) 2000-2006 Netfilter Core Team
May 25 06:42:33 superunknown kernel: [  104.916012] CPU 1 is now offline
May 25 06:42:33 superunknown kernel: [  104.916016] SMP alternatives: switching to UP code
May 25 06:47:35 superunknown kernel: [  407.123233] apt-get[5975]: segfault at 7fe1578b0000 ip 00007fe1521f8070 sp 00007fff5a69a550 error 4 in libapt-pkg-libc6.9-6.so.4.7.0[7fe1521bd000+bc000]
May 25 06:48:53 superunknown kernel: [  485.142170] apt-get[6122]: segfault at 7fb84293f000 ip 00007fb83d287070 sp 00007fff4572aa40 error 4 in libapt-pkg-libc6.9-6.so.4.7.0[7fb83d24c000+bc000]
May 25 06:50:11 superunknown syslogd 1.5.0#5ubuntu3: restart.

I took cpu1 offline. 6 minutes after it booted, the first segfault starts. This is before I've launched any application at all.

I have googled and it seems that kernel 2.6.28-12 is unreliable with glibc and python 2.6, but is this the case or do I have a hardware error?
Since it seems that my memory was not the problem and at least one core is unaffected (I am unable to take core0 offline), could it be some weird thing/error with the motherboard?

---

### Post by Sef on 2009-05-25
It could just be a bad upgrade too.   You may have to do a clean install.   I would download and run the Live CD of Jaunty.   See how that works for you.  If it does, then do a clean install.

---

### Post by Lerxst on 2009-05-26
> **Sef said:**
>   I would download and run the Live CD of Jaunty.   See how that works for you.  If it does, then do a clean install.

Good idea, thank you.

---

### Post by Anubis on 2009-05-26
"I have googled and it seems that kernel 2.6.28-12 is unreliable with glibc and python 2.6, but is this the case or do I have a hardware error?"

Sounds like both to me. I don't use that -12 kernel version either. My system became unstable, ie froze for no apparent reason. Moved back to -11 kernel, and uptime of 16days and no issues.

---

