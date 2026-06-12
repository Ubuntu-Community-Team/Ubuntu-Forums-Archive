---
title: "Ubuntu 7.04 will not install on AMD FX-51"
date: 2007-06-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by frankthechicken on 2007-06-14
I have an AMD FX-51 processor, and I tried upgrading to the latest Ubuntu x86-64, however I am now greeted with a blank screen(no video through put, montior switches off).  I have attempted a reinstallation using the live-cd, however  the same problem persists shortly after it attempts to load the kernel.  This is also occuring on any other distro (well opensuse 10.3 Alpha 64)  I use (presumably any that use the newest kernel).

I am relatively new to Linux, so if I have worded anything incorrectly, I apologise.  I am now downloading the non 64 bit version to see if I get the same problems.

Any help would be greatly appreciated, and I can supply any further info if needed).

I apologise if this has already been raised, but I had a quick search and could not find anything similar.

---

### Post by Jouke74 on 2007-06-14
Did you try to start using the recovery mode? 

If this shows a login prompt, use your inlog name and password. If this is working then you probably need to reconfigure your (graphical) X server with the command: 

sudo dpkg-reconfigure xserver-xorg 

Then type the root password and continue until done.

type reboot

Check if it's working now.

---

### Post by Cappy on 2007-06-14
Try booting with kernel option
```
nosplash
```

If that doesn't work try kernel option
```
noapic acpi=off
```

I would try Jouke's suggestion first.
By the way though, if you are in recovery mode it is just 
```
dpkg-reconfigure xserver-xorg
```
you don't use sudo.
Generally, you might want to try changing the video driver (it's the first option when reconfiguring) to "vesa". If you have a nvidia card and it is detected you should be able to use "nv". If you have an ati card and it is detected you should be able to use "ati".

---

### Post by frankthechicken on 2007-06-14
Many thanks, the nosplash, in combination with the command line install worked.  

Any idea why this is happening, as it seems to happen on a number of the new distros?

It seems I'm going to have to edit grub with each kernel update, which although only slightly annoying, is annoying nonetheless.

Anyway, thanks again for the quick input.

---

### Post by Cappy on 2007-06-14
I'm not sure. The answer is probably somewhere in the bug report thread.
[https://bugs.launchpad.net/ubuntu/+bug/86666](https://bugs.launchpad.net/ubuntu/+bug/86666)

---

### Post by frankthechicken on 2007-06-15
OK, thanks again for that.

I'm now having a second problem, one that is most likely related to the first.

On logging out/restart/turning off I get exactly the same problems as I was having on booting, i.e. hard crash, no video output, are there any similar solutions?

---

### Post by Cappy on 2007-06-15
Yes. The solution is to take any "vga=" lines off of the kernel line while keeping either "nosplash" or removing "splash". Having a "vga=" section causes the crash you are referring to.

---

### Post by frankthechicken on 2007-06-15
I'm not quite sure what you mean, but in grub I have no vga=, only[PHP]title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=72d59134-108c-426b-b867-da8d0842a8a0 ro quiet
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault[/PHP]

---

### Post by Cappy on 2007-06-15
Ah so you don't have the "VGA=" line in there. It must be something else then.

When you look in ```
sudo nano /etc/usplash.conf
```
do you have this:
```

# Usplash configuration file
xres=1024
yres=768

```
?

You may want to try putting "vga=792" on the end of your boot line and try it both with and without the "splash" parameter.

In the bug report it was only crashing on shutdown if they had the VGA line so it is upto trial and error.

---

### Post by frankthechicken on 2007-06-15
Thanks for the reply.

In usplash.conf I had the values of xres=1680 and yres=1680, I tried changing these to 1024, 768 and then all combinations of splash, vga=792, with no success, then switched back to my initial usplash.conf values, again with no success.  

It would only boot without any of the parameters. 

When I left vga=792 in, it would boot right up to login then crash hard.  However with all changes, when it did boot, it would still crash on logging out.

---

### Post by Cappy on 2007-06-15
So the usplash.conf change + just having no "splash" line on the kernel didn't fix it? That's a shame =( Unfortunately, those are the only 3 things I saw in the bug report.

---

### Post by frankthechicken on 2007-06-15
Unfortunately not, maybe I'll give the 386 version a go.

But thanks for all the help, it was greatly appreciated

---

