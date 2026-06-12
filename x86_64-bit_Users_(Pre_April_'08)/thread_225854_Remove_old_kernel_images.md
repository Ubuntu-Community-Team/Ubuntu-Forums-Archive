---
title: "Remove old kernel images?"
date: 2006-07-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by cocteau on 2006-07-30
Hi

Having updated my kernel af few times grub now has 8 different settings to start different kernel versions of ubuntu. While I know how to comment the lines out in grub is there a way to actually remove the redundant kernel images without damaging my current setup?

---

### Post by Kilz on 2006-07-30
> **cocteau said:**
> Hi

Having updated my kernel af few times grub now has 8 different settings to start different kernel versions of ubuntu. While I know how to comment the lines out in grub is there a way to actually remove the redundant kernel images without damaging my current setup?

Yes they are listed in synaptic. Do a search for kernel. You will see them listed by version as linux-image. I believe removing linux-image will also remove the other files that version needs. You can safly remove all but the latest one if everything is working. I usualy leave the last 2 just to be safe. When you remove them in synaptic it will also remove them from the grub list.

---

### Post by cocteau on 2006-07-30
Thanks. That worked like a charm. I feel in control of my boot list again. Yaw!

---

### Post by John Jason Jordan on 2006-07-30
> **Kilz said:**
> Yes they are listed in synaptic. Do a search for kernel. You will see them listed by version as linux-image. I believe removing linux-image will also remove the other files that version needs. You can safly remove all but the latest one if everything is working. I usualy leave the last 2 just to be safe. When you remove them in synaptic it will also remove them from the grub list.
I just looked in Synaptic and I see:

linux-image-2.6.15-23-amd64-generic    2.6.15-23.39
linux-image-2.6.15-25-amd64-generic    2.6.15-25.43
linux-image-2.6.15-26-amd64-generic    2.6.15-26.45
linux-image-amd64-generic              2.6.15.24

I installed linuxinfo and ran it. It says:

jjj@Devil5:~$ linuxinfo
Linux Devil5 2.6.15-26-amd64-generic #1 SMP PREEMPT Mon Jul 17 19:50:04 UTC 2006One AMD x86_64 797MHz processor, 1598.06 total bogomips, 1279M RAM
System library 2.3.6
jjj@Devil5:~$

When I boot I see three choices in Grub, the top one is 26, which is what I always boot. There are no problems, so I think I want to remove the others. But what about that last one, linux-image-amd64-generic. What is that one?

And I have a related issue. The hard disk is partitioned as hda1 (swap, 1 GB), hda2 (60 GB) and hda3 (8 GB). This installation is a brand new fresh installation of Dapper made to the 8 GB partition, which I created expressly for the purpose of creating a Dapper test bed. I also installed Dapper on the 60 GB partition, but it is just a plain, standard installation. All the tweaking and installing of stuff has been to the hda3 installation. I am now satisified with the hda3 installation and wish to copy it to the 60 GB partition. The hda3 installation mounts hda2, so I can see it with Nautilus. I am planning on just removing everything from hda2, then copying everything from hda3 to hda2. I'll leave the hda3 installation as a rescue installation.

The problem is, when I boot both installations are available in Grub. The top one is the hda2 installation, and it lists two kernels, 23 and 26 (or maybe it is 24 and 26, I can't remember for sure). The second one is the hda3 installation and it lists 23, 25 and 26, as noted above. So when I use Synaptic to remove 23 and 25 from this hda3 installation, it will modify the Grub listing so it will show just 26 on the hda3 installation. Then I'll do the remove-all from hda2 and copy-all to hda2 from hda3. When I reboot, will selecting 26 in the hda2 Grub menu actually boot? In other words, what does Grub need in order to boot? If everything on hda3 is copied to hda2, complete with all permissions and ownerships, it should just boot from the Grub menu, right?

My goal is to copy the test bed installation to the larger 60 GB partition and use that as my main installation from now on. Will my plan above work, or is there a better way?

---

### Post by Loffe_ on 2006-07-30
Don't know if this is the best way, but this is what I should have done.

1. Live-CD with gparted
2. remove hda2
3. resize and move hda3 to the place where hda2 was. May take some time...
4. create a new hda2 in the new space after hda3

This way all the device names stays the same. There should not be any trouble with GRUB.

/Loffe

---

