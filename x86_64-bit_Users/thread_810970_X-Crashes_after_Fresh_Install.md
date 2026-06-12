---
title: "X-Crashes after Fresh Install"
date: 2008-05-28
forum: x86 64-bit Users
---

### Post by evanmanny on 2008-05-28
Hello,

I just installed 64bit Ubuntu Hardy Heron on to a pc. GDM comes up fine but after I log in it hangs for a bit and then returns to GDM. If I try to switch to the command line using alt-ctrl-f# I just see a visually distorted unresponsive version of GDM. I'm guessing it's an X problem. In X0rg.0.log it says "Chipset ATI Radeon XPRESS 200 5954 (PCIE) found." Does anybody have any ideas?

---

### Post by evanmanny on 2008-05-29
I tried installing 7.10 instead of 8.04 and everything worked fine. Then I upgraded to 8.04 and I got the same problem.

I had a feeling that it might have something to do with compiz so I booted into recovery mode and did sudo apt-get remove compiz. This completely solved the problem.

If Ubuntu is coming with desktop effects enabled by default then shouldn't it fall back on to metacity if they don't work? Is this a bug?

---

### Post by Kilz on 2008-05-29
> **evanmanny said:**
> I tried installing 7.10 instead of 8.04 and everything worked fine. Then I upgraded to 8.04 and I got the same problem.

I had a feeling that it might have something to do with compiz so I booted into recovery mode and did sudo apt-get remove compiz. This completely solved the problem.

If Ubuntu is coming with desktop effects enabled by default then shouldn't it fall back on to metacity if they don't work? Is this a bug?

Perhaps it would be nice. But I always find it easier, and less stressful to simply do a clean install. Updates can go wrong in so many ways depending on whats installed. It also helps if you have a separate home partition or another partition that holds all your media files and documents. You can mount it and have less work than fixing upgrade bugs.

---

### Post by octoberdan on 2008-09-08
I was experiencing the same issue. I believe it has something to do with using a non-3D graphics module. I got around this by

1. In GDM, change session to failsafe terminal
2. run "sudo apt-get remove compiz*"
3. run "exit"
4. Log back in

I am now going to try enabling the restricted modules and reinstalling compiz. Wish me luck!

---

### Post by octoberdan on 2008-09-08
> **octoberdan said:**
> I was experiencing the same issue. I believe it has something to do with using a non-3D graphics module. I got around this by

1. In GDM, change session to failsafe terminal
2. run "sudo apt-get remove compiz*"
3. run "exit"
4. Log back in

I am now going to try enabling the restricted modules and reinstalling compiz. Wish me luck!

Reinstalling compiz worked! After you've enabled the restricted drivers, you can safely reinstall the compiz-gnome package and use compiz without issue. 

1. Enable restricted drivers; System -> Administration -> Hardware Drivers -> enable the driver for your graphics card.
2. Reboot system
3. Log back in
4. (Optional) Enable effects; System -> Preferences -> Appearance -> Visual Effects (tab)
5. Have fun.

---

