---
title: "Feisty Freezing with P4 650"
date: 2007-08-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by mkosem on 2007-08-31
Hi, I recently upgraded my cpu from an older 32-bit-only p4 3.2ghz cpu to a new EM64T cpu (p4 650 3.4ghz).  My system was working fine with the new cpu until I installed the 64-bit version of feisty.  I'm now running into freezing at odd times.  I've tried a few times to copy my music collection into banshee, but get a hard lock each time.  Shutting down also freezes the system.  It's definitely a hard lock-up, I cannot toggle caps-lock, move the mouse, or get to any of the virtual terminals.  I read on another thread that the linux-amd64-xeon kernel would be appropriate, but the thread was not for feisty.  Is this kernel also an option for me?

--Matt

Edit:  I do have the latest bios installed if that makes a difference.  My mobo is an A-Bit AA8XE.

---

### Post by Kilz on 2007-08-31
> **mkosem said:**
> Hi, I recently upgraded my cpu from an older 32-bit-only p4 3.2ghz cpu to a new EM64T cpu (p4 650 3.4ghz).  My system was working fine with the new cpu until I installed the 64-bit version of feisty.  I'm now running into freezing at odd times.  I've tried a few times to copy my music collection into banshee, but get a hard lock each time.  Shutting down also freezes the system.  It's definitely a hard lock-up, I cannot toggle caps-lock, move the mouse, or get to any of the virtual terminals.  I read on another thread that the linux-amd64-xeon kernel would be appropriate, but the thread was not for feisty.  Is this kernel also an option for me?

--Matt

Edit:  I do have the latest bios installed if that makes a difference.  My mobo is an A-Bit AA8XE.

Negative on the linux-amd64-xeon kernel. I dont think it even exists in Feisty, but is a dummy package. Sounds like you have a video driver problem to me.

---

### Post by mkosem on 2007-08-31
Thanks for the reply.  I'm running an NV 7300LE, which worked correctly with the drivers from the restricted driver manager on 32-bit feisty.  I've read of problems with it causing freezing, but the same version of the driver worked fine on my last install.  Is the process more involved on the 64-bit install?  It really doesn't seem video driver related, since I also have issues outside of X on the splash screen (when the system is shutting down).  What can I do/check?

--Matt

---

### Post by mkosem on 2007-08-31
Well, I eventually found this thread: [http://ubuntuforums.org/showthread.php?t=533494&highlight=7300+LE&page=3](http://ubuntuforums.org/showthread.php?t=533494&highlight=7300+LE&page=3)

It seems the restricted driver installer installed 1.0-9631.  I'll try my luck at 1.0-9755, but I'm kind of unsure that it will help the freezing that I'm seeing outside of X unless it's a kernel module issue that I'm facing.

--Matt

---

### Post by mkosem on 2007-08-31
Well, tried the 9755 driver via the nvidia-glx-new package.  I'm still getting lockups in when copying into banshee(0.13.1).  No other lockups yet though. The splash screen lockup hasn't happened yet either *fingers crossed*  Anyone have any suggestions?

---

### Post by mkosem on 2007-09-01
No dice, the system locks up when installing packages too.  Oddly, it's fine sitting idle for countless hours.  That makes 2 reproducible crash conditions:

1) copying library into banshee
2) installing 32-bit libraries to allow for nspluginwrapper

Does this really sound like a video driver issue?  I'd prefer not to do the manual install unless I have to.  But if it is likely to fix my problem, I'll give it a try.  I've just not seen much info on it(other than threads mentioning problems with the "newest driver").

--Matt

---

### Post by mkosem on 2007-09-01
Nevermind this issue, I ran a few runs of memtest86+ and found that one of the new memory modules that I bought is bad.  I'm all up and running just fine now!

--Matt

---

