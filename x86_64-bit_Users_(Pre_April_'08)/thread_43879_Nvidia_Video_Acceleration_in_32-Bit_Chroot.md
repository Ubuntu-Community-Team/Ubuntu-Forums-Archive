---
title: "Nvidia Video Acceleration in 32-Bit Chroot"
date: 2005-06-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by joekr on 2005-06-23
Hey all,

I followed the clear and concise [32-Bit chroot instructions](http://ubuntuforums.org/showpost.php?p=119679&postcount=1) to setup my chroot.

I'm running Firefox32 and Flash and all that wonderful stuff in my chroot successfully!

**Now I want to install Cedega into my chroot.**  The truth is I already have installed Cedega and the HL2 demo :D  However Cedega isn't using hardware acceleration... it's using ```
libGL.so.1 => /usr/X11R6/lib/libGL.so.1 (0x55602000)
```

In my native (AMD64) environment I have Nvidia-glx installed (ver 7174 from Synaptic) and the drivers are working great for native games :D

How would I go about adding hardware acceleration to my chroot?

Thanks in advance

joe

---

### Post by AndersAA on 2005-06-23
install the exact same driver version in chroot and it should work fine.

---

### Post by joekr on 2005-06-23
[QUOTE=AndersAA]install the exact same driver version in chroot and it should work fine.[/QUOTE]

If you are suggesting to install Nvidia-glx-7174 via synaptic 32, I must add that I've tried this **numerous** times, however, always receive an error... I'll go ahead and give it another try if only to post the error I receive...

EDIT:

After selecting 'nvidia-glx' in Synaptic32 and agreeing to it's dependencies, I get the following error after download and installation:

```
E: linux-image-2.6.10-5-386:  subprocess post-installation script returned error exit status 2
E: linux-restricted-modules-2.6.10-5-386:  dependency problems - leaving unconfigured
E: nvidia-glx:  dependency problems - leaving unconfigured

```

Is there a special way to install the exact same drivers in the chroot?

---

### Post by AndersAA on 2005-06-23
the reason for this is it's failing to install linux-image, because /etc/fstab isn't set up.

You could install it manually in chroot (from nvidia's website), that's what I did anyway, and that works fine.  Or you could modify /etc/fstab so mkinitrd can find root properly.

---

### Post by joekr on 2005-06-23
Thanks for responding...

By 'manually installing', do you mean to run **sudo sh NVIDIA-Linux-x86-1.0-7174-pkg1.run** ?

Or do I add '--extract-only' and copy the files one by one to their respective directories?

---

### Post by joekr on 2005-06-23
Thanks, I went ahead and manually copied over the contents of the pkg1.run file after issuing the --extract-only variable...

It works like a charm now :D

---

### Post by ngolian on 2005-07-11
I haven't tried this myself, but I noticed the 64-bit package installs libraries in /usr/lib32. So maybe if you made sure that was accessible from within the chroot and gave it a high priority in the chroot's /etc/ld.so.conf, that would work as well?

---

### Post by Jet2k5 on 2005-07-11
Sorry I'm confused here.  For one I thought that you can run Cedega on 64-bit?  From the link [here](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#How_to_install_Cedega_on_AMD64)
 I thought this was going to be possible.  Also the nvidia drivers are for 64-bit too?  

Why would you want to run cedega in 32-bit mode when you can do it on 64-bit mode.  Or is it like all the 32 bit apps and 64-bit they just suck?

---

### Post by AndersAA on 2005-07-12
[QUOTE=Jet2k5]Sorry I'm confused here.  For one I thought that you can run Cedega on 64-bit?  From the link [here](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#How_to_install_Cedega_on_AMD64)
 I thought this was going to be possible.  Also the nvidia drivers are for 64-bit too?  

Why would you want to run cedega in 32-bit mode when you can do it on 64-bit mode.  Or is it like all the 32 bit apps and 64-bit they just suck?[/QUOTE]


first of all, no, you can not run cedega in "64 bit", you CAN run it on a 64bit system, without chroot, but it would be running 32bit on your 64bit system (if you compile it for a 64bit system it'd probably be able to run windows 64bit programs, but not windows 32bit programs).

---

### Post by Jet2k5 on 2005-07-12
So if you can run it on 64-bit system, then what is the point of running it in chroot?

---

### Post by puiphooey on 2005-10-12
Don't know of how much use this will be to you, but here goes.

I use an ATI Graphics card. Upon completing all the steps including /dev to my fstab, I switched to the ATI drivers. The chroot ceased working, complained that it was being denied a connection. So I changed do_chroot to this:
> #!/bin/sh

xhost + local:
/usr/bin/dchroot -d "`echo $0 | sed 's|^.*/||'` $*"

Still no luck. Then I installed ubuntu-desktop through synaptic32 and voila, 3d graphics acceleration. Hope this helps.

---

### Post by queenorych on 2006-01-27
[QUOTE=AndersAA]the reason for this is it's failing to install linux-image, because /etc/fstab isn't set up.

You could install it manually in chroot (from nvidia's website), that's what I did anyway, and that works fine.  Or you could modify /etc/fstab so mkinitrd can find root properly.[/QUOTE]

How does one go about setting up /etc/fstab in the chroot so mkinitrd can find root properly?

---

### Post by Alabama_Man on 2006-01-27
With my ATI-card i installed the same drivers in chroot like in my normal enviroment. Then i had to activate shared memory by typing in chroot
```
sudo mount /dev/shm/
```
I also added something to the fstab in chroot, but this doesnt seems to work

---

