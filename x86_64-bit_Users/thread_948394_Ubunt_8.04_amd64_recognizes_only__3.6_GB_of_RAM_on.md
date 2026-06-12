---
title: "Ubunt 8.04 amd64 recognizes only  3.6 GB of RAM on 4 GB RAM computer"
date: 2008-10-15
forum: x86 64-bit Users
---

### Post by abcuser on 2008-10-15
Hi,
I have installed Ubuntu 8.04 amd64 from [Minimal CD image](https://help.ubuntu.com/community/Installation/MinimalCD) on my computer. Computer has 4 GB of RAM.
In BIOS there is info: Installed memory 4096 MB, Available to OS 4069, Used by devices 27 MB.

By default on computer was Windows Vista which confirmed 4 GB of RAM.

After I have installed Ubuntu 8.04 amd64 I executed: free -m and result is total mem: 3677 MB.

In Ubuntu I have executed: uname -a and return is: x86_64 so I have 64-bit type of processor.

It looks like Ubuntu didn't recognized all available memory. What do I need to do to Ubuntu recognize 4 GB of RAM?
Regards,
Abcuser

---

### Post by Kevbert on 2008-10-15
It may be that some of the peripheral devices (especially display adapter) are using some of the memory. Regardless of that 3.6Gb seems low (mine shows 3.9Gb for 4Gb installed). Have you tried running memtest for example (in case of faulty memory) ?  I think you'll find Vista probably just reports the amount of memory seen by the bios and memtest performs a more expansive test than you get with the POST when you boot up.

---

### Post by overdrank on 2008-10-15
Moved :)

---

### Post by insane_alien on 2008-10-15
Have you checked your BIOS for memory remapping? if you find an option in there make sure it is checked.

---

### Post by abcuser on 2008-10-16
@Kevbert, memory test has passed succesfully.
@insane_alien, I can't see any option in BIOS for memory remapping.

More info:
I have purchased new [Lenovo ThinkCentre M57p](http://www5.pc.ibm.com/europe/products.nsf/$wwwPartNumLookup/_VVCBvxx?OpenDocument). I have purchased additional 2 GB RAM module. In first mem slot I have put 2 GB module, 1 GB in second slot and 1 GB in third slot.

In BIOS I have found out info in Devices section:
Active Video Intel Q33/Q35/G DUMT Graphics Memory: 376 MB.

Does this mean my video card is using my main memory? Is there way to free up memory used by video card?

---

### Post by jespdj on 2008-10-16
Indeed, it sounds like you have a graphics chip that doesn't have its own separate video memory, and that uses part of the main memory. I don't know if there's anything you can do to limit the amount of memory used by the graphics chip; obviously it does need *some* memory.

Is this really a problem, are you running software that really requires more than 3.6 GB RAM?

---

### Post by Kevbert on 2008-10-16
Unfortunately the missing memory is used by video. It looks like sound could also use some of the RAM.

---

### Post by toasty_ghosty on 2008-10-16
I have the same issue. I have 8gigs installed but Ubuntu only reports 7.8gigs. I have a video and sound card so that cannot be where the .2 is. Any reason?

---

### Post by brau0123 on 2008-10-16
I have 5 GB installed, BIOS says it's there, 

 sudo lshw -C memory

says its there, but I can only access 3.6 GB of it? any ideas

I'm running 64 bit os.

Thanks,

---

### Post by brau0123 on 2008-10-16
Should have added this:

Running  ~$ free -m  yeilds:
     total  used  free shared    buffers     cache
Mem: 3295   2620  675  0        120       2006
-/+ buffers/cache:        493       2801
Swap:         9648         38       9609

Any ideas what's wrong?

---

### Post by Agent ME on 2008-10-16
> **toasty_ghosty said:**
> I have the same issue. I have 8gigs installed but Ubuntu only reports 7.8gigs. I have a video and sound card so that cannot be where the .2 is. Any reason?
Do your video and sound cards have their own onboard ram, or maybe they just use some of the system memory?

---

### Post by toasty_ghosty on 2008-10-18
I have both a sound card and video card. My video card has its own gig so that isnt it. I don't really know about my sound card, but I really cannot imagine it using up that much ram...

---

### Post by abcuser on 2008-10-20
> **jespdj said:**
> Is this really a problem, are you running software that really requires more than 3.6 GB RAM?
400 MB out of 4000 MB is 10% of RAM. I have virtual machines running and having lost of 400 MB this means I can't use at least one or even two of them.

---

