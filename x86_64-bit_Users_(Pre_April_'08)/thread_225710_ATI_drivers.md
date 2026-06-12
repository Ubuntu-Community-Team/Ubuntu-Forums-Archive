---
title: "ATI drivers"
date: 2006-07-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by kriding on 2006-07-30
I've tried every ATI howto on here, and have finally manged to get all the drivers installed, however, if i type in 

```
fglrxinfo
```


I get this output

```
Error: couldn't find RGB GLX visual!

```


What does this mean?

also, in Cedega, when i run the system test, all the 3d graphics related tests fail

can anyone help?

My system is Athlon64 3200+, 1 Gb RAM, on a Gigabyte K8NS ultra 939 motherboard, my grahics card is ATI Radeon 9500

---

### Post by Kilz on 2006-07-30
> **kriding said:**
> I've tried every ATI howto on here, and have finally manged to get all the drivers installed, however, if i type in 

```
fglrxinfo
```


I get this output

```
Error: couldn't find RGB GLX visual!

```


What does this mean?

also, in Cedega, when i run the system test, all the 3d graphics related tests fail

can anyone help?

My system is Athlon64 3200+, 1 Gb RAM, on a Gigabyte K8NS ultra 939 motherboard, my grahics card is ATI Radeon 9500

I suggest you [go to ATI]("https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27") and get the ati-driver-installer and [use this howto]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.27.10_drivers_in_Ubuntu_Dapper_Manually") to install the latest 8.27.10 drivers.

---

### Post by kriding on 2006-07-30
that's the one I used. I've redone it, followed the troubleshooting guide and i still get the same error message

---

### Post by Kilz on 2006-07-30
> **kriding said:**
> that's the one I used. I've redone it, followed the troubleshooting guide and i still get the same error message

If you followed that howto, you have this package that it made. Please try and install it. Copy the terminal and paste it in a message when you are done.

```
sudo dpkg -i xorg-driver-fglrx_8.27.10-1_amd64.deb
```

---

### Post by kriding on 2006-07-30
as requested :) 

```
(Reading database ... 92321 files and directories currently installed.)
Preparing to replace xorg-driver-fglrx 8.27.10-1 (using xorg-driver-fglrx_8.27.10-1_amd64.deb) ...
Stopping atieventsd: done.
Unpacking replacement xorg-driver-fglrx ...
Setting up xorg-driver-fglrx (8.27.10-1) ...
Starting atieventsd: done.

```

---

### Post by Kilz on 2006-07-30
> **kriding said:**
> as requested :) 

```
(Reading database ... 92321 files and directories currently installed.)
Preparing to replace xorg-driver-fglrx 8.27.10-1 (using xorg-driver-fglrx_8.27.10-1_amd64.deb) ...
Stopping atieventsd: done.
Unpacking replacement xorg-driver-fglrx ...
Setting up xorg-driver-fglrx (8.27.10-1) ...
Starting atieventsd: done.

```

Ok no errors, try it with 
```
sudo dpkg -i fglrx-kernel-source_8.27.10-1_amd64.deb
```

---

### Post by kriding on 2006-07-30
```
(Reading database ... 92321 files and directories currently installed.)
Preparing to replace fglrx-kernel-source 8.27.10-1 (using fglrx-kernel-source_8.27.10-1_amd64.deb) ...
Unpacking replacement fglrx-kernel-source ...
Setting up fglrx-kernel-source (8.27.10-1) ...

```
 
here ya go

---

### Post by Kilz on 2006-07-30
> **kriding said:**
> ```
(Reading database ... 92321 files and directories currently installed.)
Preparing to replace fglrx-kernel-source 8.27.10-1 (using fglrx-kernel-source_8.27.10-1_amd64.deb) ...
Unpacking replacement fglrx-kernel-source ...
Setting up fglrx-kernel-source (8.27.10-1) ...

```
 
here ya go

I was expecting an error that I got that didn't show up. 
Just curious what dose the command
```
dmesg | grep fglrx
```
give you

---

### Post by kriding on 2006-07-30
it gives me 

