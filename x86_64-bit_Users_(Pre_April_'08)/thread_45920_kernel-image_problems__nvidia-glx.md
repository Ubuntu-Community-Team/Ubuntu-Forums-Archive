---
title: "kernel-image problems \ nvidia-glx"
date: 2005-07-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tamir on 2005-07-02
hi, I compiled a kernel by my-self, and I wanted *nvidia-glx*.
I did : ```
apt-get install nvidia-glx
```

and I got this:
```
root@ubuntu:/usr/src # apt-get install nvidia-glx
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  linux-image-2.6.10-5-amd64-generic linux-restricted-modules-2.6.10-5-amd64-generic
Suggested packages:
  lilo linux-doc-2.6.10 linux-source-2.6.10
The following NEW packages will be installed:
  linux-image-2.6.10-5-amd64-generic linux-restricted-modules-2.6.10-5-amd64-generic nvidia-glx
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/22.3MB of archives.
After unpacking 77.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
Selecting previously deselected package linux-image-2.6.10-5-amd64-generic.
(Reading database ... 32879 files and directories currently installed.)
Unpacking linux-image-2.6.10-5-amd64-generic (from .../linux-image-2.6.10-5-amd64-generic_2.6.10-34.3_amd64.deb) ...
Selecting previously deselected package linux-restricted-modules-2.6.10-5-amd64-generic.
Unpacking linux-restricted-modules-2.6.10-5-amd64-generic (from .../linux-restricted-modules-2.6.10-5-amd64-generic_2.6.10.5-1_amd64.deb) ...
Selecting previously deselected package nvidia-glx.
Unpacking nvidia-glx (from .../nvidia-glx_1.0.7174-0ubuntu1_amd64.deb) ...
Setting up linux-image-2.6.10-5-amd64-generic (2.6.10-34.3) ...
/usr/sbin/mkinitrd: Cannot determine SCSI module
Failed to create initrd image.
dpkg: error processing linux-image-2.6.10-5-amd64-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.10-5-amd64-generic:
 linux-restricted-modules-2.6.10-5-amd64-generic depends on linux-image-2.6.10-5-amd64-generic; however:
  Package linux-image-2.6.10-5-amd64-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.10-5-amd64-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nvidia-glx:
 nvidia-glx depends on nvidia-kernel-1.0.7174; however:
  Package nvidia-kernel-1.0.7174 is not installed.
  Package linux-restricted-modules-2.6.10-5-amd64-generic which provides nvidia-kernel-1.0.7174 is not configured yet.
  Package linux-restricted-modules-2.6.10-5-amd64-k8 which provides nvidia-kernel-1.0.7174 is not installed.
dpkg: error processing nvidia-glx (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.10-5-amd64-generic
 linux-restricted-modules-2.6.10-5-amd64-generic
 nvidia-glx
E: Sub-process /usr/bin/dpkg returned an error code (1)
``` 

I don't know what to do, I tried to install from apt-get source, it didn't work.
I want to use my compiled kernel, not an image one. can't I ?

---

### Post by alastair on 2005-07-02
Not sure. But if you are not using an Ubuntu installed kernel, then there may be issues using an Ubuntu kernel add-on like the nvidia-glx module (did you compile your kernel using the Ubuntu kernel config as a template?).

Remember, you could always just download the NVidia driver from the NVidia website ... as a last resort.

---

### Post by rsw on 2005-07-02
[QUOTE=alastair]
Remember, you could always just download the NVidia driver from the NVidia website ... as a last resort.[/QUOTE]


... and then fall victim to the no-symbols-bug? :(

---

### Post by Tamir on 2005-07-03
I am not sure, I installed kernel from gentoo-sources 'cause I wanted 2.6.12.
Should be problems with that? I want my Nvidia Driver to update, so downloading from website it is a last resort.

---

