---
title: "NVIDIA 9800 GTX not detected in Restricted Drivers"
date: 2008-06-21
forum: x86 64-bit Users
---

### Post by noarc on 2008-06-21
Hi!

I'm running Hardy64. I'd like to get hardware acceleration for my 9800 GTX working in Hardy, but there is nothing showing under "Hardware Drivers".

The latest 64-bit Linux NVIDIA drivers list my card as supported. But on another install I tried EnvyNG, nvidia-glx-new, the installer from nvidia.com, and nothing worked and I was left in some failsafe low-resolution mode. I tried all the guides and howtos which ultimately did nothing to recover my system.

Can someone help?

---

### Post by macaholic on 2008-06-22
Are there any errors outputted from the manual installer from nvidia's site? Also, it may be long and tedious, but do the graphics work on an ubuntu live cd?

---

### Post by Nepherte on 2008-06-22
Envy doesn't download the latest version over here but 169.12 instead. The same one as in the repos. I'd go for the manual installation of the drivers from the nvidia site. What are the errors you get when trying to install those?

---

### Post by Nullack on 2008-06-22
169.12 doesnt support your card. You will need to manually install the latest nvidia driver to get 3d support for your card.

---

### Post by noarc on 2008-06-22
The latest on NVIDIA for x86_64 is 

Version: 173.14.09
Operating System: Linux x64 (AMD64/EM64T)
Release Date: June 11, 2008

So I will try installing that (it is a newer version than when I last tried the NVIDIA installer). Question: what guide have you used succesfully to install the NVIDIA drivers? Specifically, is there anything that needs to be uninstalled first?

Thanks!

---

### Post by RAOF on 2008-06-22
You want to follow [this guide](http://wiki.ubuntu.com/NvidiaManual).  There are a couple of things you need to do to tell the system that you've manually installed the drivers, and not to mess with them.

---

### Post by veedub on 2008-06-22
Or view my post here:

[http://ubuntuforums.org/showthread.php?t=776802&page=6]("http://ubuntuforums.org/showthread.php?t=776802&page=6")

173.14.05 driver using synaptic....much easier than a manual configuration.

---

### Post by noarc on 2008-06-23
RAOF: 

First step of that guide says     

* The command lspci | grep -i nvidia prints out a line of text
* You want one or more of the following: hardware-accelerated 3D, TV-Out support, dual head support

However, my output is:

$ lspci | grep -i nvidia
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0612 (rev a2)

Will the following steps in the guide still work, even though I do not meet the prerequisites?

---

### Post by RAOF on 2008-06-23
> **noarc said:**
> RAOF: 

First step of that guide says     

* The command lspci | grep -i nvidia prints out a line of text
* You want one or more of the following: hardware-accelerated 3D, TV-Out support, dual head support

However, my output is:

$ lspci | grep -i nvidia
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0612 (rev a2)

Will the following steps in the guide still work, even though I do not meet the prerequisites?

Yes.  That output is a line of text :).

---

### Post by noarc on 2008-06-23
Doh, misread the guide, I thought that line of output had to include something about hardware-accel/tv-out/dual-head.

---

### Post by flip314 on 2008-07-17
> **veedub said:**
> Or view my post here:

[http://ubuntuforums.org/showthread.php?t=776802&page=6]("http://ubuntuforums.org/showthread.php?t=776802&page=6")

173.14.05 driver using synaptic....much easier than a manual configuration.

I too have a 9800 GTX.

I installed 173.14.09 from hardy-proposed using the guide above, but nothing is showing up in the hardware drivers section :confused:  I don't appear to have any other nvidia drivers installed (I even uninstalled nv)

Any ideas?  I'd really like to get hardware acceleration here and hopefully get the right screen resolutions without editing my xconf...

```
$ lspci | grep -i nvidia
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0612 (rev a2)

```

---

