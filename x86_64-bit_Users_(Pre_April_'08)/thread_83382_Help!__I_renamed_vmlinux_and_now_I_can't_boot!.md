---
title: "Help!  I renamed vmlinux and now I can't boot!"
date: 2005-10-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Rob_Frohne on 2005-10-28
Hi,

Recently I noticed a problem where my Powerbook Lombard G3 was freezing periodically after updating ubuntu.  I thought I would go back to the previous kernel by renaming /boot/vmlinux to /boot/vmlinux.newer /boot/vmlinux.old to /boot/vmlinux and reboot.  Unfortunately, with this setup it can't find the lib/mod/... for the previous kernel of ubuntu, and I can't figure out the yaboot selection to get the /boot/vmlinux.newer to boot, so I can't boot at all!

I tried 

boot:/boot/vmlinux.newer 

and it kernel panics.

Any ideas?

Thanks,

Rob

---

### Post by kalin on 2005-10-28
Boot from the Live CD, mount the root partition, and rename the files as they were. That should help you boot into your system.

If you wan to run older kernels try looking for them in the repositories (Synaptic), the packages are named "linux-image-<version>", select those that you want, and after install they'll appear in the boot menu along with the last one.

That way you can try if an older kernel works for you without risking to break you system.

---

### Post by Rob_Frohne on 2005-10-28
Thanks, that worked!

Rob

---

### Post by kalin on 2005-10-31
Did an older kernel help on the freezing problem?

---

### Post by Rob_Frohne on 2005-10-31
I haven't made it that far yet, but I'll let you know.  The problem I've been having seems to occur after the machine has been up for a while.  It was happening about three or four kernels ago, where the machine would be locked up when I got back to the office every morning.  It would automatically reboot by itself, after I tried to wake it up by moving my finger over the trackpad or hitting keys on the keyboard.  It usually took a minute or two for the reboot to happen.  Then a kernel update came along that solved my problem, and I was delighted.  Unfortunately, it seems to have come back, though sometimes now the machine will still be up when I come back in a day or two.  I am planning to try a the last version of the kernel, and see how that works.  I'll let you know.

Rob

---

### Post by Rob_Frohne on 2005-10-31
I went to install the older kernel, and discovered that Syanptic Package manager said that it had installed a newer kernel yet (2.6.12.16), but there is no kernel in my /boot directory with that number.   I reinstalled it, and still there is no 2.6.12.16. 

Could this be a result of installing Mac-on-linux which required me to build the previous version of the kernel using the instructions on the Wiki?  The URL is:  

[https://wiki.ubuntu.com/MacOnLinuxHowto?highlight=%28Maconlinux%29](https://wiki.ubuntu.com/MacOnLinuxHowto?highlight=%28Maconlinux%29)

Rob

---

### Post by kalin on 2005-10-31
That's weird, what's the content of /boot?

BTW those instructions on the WiKi are about building only a set of modules, the kernel itself should be untouched.

---

### Post by kalin on 2005-10-31
Hm, the latest kernel I can find on packages.ubuntu.com is linux-image-2.6.12-9-powerpc, are you sure the 2.6.12.16 comes from the ubuntu repositories?

Not that it matters, it's still weird to have it installed and not to see it in /boot...

---

### Post by Rob_Frohne on 2005-10-31
Well, I looked at the Properties of the linux-image 2.6.12.16 and the files says it doesn't install anything in /boot and it depends on 2.6.12-9 and so it must not be a later version of the kernel exactly.  I also looked at the kernel I modified for Mac On Linux, and it was 2.6.12-9 and it seemed to be working just fine.  So my statement about the kernel that didn't work (assuming it was a kernel problem) would probably be that 2.6.12-8 had the problems because it was the kernel I was actually running when I was having the worst problems.  At this point I'm not sure how to proceed finding the problem.  

Are you having a similar problem?

Rob

---

### Post by kalin on 2005-11-01
No, I'm just curious, it's all good if everything works now :)

---

