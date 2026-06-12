---
title: "Installing Starcraft Basic Help"
date: 2008-07-02
forum: Wine
---

### Post by zalberico on 2008-07-02
I'm trying to install starcraft with the expansion pack through wine in ubuntu 8.04.  I've had no prior experience or success with wine so any help would be great.

I'm trying to follow the how to located here:
[http://danmarner.blogspot.com/2008/05/starcraft-brood-war-on-ubuntu-hardy.html](http://danmarner.blogspot.com/2008/05/starcraft-brood-war-on-ubuntu-hardy.html)

First I noticed that my cdrom0 was not located in /dev/cdrom0 but rather /media/cdrom0.  I continued to follow the instructions with that difference and right at the beginning when it said to create the .iso I did so but the .iso that was copied to my desktop is 0 bytes.

I think I'm doing it wrong.

Anyone who has had success doing this please let me know.

thanks

---

### Post by cogadh on 2008-07-02
Skip the whole disk image thing, it is unecessary and a waste of time. Just put the CD in the drive, let it mount, then run the install like this (adjust the "setup.exe" name as necessary):
```
wine /media/cdrom/setup.exe
```
Just a note, "/media/cdrom" is symlinked to "/media/cdrom0", so they are interchangable.

---

### Post by zalberico on 2008-07-02
ok I did that and installed it, however it will not actually let me play the game

when i go to open it it'll open for a second in the bottom gnome panel and then immediately close:

preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:advapi:SetSecurityInfo stub
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  148 (GLX)
  Minor opcode of failed request:  16 (X_GLXVendorPrivate)
  Serial number of failed request:  548
  Current serial number in output stream:  549

That's my output

---

### Post by zalberico on 2008-07-02
Apparently this is a bug in wine due to some new kernel upgrades or something.  

I cam across this work around:
sudo sysctl -w vm.mmap_min_addr=0

located here:
[https://bugs.launchpad.net/ubuntu/+source/wine/+bug/114025](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/114025)

I'm now getting a different error message, at least that's something.
X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  148 (GLX)
  Minor opcode of failed request:  16 (X_GLXVendorPrivate)
  Serial number of failed request:  548
  Current serial number in output stream:  549

Not quite sure what that means
I'll try to find out

---

### Post by zalberico on 2008-07-02
Well I don't have direct rendering enabled, but compiz fusion is running fine.

Does anyone know how to enable direct rendering for the Intel X3100?

I'm I wasting my time trying to get starcraft and warcraft III to work with this card?

Anyone else able to do it?

Thanks

---

### Post by cogadh on 2008-07-02
Turn off Compiz, Wine won't run 3D games properly if Compiz is running. It will sometimes also interfere with the Direct Rendering reporting.

---

### Post by zalberico on 2008-07-02
Thank you I will try that

---

### Post by zalberico on 2008-07-03
After doing more research I've found that it's hopeless for me because of my intel open source driver.  That is why I'm getting that output.

Someone else figured out how to play tibia [some rpg] even though they experienced the same problems; if you're in my position and you see this maybe there is something in there that can help, more likely not.

While I won't use it, unfortunately windows remains the obvious gaming machine

It isn't gnulinux's fault, it's the fact that there does not exist a satisfactory driver for the Intel X3100 that can have direct rendering and play simple games like starcraft.

UNSOLVED.<for now>

---

