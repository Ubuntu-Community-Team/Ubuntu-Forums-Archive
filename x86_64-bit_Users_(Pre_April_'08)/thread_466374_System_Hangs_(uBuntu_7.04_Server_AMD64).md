---
title: "System Hangs (uBuntu 7.04 Server AMD64)"
date: 2007-06-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by stokkes on 2007-06-06
Hey everyone,

Posting my first post here, hopefully someone can shed some light. I can't provide a lot of info which is why I'm asking here for some assistance.

I've setup about a month ago a uBuntu 7.04 server (AMD64) and within the past few weeks i'm getting random  system hangs. When the system hangs, I can no longer SSH to it, access the file shares, even looking at the monitor hooked up to the server shows a black screen with nothing on it.

I have to hard reset the server to get it back, and obviously, this takes a while, since fsck has to check 750gb of space which takes an enormous amount of time. 

I'm just wondering where I can start looking for this.. I'm not sure if it's software or hardware related. I did run this same configuration on Windows XP for a while without these hangs, so I don't believe it's hardware based. Could be some driver going wonky, but again, I'm just looking (at this point) for a nudge in the right direction to help me get this sorted. 

Anything would be great !

---

### Post by dmfield on 2007-06-08
you could have a look in /var/log/messages it might tell you whats going on in there?

From Gnome System -> Administration -> System Log

---

### Post by stokkes on 2007-06-09
Here's an update:

I ran all the SMART tests, no errors on my hard drives, booted with memtest , no RAM errors, so I'm not sure what would cause this:

[46683.018116]
[46683.018118] HARDWARE ERROR
[46683.018119] CPU 0: Machine Check Exception:		4 Bank 4: b200000000070f0f
[46683.018147] TSC 556a9952579c
[46683.018155] This is not a software problem!
[46683.018164] Run through mcelog --ascii to decode and contact your hardware vendor
[46683.018179] Kernel panic - not syncing: Machine check
[46683.018289]

this happens quite often and hangs the system with that message (i have to hit the reset switch to restart the system, it's completely hung).

I'm not sure what else I can check.
I never had any issues in XP running the same system, and thus I'm questioning whether it's a hardware issue.

---

### Post by Sockerdrickan on 2007-06-09
uBuntu lol

---

### Post by stokkes on 2007-06-09
?

---

### Post by Sockerdrickan on 2007-06-09
u[SIZE="7"]**B**[/SIZE]untu

---

### Post by stokkes on 2007-06-09
So do you have any helpful information to share? Otherwise, stop wasting your time and increasing your post count.

---

### Post by Sockerdrickan on 2007-06-09
Are you jelous because I registered here 2 months earlier than you?

---

### Post by sen~ on 2007-06-18
> **stokkes said:**
> Here's an update:

I ran all the SMART tests, no errors on my hard drives, booted with memtest , no RAM errors, so I'm not sure what would cause this:

[46683.018116]
[46683.018118] HARDWARE ERROR
[46683.018119] CPU 0: Machine Check Exception:		4 Bank 4: b200000000070f0f
[46683.018147] TSC 556a9952579c
[46683.018155] This is not a software problem!
[46683.018164] Run through mcelog --ascii to decode and contact your hardware vendor
[46683.018179] Kernel panic - not syncing: Machine check
[46683.018289]

this happens quite often and hangs the system with that message (i have to hit the reset switch to restart the system, it's completely hung).

I have exactly the same problem on my File-Server (ubuntu 7.04 Server AMD64).
No drive errors (smart)
No ram errors (memtest)

```
CPU 0: Machine Check Exception:                4 Bank 4: b200000000070f0f
TSC 2866315f776
Kernel panic - not syncing: Machine check

```

**mcelog**
```
sen@FileServer:~$ sudo mcelog --k8 --ascii < mce.txt
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
CPU 0 4 northbridge TSC 2866315f776
  Northbridge Watchdog error
       bit57 = processor context corrupt
       bit61 = error uncorrected
  bus error 'generic participation, request timed out
      generic error mem transaction
      generic access, level generic'
STATUS b200000000070f0f MCGSTATUS 4
Kernel panic - not syncing: Machine check

```

Before I set up ubuntu server, arch was running on this machine without any problems...  does it really have to be an hardware error? :(

---

