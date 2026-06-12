---
title: "nvidia driver reinstallation every reboot"
date: 2006-05-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by rotten777 on 2006-05-14
everytime i reboot i have to reinstall the driver and it works perfectly fine. on reboot i don't notice any errors but X doesn't start and i have to reinstall each time.

any idea?

i'm doing the

CC=gcc-3.4
export CC
./NV.....run

on K8SMP kernel

---

### Post by tseliot on 2006-05-14
Type:
```
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
```

and reinstall the driver

---

### Post by rotten777 on 2006-05-14
Reading package lists... Done
Building dependency tree... Done
Package nvidia-glx is not installed, so not removed
Package nvidia-settings is not installed, so not removed
The following packages will be REMOVED:
  linux-amd64-generic* linux-amd64-k8-smp*
  linux-restricted-modules-2.6.12-10-amd64-generic*
  linux-restricted-modules-2.6.12-10-amd64-k8-smp*
  linux-restricted-modules-2.6.12-10-amd64-k8-smp-nvidia-legacy*
  linux-restricted-modules-2.6.12-9-amd64-generic*
  linux-restricted-modules-2.6.12-9-amd64-k8-smp-nvidia-legacy*
  linux-restricted-modules-amd64-generic*
  linux-restricted-modules-amd64-k8-smp* nvidia-kernel-common*
0 upgraded, 0 newly installed, 10 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 57.5MB disk space will be freed.
Do you want to continue [Y/n]?



is that right? it looks like it's going to remove my kernel

---

