---
title: "boot up to a blank screen issue"
date: 2007-11-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by razorboy on 2007-11-25
I installed ubuntu 7.10 on my dell 1501 running an amd turion64 dual core - the system also has ATI Radeon®  Xpress 1150.

I installed the restricted driver for the ATI card and started getting all sorts of error messages with other programs....exit error 139 or something to that effect.  So I uninstalled the restricted driver and now the system boots to a black screen

no sound

but when I type, I do get the charactes showing up on the screen?

I scanned the forums to see how to solve this, but couldnt find any thing.  I have another installation of 7.10 (dont ask......i upgraded from 7.04 to 7.10 rather than reinstalling, then had back up issues.....whatever) running on another partition that works just fine, so I know that the hardware is functional

any thoughts?  If I had a clue what I was doing, I would dig to see if this is related to a bug already reported.

I assume what I want to do is reset my ubuntu video drivers to the original settings, but am not sure how to do this.

---

### Post by Kilz on 2007-11-25
> **razorboy said:**
> I installed ubuntu 7.10 on my dell 1501 running an amd turion64 dual core - the system also has ATI Radeon®  Xpress 1150.

I installed the restricted driver for the ATI card and started getting all sorts of error messages with other programs....exit error 139 or something to that effect.  So I uninstalled the restricted driver and now the system boots to a black screen

no sound

but when I type, I do get the charactes showing up on the screen?

I scanned the forums to see how to solve this, but couldnt find any thing.  I have another installation of 7.10 (dont ask......i upgraded from 7.04 to 7.10 rather than reinstalling, then had back up issues.....whatever) running on another partition that works just fine, so I know that the hardware is functional

any thoughts?  If I had a clue what I was doing, I would dig to see if this is related to a bug already reported.

I assume what I want to do is reset my ubuntu video drivers to the original settings, but am not sure how to do this.

```
sudo dpkg-reconfigure xserver-xorg
```

That command will reconfigure your graphics. You will get a list at some point, choose ati instead of flgrx. That should get the graphics back. If you choose the safe mode boot in grub it will bring you to a command line. You may not need the sudo in the command tthere.

The current graphics driver from ATI is a new one and full of bugs. Its a new code base. You may want to use the 8.40.4 driver and only upgrade when told it is safe. [his topic has more]("http://ubuntuforums.org/showthread.php?t=619714") on the problems and reasons not to use the newest driver at this time.

---

### Post by razorboy on 2007-11-25
much thanks - it worked

now I got back to where I was before it went blank.....

now I get  a blank beige screen with a cursor (that moves mind you) unless i log in under a failsafe mode

now to figure this out................(where is my vista disk :))

---

