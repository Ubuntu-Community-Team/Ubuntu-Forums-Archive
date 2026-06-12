---
title: "Nasty new AMD64 auto update"
date: 2006-09-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by David Jenkins on 2006-09-15
Last night I had a notification for the new kernel.  Tried to install it, but got a 403 error (presumably the file wasn't there). I tried again this morning, and it downloaded.  Got to the reboot - and got a crash after xstart, reporting a problem with the nvidia driver.  I edited the config file so that I could at least start X, and found some more updates showing - including nvidia.  Taking those updates and rebooting seemed to put everything back to a working state.

Now I notice that I am unable to mount removable media, something that was working perfectly prior to the kernel update.  

Luckily I have a reasonable amount of Linux knowledge, otherwise my system would now be useless - this is NOT a good way to upgrade a system that's directly aimed at new Linux users! :mad: 

Now can anyone suggest how to get the removable media working once more?

regards,
David

UPDATE: I see from the sticky thread further down that the nvidia problem has been spotted and dealt with - but any poor user who has lost his video will be unable to see the fix instructions! :o

---

### Post by sdledesma on 2006-09-15
In my case I get kernel panics when trying to boot from the updated kernel. Unfortunately I decided to uninstall all older kernels a few days ago since the current one was working fine (what could possibly go wrong?). 

This is what I get when booting

***---
RAMDISK: ran out of compressed data
invalid compressed format (err=1)
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
---***


It looks like I have a corrupt kernel image. Oh well...

](*,) 

I'm just curious to know if anybody else has had any problem with their kernel updates on amd64 or if this is just my computer

---

### Post by David Jenkins on 2006-09-15
I have seen various strange things happening, e.g. a total x-windows lockup just after opening Firefox, requiring a hard reboot (x-restart didn't work, as the keyboard was completely frozen) - this NEVER happened with the old kernel.

---

### Post by Kilz on 2006-09-15
> **David Jenkins said:**
> I have seen various strange things happening, e.g. a total x-windows lockup just after opening Firefox, requiring a hard reboot (x-restart didn't work, as the keyboard was completely frozen) - this NEVER happened with the old kernel.

IMHO its always nice to have the current kernel, and the one just before it. In case of problems like this. Its easier to just go back to the older kernel by booting it untill the bad update is fixed.
But lets hope this isnt a trend, the bad updates thing.

---

### Post by sdledesma on 2006-09-15
This looks too big a screw up to be a generalized thing. If it was we would be seeing LOTS of posts about it. I'm fairly sure this is a problem with my computer rather than an update induced crash. But I wanted to check just in case.

Thanks.

Santi

---

### Post by David Jenkins on 2006-09-16
> **Kilz said:**
> IMHO its always nice to have the current kernel, and the one just before it. In case of problems like this. Its easier to just go back to the older kernel by booting it untill the bad update is fixed.
But lets hope this isnt a trend, the bad updates thing.

It would have been nice to know this BEFORE picking up the update... sigh... :( 

I was starting to get so impressed with Ubuntu as well...

David

P.S. The list of new bugs so far includes:

No longer able to mount removable media other than USB drives
Firefox crashing 30 seconds after starting (I believe caused by the screensaver running prior to starting Firefox)

---

### Post by David Jenkins on 2006-09-16
One question - is it possible to reload the previous kernel version?

If so, how is it done?  It's not something I've attempted before.

David

---

### Post by RoyArne on 2006-09-16
> **David Jenkins said:**
> One question - is it possible to reload the previous kernel version?

If so, how is it done?  It's not something I've attempted before.

David

I think you can select a different kernel from the Grub menu, when you boot (If the previous version of the kernel is still on your system). The computer waits three seconds or so early in the boot sequence; it gives a message to press "1" (i think) to enter the grub menu.

---

### Post by hajk on 2006-09-16
> **Kilz said:**
> IMHO its always nice to have the current kernel, and the one just before it. In case of problems like this. Its easier to just go back to the older kernel by booting it untill the bad update is fixed.
But lets hope this isnt a trend, the bad updates thing.

I agree, except this wasn't a version upgrade...

---

### Post by David Jenkins on 2006-09-17
I now have 2 installations of Ubuntu - 1 on a normal laptop and the other on an AMD64 'desktop'.  The laptop is working OK and coped with the kernel upgrade without problems: the AMD64 installation is now unreliable, to the point where I'm thinking of reverting to Mandriva (which has previously served me well for several years).

Is there any urgency in getting this kernel fixed and re-issued?

David

---

### Post by David Jenkins on 2006-09-18
Well... I've just installed a brand-new AMD64 kernel update, complete with assorted drivers, and it seems to be working properly.

I don't want to say too much yet - but I may be feeling a lot happier! :D

David

---

### Post by kleeman on 2006-09-18
Lucky you. The latest 2.6.15-27-amd64-xeon kernel caused a kernel lockup for me. I am starting to get a tad pissed off. Why is Ben Collins not getting enough support from Canonical? IMHO there should be at least two kernel developers and extensive testing with a large range of hardware before releasing updated kernels for LTS distros. And why have they not straightened out Quality Assurance as promised by sabdfl about a month ago following the xorg screwup?

This seems to be the second or third major screwup with QA in a month. Not good for an LTS distro.

Careful Mark if you don't get these issues sorted all the good work to date may be undone.

I have been a loyal Ubuntu user right from the start (warty) but these screwups are raising significant doubts in my mind.

---

