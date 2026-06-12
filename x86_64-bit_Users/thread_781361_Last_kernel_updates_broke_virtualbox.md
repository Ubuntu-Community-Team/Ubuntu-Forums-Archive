---
title: "Last kernel updates broke virtualbox?"
date: 2008-05-04
forum: x86 64-bit Users
---

### Post by Pitou on 2008-05-04
Hello,

I just did the updates yesterday and now virtualbox doesn't anymore. It can't load the vboxdrv module anymore.

Any idea?

Pitou!

---

### Post by RowanC on 2008-05-04
I'm still learning Ubuntu, but Looks to me like the modules package didn't upgrade in the repos, and it can't deal with the old ones. I've found that if I boot into the last version of the kernel .16 it works (for now)

Cheers,
RowanC

---

### Post by Didjit on 2008-05-04
just run  
sudo /etc/init.d/vboxdrv setup
Then try again.
Didjit

---

### Post by Pitou on 2008-05-04
manager@univers:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for manager: 
 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}
manager@univers:~$ sudo /etc/init.d/vboxdrv start
 * Starting VirtualBox kernel module vboxdrv                                    
 * No suitable module for running kernel found.
manager@univers:~$

---

### Post by slo7 on 2008-05-04
Having the same problem. As shown above setup doesn't work.
The vboxdrv script has the following lines:

# Modified for Ubuntu by Daniel Hahler:
# - Removed "setup" action
# - Removed "/lib/lsb/init-functions"-conditional

Anyway, I'm content running the older kernel until the modules package is updated. I run Ubuntu so I can get some work done, not so I can spend hours fixing the system ;)

---

### Post by roberine on 2008-05-04
Have you checked that the linux-headers package for the
latest kernel is installed. This is needed.

---

### Post by Didjit on 2008-05-04
Strange, I have had no problems  with the updates after running the setup again. Maybe it needs Kernel Headers and you didn't get them? Not sure....
Didjit

---

### Post by John Jason Jordan on 2008-05-04
> **Pitou said:**
> I just did the updates yesterday and now virtualbox doesn't anymore. It can't load the vboxdrv module anymore.
I did the upgrade from Gutsy to Hardy the other day, but hadn't tried my installation of Windows on Virtualbox yet. Upon seeing this thread I tried it. Virtualbox launched, but when I tried to start Windows I got:

"Vitrualbox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g., virtualbox-ose-modules-generic."

So I launched Synaptic and looked at the log list of "Installed, local or obsolete" and found the modules for 2.6.24-14-generic. Then I opened a command line and did "uname -a," which said I had kernel 2.6.24-16-generic. So I searched in Synaptic and found the virtualbox-ose-modules-2.6.24-16-generic package and marked it for installation. Marking it for installation automatically marked the -14 modules package for removal. I clicked on Apply so Synaptic would install the new package and remove the old one. Afterwards I relaunched Virtualbox, and then Windows launched just fine.

Thanks to all who pointed out the problem. If I hadn't seen this thread I wouldn't have known there was a problem until I went to launch Windows. It's a lot easier to fix things when you're not in a hurry and have time to poke around.

---

### Post by slo7 on 2008-05-04
Aye, I'm guessing the problem is enabling pre-released updates (hardy proposed) in synaptic.  :P

The updated kernel package linux-image-2.6.24-17-generic originates from pre-released updates, whereas the newest kernel from hardy is 2.6.24-16

Synaptic shows that the newest virtualbox-ose-modules package is virtualbox-ose-modules-2.6.24-16-generic and that there is no version 2.6.24-17 equivalent in pre-released updates.

I'm now beginning to think enabling pre-released updates wasnt such a grand idea.

---

### Post by robmoore on 2008-05-05
Thanks for the hint! I, too, am regretting that decision now...

---

### Post by Anthony M on 2008-05-05
Thankfully this bug has been reported

[https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose-modules/+bug/226753](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose-modules/+bug/226753)

---

### Post by stbcomp on 2008-06-04
> **Pitou said:**
> manager@univers:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for manager: 
 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}
manager@univers:~$ sudo /etc/init.d/vboxdrv start
 * Starting VirtualBox kernel module vboxdrv                                    
 * No suitable module for running kernel found.
manager@univers:~$

I tried this solution, but setup was not one of the options. So I decided to try start instead which worked nicely.
Thanks for the hint!

---

### Post by ASULutzy on 2008-06-05
If you've installed the -18 kernel then there aren't suitable modules for it yet. You'll need to boot into the -17 kernel until there are modules made available for the newest kernel

---

