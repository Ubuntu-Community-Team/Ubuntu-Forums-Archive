---
title: "Intrepid installation broken after upgrade"
date: 2009-01-28
forum: x86 64-bit Users
---

### Post by Artemus on 2009-01-28
I installed the upgrades for Intrepid AMD64 today (to kernel 2.6.27-11) and tried to reboot, but it failed on the restart with numerous errors about not being able to find libc.so.6. Thinking I must have done something to destroy the system, I reinstalled from scratch and did the updates again, and once again it died on reboot with the same error. Apparently there is something seriously wrong in one of the updated packages. Has anyone else run into this problem, and is there any fix for it?

---

### Post by cariboo on 2009-01-29
If you can start in recovery mode, once you get to the menu, select drop tot root prompt. To start networking at the prompt type:

```
dhclient eth0
```

Once you have obtained an ip address, at the prompt type:

```
apt-get install -f
```

The above command will install missing dependencies and hopefully get you back to a working installation.

Jim

---

### Post by theotherphil on 2009-01-30
Or you could just select one of the earlier Kernels from the Grub Menu.

---

### Post by Artemus on 2009-01-30
Thanks for the responses...I didn't have a chance to look at this forum again until now. I wasn't able to get back in using any of the other kernels nor to the recovery mode. It simply could not load the libc shared library for multiple commands (pages scrolled by too quickly to read all of them). This is my primary work machine that I can't afford to have it down for any amount of time, so I just decide to completely re-build the system (not just a simple reload from the CD). I installed on a new root disk for both re-installations to save my original /etc, /var, /usr/local, etc. so I didn't lose anything, but it took quite a while to get all the packages installed and my specific settings restored.

I don't think it was a dependency issue since the update completed without errors each time. I'm not willing to do the experiment again(!), so I just won't do another "apt-get upgrade" until either Jaunty is released or I see someone else have the problem and a solution gets posted.

---

