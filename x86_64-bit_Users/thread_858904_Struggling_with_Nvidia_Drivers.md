---
title: "Struggling with Nvidia Drivers"
date: 2008-07-14
forum: x86 64-bit Users
---

### Post by Ducksgoquak on 2008-07-14
Hi guys. I've managed to install the newest nvidia driver: 173.14.09 for my card: 7800gtx but am having troubles getting compiz to work.

Kernel Infos
```
mark@mark:~$ uname -a
Linux mark 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64 GNU/Linux

```

When i do try to run compiz i get the error

```
mark@mark:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0092 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
```

so i'm thinking that my xgl is not installed/working. So i checked my synaptic package manager and xserver-xgl is not installed. However when i install it and restart the x-server i freeze up at a tan background before anything really starts and i have to hard reboot then remove xgl. 

Kind of lost at this point. I did try to install the restricted drivers via hardware manager but on reboot i froze and couldn't do anything. Next i tried envyng and ended up with the same problem. So instead i purged all of the nvidia packages and installed the newest driver from their website and can login and most everything ok(except for compiz, etc). /shrug

i'm lost :(

Edit: Attempting to use glxgears caused me to crash and i had to reinstall the driver. Upon reinstalling i got an error saying:

```

unable to create '/use/include/GL/gl.h (no such file or directory)
```

Maybe this has something to do with it also?:)

---

### Post by eric1959 on 2008-07-14
How did you install the driver for your card the first time ? Did you use the Hardware Drivers manager ?  You don't need Xgl.

It sounds like its got a bit messed up. If I were you I just started all over with a fresh install.

---

### Post by Kilz on 2008-07-14
> **eric1959 said:**
> How did you install the driver for your card the first time ? Did you use the Hardware Drivers manager ?  You don't need Xgl.

It sounds like its got a bit messed up. If I were you I just started all over with a fresh install.

Why not just install xgl? Why reinstall everything? If you dont know whay went wrong, and thats why most people reinstall everything, you stand a good chance of redoing the same mistake. Reinstalling is not a cure all.

---

### Post by Ducksgoquak on 2008-07-14
Yeah i just used the hardware manager the first time i installed... came crashing down. Then envyNG. Same results. So i installed nvidias driver from their website via the instructions on this page after using this command to get rid of the old crap
```
sudo apt-get --purge remove nvidia-glx* nvidia_settings linux_restricted_modules
``` 

[http://ubuntuforums.org/showthread.php?p=5382269#post5382269](http://ubuntuforums.org/showthread.php?p=5382269#post5382269)

that i posted (post #23)

i'm sure it's possible i got rid of something i needed from that purge command. Sorry i'm definitely still a newb.. .but learning!

Edit: oh and installing xserver-xgl from synaptic caused me to crash too:( i'm almost beginning to think it's my video card.

---

### Post by philinux on 2008-07-14
Installing this **xserver-xgl** borks x.

According to some nvidia doesn't need xgl. Some say it does. But if you install xgl it don't work. :confused:

If you google **ubuntu nvidia xgl** there are a loads of stuff about this. Which one is right I've no idea.

My system is running compiz smoothly with the default nvidia-glx-new driver, so I'm going with the nah camp for now. I'm getting 5000 fps from glxgears if that means anything.

---

### Post by legatoistheman on 2008-07-15
I am having a similar problem with the same card i have two 7800 gtx's that were running in sli, that is until i used updated manager earlier today and updated both the kernel and the nvidia driver.  

Used envy ng to redownload latest driver, dont think it quite worked. What happens is that when i check hardware drivers i see that the icon is green and it says the nvidia drivers are in use, but the box is not checked stating that the driver is enabled. when i check the box to enable and restart x or reboot x will not boot up and then i have to reboot into safe mode and reconfigure x, then all is well again.  

I am a real newbie to these sort of things and i try, but i have no idea what im doing and how i would even begin to fix this.

Any Suggestions?

---

