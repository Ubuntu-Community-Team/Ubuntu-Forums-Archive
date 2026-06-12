---
title: "kernal upgrade: Ubuntu 8.10, kernel 2.6.27-12-generic"
date: 2009-02-18
forum: x86 64-bit Users
---

### Post by jet2230 on 2009-02-18
i just updated to the latest kernal 2.6.27-12-generic via ubuntu update.

problems i encounted after restart:
[LIST]
[*]graphcs card modules had to re-installed - for me i had to install the nidia drivers again so:
sudo /etc/init.d/gdm stop
sh NVIDIA-Linux-x86_64-180.29-pkg2.run
sudo /etc/init.d/gdm start

[*]vmware stopped working, to fix run: sudo /usr/bin/vmware-config.pl
[/LIST]

cant notice any other breakups.. if i do i will update this post.

---

### Post by Arup on 2009-02-18
> **jet2230 said:**
> i just updated to the latest kernal 2.6.27-12-generic via ubuntu update.

problems i encounted after restart:
[LIST]
[*]graphcs card modules had to re-installed - for me i had to install the nidia drivers again so:
sudo /etc/init.d/gdm stop
sh NVIDIA-Linux-x86_64-180.29-pkg2.run
sudo /etc/init.d/gdm start

[*]vmware stopped working, to fix run: sudo /usr/bin/vmware-config.pl
[/LIST]

cant notice any other breakups.. if i do i will update this post.


If you have installed nvidia drivers from the nvidia site and not the repos, then you will have to re-install again.

---

### Post by matmat07 on 2009-02-18
Here the backlight(laptop) still isn't working. It stopped at the last kernel. the Fn key + the right arrow sended ± instead of raising the light, but in -12 it doesn't do anything.

---

### Post by SketchyClown on 2009-02-19
Apt has yet to report a kernel update to 2.6.27-12 here. Checked a few mirrors and none seem to have a kernel update.

---

