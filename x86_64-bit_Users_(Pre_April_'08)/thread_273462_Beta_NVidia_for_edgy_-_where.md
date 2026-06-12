---
title: "Beta NVidia for edgy - where?"
date: 2006-10-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by jbernardo on 2006-10-08
Hello,
As anyone got a repo with the updated (release 9625) nvidia drivers for edgy? I've tried the recommended way in some howto's, removing nvidia-glx before installing the new drivers, but that just broke my system, attempting to remove all xorg stuff and kubuntu-desktop. If I leave the current nvidia-glx and install the new drivers using nvidia script, I'm sure I'll get breakeage in the future when the kernel is updated and the "old" version modules get reinstalled.

I've tried just downloading nvidia-glx "source", but that got me a 90+MB jumble of linux-restricted-drivers, and I've yet to make my way around it to have it build nvidia-glx using driver v9625.

As anyone already done this, and can give me some pointers on how to go (since "fakeroot debian.binary/rules binary" in nvidia directory in restricted-drivers won't work)? Or is there a amd-64 repository with the latest nvidia drivers?

Thank you!

---

### Post by russianpirate on 2006-10-08
AMD64: [http://download.nvidia.com/XFree86/Linux-x86_64/1.0-9625/NVIDIA-Linux-x86_64-1.0-9625-pkg2.run](http://download.nvidia.com/XFree86/Linux-x86_64/1.0-9625/NVIDIA-Linux-x86_64-1.0-9625-pkg2.run)
x86: [http://download.nvidia.com/XFree86/Linux-x86/1.0-9625/NVIDIA-Linux-x86-1.0-9625-pkg1.run](http://download.nvidia.com/XFree86/Linux-x86/1.0-9625/NVIDIA-Linux-x86-1.0-9625-pkg1.run)

---

### Post by jbernardo on 2006-10-08
Thanks, but those files I've got them already. What I wanted was to have them packaged as nvidia-glx and linux-restricted-modules, or a way/script on how to do that starting from the existing "source" package.

---

### Post by russianpirate on 2006-10-08
why?

just run those files as root (make sure u have libc-dev, linux-headers-`uname -r` installed first..) and make sure u dont have any other nvidia drivers installed

---

### Post by jbernardo on 2006-10-08
> **jbernardo said:**
> Hello,
As anyone got a repo with the updated (release 9625) nvidia drivers for edgy? I've tried the recommended way in some howto's, removing nvidia-glx before installing the new drivers, but that just broke my system, attempting to remove all xorg stuff and kubuntu-desktop. If I leave the current nvidia-glx and install the new drivers using nvidia script, I'm sure I'll get breakeage in the future when the kernel is updated and the "old" version modules get reinstalled.

Here is why - as I stated, making sure I don't have other nvidia drivers installed breaks my kubuntu install. Also, I like having things "controlled" - keeping the number of extraneous files to a minimum. If I can install something in a way that can be removed by the distro package manager, I'd rather to it that way than installing in a non-standard way, that will make it hard to update/remove in the future.

---

### Post by patrickfromspain on 2006-10-08
run the install from the files from the nvidia site, you just have to remove the restricted-modules packages.

Also, to update the drivers you would just have to reinstall the new version from the nvidia site or reinstall the restricted-modules package.

---

### Post by kleeman on 2006-10-08
> **jbernardo said:**
> Here is why - as I stated, making sure I don't have other nvidia drivers installed breaks my kubuntu install. Also, I like having things "controlled" - keeping the number of extraneous files to a minimum. If I can install something in a way that can be removed by the distro package manager, I'd rather to it that way than installing in a non-standard way, that will make it hard to update/remove in the future.
True that would be ideal but these drivers are beta software and if you look on the nvidia linux forum you will see that many users are reporting problems with the new driver. So it is not stable yet meaning that the developers (or others) do not wish to package it. FWIW I needed to install these drivers by tseliots method 2) (see elesewhere in the forum) and they work very nicely on my 64 bit install. When I come to upgrade I will follow tseliots guide for uninstalling and then put the original packages back in place.

---

### Post by jbernardo on 2006-10-08
Removing the restricted-modules package only manages to break everything too. Aptitude just wants to downgrade my kernel to the dapper version and install those restricted modules, apt tries to remove everything...
I guess I'll just wait.
I just asked for a repository for the beta drivers as I see that (on the beryl howto) there are repositories for them for x86. And if I manage to find out how to build the nvida-glx and linux-restricted-modules packages, I might try to update those for the x86-64, at least for my own use.

---

### Post by SlCKB0Y on 2006-10-08
> **jbernardo said:**
> Aptitude just wants to downgrade my kernel to the dapper version and install those restricted modules, apt tries to remove everything...

Ummm. Id say you have some configuration with you system. Possibly PEBKAC.

---

### Post by RAOF on 2006-10-09
For the record, you don't need to remove linux-restricted-modules, just nvidia-glx.

Also, wouldn't the Edgy forum have been a more appropriate place to post this?

As far as I know, no-one has packaged the new nVidia drivers (and associated l-r-m) for x86-64, although I'm hosting the vanila (freedesktop.org) compiz builds.

---

### Post by jbernardo on 2006-10-09
Probably PEBCAK, as my amd64 machine was updated from dapper to edgy with probably some extranous packages in the mix, so I might have broken something or added some strange dependencies. All I know know is that trying to remove linux-restricted-modules or nvidia-glx tries to remove a lot of other stuff that should stay put... Next weekend I'll see if I can build linux-restricted-modules and nvidia-glx from "source" (apt-get source) with the new versions, or if I can persuade xorg-server to stay put if I add another driver.
Thanks guys.

---

### Post by RAOF on 2006-10-09
> **jbernardo said:**
> ...or if I can persuade xorg-server to stay put if I add another driver.
Thanks guys.

Oh, have you removed **all** the other xorg-video drivers?  Then, yes, you will need to install at least one in order to satisfy the xorg dependency on having a video driver :P

---

### Post by jbernardo on 2006-10-11
I hadn't removed the other xserver-xorg-* drivers. I now tried removing nvidia-glx with adept_manager, and it was the only thing removed. I then followed method 2, got the driver to install, but now it hangs with a blank screen (and the remedies from the howto don't work). The last lines in /var/log/Xorg.0.log are from the nvidia driver, and disabling glx doesn't help, it hangs the same way. I guess I'll have to give up on the latest and greatest stuff for now.

The end of Xorg.0.log with GLX enabled:
```
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "UseEdidFreqs" "False"
(**) NVIDIA(0): Option "Coolbits" "1"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "true"
(**) NVIDIA(0): Option "DisableGLXRootClipping" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     disabled on all display devices.
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.

```

And with it disabled:
```
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "UseEdidFreqs" "False"
(**) NVIDIA(0): Option "Coolbits" "1"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     disabled on all display devices.
(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.

```

---

### Post by rplantz on 2006-11-01
> **jbernardo said:**
> I guess I'll have to give up on the latest and greatest stuff for now.

I find it a bit weird that we buy the latest and greatest CPU but cannot run the l & g software.

Ironically, I think it's the backwards compatibility of the x86-64 that has caused this problem. If it would not run x86-32 code, developers would be upgrading to 64-bit much faster.

---

### Post by tseliot on 2006-11-01
My Unstable repositories include the Nvidia Beta driver:
[http://ubuntuforums.org/showthread.php?t=255929](http://ubuntuforums.org/showthread.php?t=255929)

---

