---
title: "64 bit Server ?"
date: 2007-06-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by ruiruas on 2007-06-17
Hi,
I'll be installing a new web server for my school in the next weeks and I'm thinking if I should install the 64bit distro or the 32bit.
Can anyone advise me? the new machine will be:

Core 2 Duo E6420
4GB ram
2 sataII disks in software RAID 1

I'll be installing a "MOODLE" in it for my school (about 1300 users)...

Is it safe to use the 64bit version? 
Is it better in anyway, using an apache server, MySQL and PHP?
Is there anything to gain in the 64bit version? 
Is it truly stable?

---

### Post by incubus on 2007-06-17
ruiruas,

This is a common question and it is best to read the existing discussions first:

[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

Reliable and stable, yes, by the way.  To get useful answers (as opposed to "I love it, I hate it"), you'll have to ask more specific questions.  "Is it better?"-type of questions will typically lead nowhere, something you can confirm yourself by reading past threads.  It would be helpful, I imagine, to ask if somebody has any experience with Moodle on 64 bit, for example.  I don't, unfortunately.  But I do have a 64 bit server and have not had a problem related to 64 bit mode.

Boa sorte,

incubus

---

### Post by Kilz on 2007-06-17
Most people asking the question are interested in using Ubuntu as a desktop. As a desktop there are some things that require setup because of desktop use. Things like a browser and plugins because there are no 64bit replacements for Macromedia flash, or java.
For a server these are not issues. There are few downsides to a 64bit server. The few bits of proprietary code a Desktop user needs are not needed. 

The MOODLE is available as a 64bit package in the repositories.


To answer the questions
[B]
Is it safe to use the 64bit version?[/B]
Yes very safe, as safe as the 32bit version.
[B]
Is it better in anyway, using an apache server, MySQL and PHP?[/B]
The ability to go over the 4gb ram limit of 32bit servers will improve performance. You could ask the same question of the 32bit version.

**Is there anything to gain in the 64bit version?**
There is a 4gb limit on Ram for the 32bit version. You will be able to make full use of your hardware.

**Is it truly stable?**
Yes.

---

### Post by ruiruas on 2007-06-17
Thanks guys,
I'm definitely going for the 64bit  distro!

---

### Post by interval1066 on 2007-06-17
Seriously, the 64 bit distro is fine. The only thing I have problems with is flash; I find I need to re-run the flashinstall script from time to time. Its a livable situation.

---

### Post by sel on 2007-06-17
If you are planning on using encryption on that site then you'll probably be better off with the 64 bit system check out 64bit speed [here]("http://enterprise.linux.com/enterprise/05/06/09/1413209.shtml?tid=121")... 

Also using 4GB ram IIRC 32bit PC systems will map device addresses into the last part of that address space making a 'hole' with device addresses and AGP apertures etc. where your ram should be (they may have fixed this).

---

