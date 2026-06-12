---
title: "nvidia drivers"
date: 2009-03-12
forum: x86 64-bit Users
---

### Post by darkzerox on 2009-03-12
Hi guys,

Not sure which is the best forum to put this under...but I am running 64-bit... although I'm not sure if it's a 64-bit problem or not.

Anyway, I went System > Admin > Hardware Drivers and updated to the latest NVIDIA graphics drivers (177), and then it told me I had to reboot, so I did, but the xserver/gui/gnome whatever you call it, never came up. Just got the command-line. I eventually gave up fixing it and reinstalled Ubuntu again.

So, now I'm afraid to update my nvidia drivers, but my resolution is a little off, and glxgears runs at only 278 FPS when it should be running at over 8000. So I would really like to update my drivers...

Is there anyway I can, I don't know, save the system state so that I can come back to it if a driver explodes on me again? Should I even try driver 177 again, or is there another alternative?

---

### Post by norwoods on 2009-03-12
i update to the latest nvidia proprietary releases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.37 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using synaptic package manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev
for a fresh install, you might also want or need:
jockey-common
jockey-gtk or jockey-kde
nvidia-settings
nvidia-xconfig

---

### Post by philinux on 2009-03-12
I get ~3500 with compiz on and ~5000 with compiz off. Given that HD tv runs at less than 50 fps I'm not too fussed.

---

### Post by darkzerox on 2009-03-12
I installed nvidia-glx-180 and now I lost my xserver again. All I've got is the command-line...how do I fix this?

---

### Post by darkzerox on 2009-03-12
Yay for trial and error... been trolling through forums and what, didn't find anything that could help me.

removed /etc/X11/xorg.conf
then sudo apt-get removed all nvidia-180 things, and rebooted.
I'm greeted with some lovely ubuntuesque noises and what do you know...gui-goodness.

anyway, I still want newer drivers. no one else has been having this problem?

---

### Post by technobear on 2009-03-12
im having the same issue, 9800gtx superclocked evga.

ill try the config delete and see if it comes back.. 

a better/more definite driver solution would be great

---

### Post by darkzerox on 2009-03-12
damn it!

tried this too: [http://www.nvidia.com/object/linux_display_amd64_180.29.html](http://www.nvidia.com/object/linux_display_amd64_180.29.html)

that's not working either, AND I can't apt-get remove it, so now I'm really screwed.

---

### Post by darkzerox on 2009-03-13
it's not a 64-bit problem. just tried 32-bit ubuntu, tried version 177 from the hardware drivers program, and also ver 180 from avenard.

i'm on a Dell Studio XPS 13, with a GeForce 9500M graphics card... anyone know why the drivers don't want to install?

---

### Post by norwoods on 2009-03-13
> **darkzerox said:**
> it's not a 64-bit problem. just tried 32-bit ubuntu, tried version 177 from the hardware drivers program, and also ver 180 from avenard.

i'm on a Dell Studio XPS 13, with a GeForce 9500M graphics card... anyone know why the drivers don't want to install?

what all did you try to install and how did you try to install it( apt, synaptic, etc)?

---

### Post by jongkind on 2009-03-15
> **darkzerox said:**
> Hi guys,

glxgears runs at only 278 FPS when it should be running at over 8000. So I would really like to update my drivers...



How sure are you about that?

[http://qa-rockstar.livejournal.com/7869.html]("http://qa-rockstar.livejournal.com/7869.html")

---