```
[   61.494449] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   61.496014] [fglrx] Maximum main memory to use for locked dma buffers: 859 MBytes.
[   61.496232] [fglrx] module loaded - fglrx 8.27.10 [Jul 27 2006] on minor 0
[   65.414689] [fglrx] AGP GART is configured for kernel IOMMU, internal GART will not be used
[   65.414906] [fglrx] Internal AGP is not supported in 2.6 kernel.
[   65.415158] [fglrx:firegl_unlock] *ERROR* Process 5225 using kernel context 0

```

---

### Post by Kilz on 2006-07-30
> **kriding said:**
> it gives me 

```
[   61.494449] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   61.496014] [fglrx] Maximum main memory to use for locked dma buffers: 859 MBytes.
[   61.496232] [fglrx] module loaded - fglrx 8.27.10 [Jul 27 2006] on minor 0
[   65.414689] [fglrx] AGP GART is configured for kernel IOMMU, internal GART will not be used
[   65.414906] [fglrx] Internal AGP is not supported in 2.6 kernel.
[   65.415158] [fglrx:firegl_unlock] *ERROR* Process 5225 using kernel context 0

```

It looks like its installed, just not configured corectly. Try these commands again just to make sure, then reboot.

```
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a
```

---

### Post by kriding on 2006-07-30
did that, this is what was displayed at each step

```
sudo module-assistant prepare

Getting source for kernel version: 2.6.15-26-amd64-generic
Kernel headers available in /usr/src/linux

Done!


```

```
sudo module-assistant update

Updated infos about 70 packages


```

```
sudo module-assistant build fglrx

Extracting the package tarball, /usr/src/fglrx.tar.bz2, please wait...
Target package file
/usr/src/fglrx-kernel-2.6.15-26-amd64-generic_8.27.10-1+2.6.15-26.45_amd64.deb
already exists, not rebuilding!


```

```
sudo module-assistant install fglrx

Version 8.27.10-1+2.6.15-26.45 of fglrx-kernel-2.6.15-26-amd64-generic already installed, skipping.

```

the last command did nothing obvious, but after a short wait, the terminal went back to the normal prompt

---

### Post by kriding on 2006-07-30
oh yeah....I still have the same error message as in my original post, but when I enter 

```
dmesg | grep fglrx
```

I get nothing

---

### Post by Kilz on 2006-07-30
> **kriding said:**
> oh yeah....I still have the same error message as in my original post, but when I enter 

```
dmesg | grep fglrx
```

I get nothing

Well since we remade the modules maybe we need to finish the end of the howto, forgot to add these last time.
```

sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```
Reboot and try fglrx
If this doesnt work Im at a loss. You may want to go over the howto to get it back to where you started.

---

### Post by kriding on 2006-07-30
still no luck:( 

thanks for helping anyway mate.

---

### Post by kriding on 2006-08-06
Anyone else? I have done a fresh install of dapper 64bit, followed the howto and i still have the original error!

---

### Post by M@dMerC on 2006-08-11
yeah this sucks im getting the same error message im running an ATI Radeon 9600 Pro

---

### Post by Yuric on 2006-08-12
i am aswell. ATI Radeon 9600xt

---

### Post by Kilz on 2006-08-12
> **kriding said:**
> Anyone else? I have done a fresh install of dapper 64bit, followed the howto and i still have the original error!

A fresh install, did you try to install the drivers with [the same  howto?]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.27.10_drivers_in_Ubuntu_Dapper_Manually")

---

### Post by Kilz on 2006-08-12
I have [created a driver install script]("http://home.comcast.net/~ubuntu64user/ATI-8.27.10-install.tar.gz") in case anyone is interested.

---

### Post by Yuric on 2006-08-13
i got mine working by running 

sudo dpkg-reconfigure xserver-xorg
sudo apt-get install --reinstall libgl1-mesa

which will uninstall what you have done and then using the howto[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.27.10_drivers_in_Ubuntu_Dapper_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.27.10_drivers_in_Ubuntu_Dapper_Manually")

---

