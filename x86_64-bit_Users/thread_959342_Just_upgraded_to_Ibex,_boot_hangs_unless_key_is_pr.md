---
title: "Just upgraded to Ibex, boot hangs unless key is pressed"
date: 2008-10-26
forum: x86 64-bit Users
---

### Post by opr8ive on 2008-10-26
Hello all..

Okay, I upgraded to Ibex last night using the update manager gui. Aside from an error in the Ubunto Studio themes (IIRC) package, it all appears to have gone correctly, except..


last good configuration was, I had the rt version of the kernel running previously (2.6.24-21-rt) in hardy, (2.6.24.21-generic ran fine too) and all was good. The update to Ibex put in both the generic, and the rt kernels for 2.6.27-7.

Okay, so heres whats going on. 

If I try to boot the 2.6.27-7-rt kernel, it hangs after grub, flashing underscore at a black screen, no love.
If I try to boot the 2.6.24-21-rt kernel (previously working great) it hangs after grub, same issue.
If I try to boot the 2.6.27-7-generic kernel, things start to go as planned... ... to a point.  When at the Ubuntu usplash screen, with the little orange doodad bouncing back and forth, the doodad suddenly stops, and the system 'freezes' there.. That is, until I hit a key (any key, in my case, I've been hitting the CapsLock button) then it will advance a bit. hit the capslock again, it'll advance more. Hold the capslock down, and it will boot through normally. 

Whiskey Tango Foxtrot, over.

-Jason

---

### Post by cariboo on 2008-10-26
There have been several people with the same problem. Have a look here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247)

To see if someone has come up with a work around.

Jim

---

### Post by inxygnuu on 2008-12-29
WORKAROUND: in menu.lst, add acpi=noirq and everything boots fine. 9for now... hope nothing happens)

```
sudo gedit /boot/grub/menu.lst
```

before:
title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1869fedd-4125-4bbc-94ff-65c782c2f77c ro quiet splash
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

after:
title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1869fedd-4125-4bbc-94ff-65c782c2f77c ro quiet splash **[COLOR="Plum"]acpi=noirq[/COLOR]**
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

---

### Post by bigrob301 on 2009-01-09
> **inxygnuu said:**
> WORKAROUND: in menu.lst, add acpi=noirq and everything boots fine. 9for now... hope nothing happens)

```
sudo gedit /boot/grub/menu.lst
```

before:
title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1869fedd-4125-4bbc-94ff-65c782c2f77c ro quiet splash
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

after:
title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1869fedd-4125-4bbc-94ff-65c782c2f77c ro quiet splash **[COLOR="Plum"]acpi=noirq[/COLOR]**
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

thanks works like a charm

---

### Post by stchman on 2009-01-09
I have never had any luck with upgrade.  I recommend a clean install as it is actually quicker.

---

### Post by Megrimn on 2009-09-02
Same thing worked for Jaunty - the "acpi=noirq" thing.

---

