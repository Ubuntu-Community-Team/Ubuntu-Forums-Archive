---
title: "Default Runlevel to Install NVIDIA Driver"
date: 2008-09-01
forum: x86 64-bit Users
---

### Post by raywood on 2008-09-01
[The NVIDIA instructions]("ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/chapter-02.html") accompanying their recommended driver for my video card say, "Prior to beginning the installation, you should exit the X server and kill all OpenGL applications. ... You should also set the default run level on your system such that it will boot to a VGA console, and not directly to X."  [The accompanying details]("ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/chapter-08.html") refer to inittab, which apparently does not exist in Hardy.  How should I proceed to do what they are recommending?

---

### Post by IntuitiveNipple on 2008-09-01
You can safely ignore the inittab instructions.

Log-out of Gnome/X-server, switch to a console (Ctrl+Alt+F1), log-in, then stop Gnome:
```

sudo /etc/init.d/gdm stop

```
Change to the directory containing the Nvidia installer you've downloaded, ensure it has executable permissions:
```

chmod +x NVIDIA*.run

```
Run the installer:
```

sudo ./NVIDIAxxxxxxxxxx.run

```
Obviously, replace xxxxxxxx with the full name of the installer :)

When it has built and installed the new kernel module and libraries you should be able to restart Gnome (if you've got the Ubuntu LRM (Linux Restricted Modules) installed you might see an error report due to a bad script in /sbin/lrm-video - if that happens, ask me for how to fix it.
```

sudo /etc/init.d/gdm start

```

---

### Post by tuxxy on 2008-09-01
Have you tried any other method of installing a driver for your card?

What card are you using ?

---

### Post by raywood on 2008-09-01
IntuitiveNipple:  everything went really well, no problems -- except, would you believe, when I tried to restart GNOME, I got "No Signal" from my monitor and, shortly, no further hard drive light action.  I punched the Restart button, allowed GRUB to do a normal boot, saw the Ubuntu loading screen, but before getting to the login screen, once again, "No Signal" and then, once again, a black screen and no further action from the computer.

Tuxxy:  I think I've [tried every method]("http://raywoodcockslatest.blogspot.com/2008/08/vmware-in-ubuntu-dual-monitor-nightmare.html") there is.  I've been at this for days.  EnvyNG, reinstall a previous working setup via Acronis True Image and start over from there, etc.

---

