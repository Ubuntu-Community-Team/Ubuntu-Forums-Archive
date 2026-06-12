---
title: "Software interrupt causes 50%+ cpu usage"
date: 2005-06-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by UrbanFallout on 2005-06-25
Hi

I've just installed Hoary Ubuntu amd-64 onto a new Acer Aspire laptop: Turion TL34, 1GB Ram, 100GB HDD, ATI Radeon X700. Swap partition is 1.5GB. Ram usage 

Everything works, however the CPU always 50% or higher due to software interrupts. A cut paste from top is given below:
Cpu(s):  3.0% us,  0.7% sy,  0.0% ni, 43.0% id,  2.3% wa,  0.0% hi, 51.0% si
Mem:   1023764k total,   485348k used,   538416k free,    50748k buffers
Swap:  1534136k total,        0k used,  1534136k free,   156548k cached

As shown cpu usage by deamons and apps is fairly low, as is memory usage.

This also seems to slow the system down somewhat, especially when I read the Hard-disk. 

Knoppix does not exhibit this effect.

Any ideas?

Thanks in advance
Nick

---

### Post by tseliot on 2005-06-25
I had the same problem. You should install kernel 2.6.12. You can compile it  or install it from synaptic after havingbreezy repositories  added to your "sources.list". However someone thinks we shouldn't use breezy repositories (but this did the trick for me and didn't cause me any trouble).

Then you should follow these exact instruction (please don't skip any step otherwise it won't work)

1) open Terminal (or Konsole) (the command line) and prompt:
 sudo gedit /boot/grub/menu.lst (or if you use KDE put kate instead of gedit, or nano if you haven't both of  them)

look for these lines

## ## Start Default Options ## ## default kernel options ## default kernel options for automagic boot options ## If you want special options for specifiv kernels use kopt_x_y_z ## where x.y.z is kernel version. Minor versions can be omitted. ## e.g. kopt=root=/dev/hda1 ro # kopt=root=/dev/hda2 ro console=tty0 no_timer_check 

2) Add add no_timer_check in the kopt line (exactly where you see it in the example above, leave the rest as it is in your file)

3) Save the document and restart your computer

4) After you have restarted your computer open Terminal (or Konsole) and prompt:

sudo update-grub

5) restart your computer again

Tell me if it works for you

---

### Post by UrbanFallout on 2005-06-26
Thankyou very much. Your advice worked like charm.
It was a little more complicated than I expected so I'll outline my steps here:

1. added the no_timer_check as per your advice above. 
(I know This should have been done last - but I was experimenting, this gave me a substantial speed increase although I was still getting 50% cpu usage by the software interrupt)

2. use synaptic package manager to install kernel-package

3. use synaptic package manager to install kernel 2.6.10-k8 
(This was simply to get the kernel compilation configuration for when I compiled 2.6.12)
2a. Reboot (Got even more of a speedup)

4. Download kernel 2.6.12 from kernel.org 
(In fact breezy did not have kernel 2.6.12 - only kernel 2.6.11 - which I tried and didn't work - maybe I had the wrong repository names...)

5. Untarballed the image and went to its directory and created a debian package as per the instructions at [http://newbiedoc.sourceforge.net/system/kernel-pkg.html](http://newbiedoc.sourceforge.net/system/kernel-pkg.html)
 (I just did a vanilla install) i.e.
5a. cd /untarredDirectory
5b. cp /boot/config-2.6.10-5-amd64-k8 .config
5c. sudo make-kpkg --append-to-version=.050627 kernel_image
(This takes quite a while)
5d. dpkg -i kernel-image-2.6.12.1-amd64-k8_20050627.1_amd64.deb
5e. Reboot

6. Viola - no more 50% cpu usage.

Thank again
Nick

---

### Post by NickB on 2005-06-26
You probably didn't get far enough along to notice a host of other problems this solved:

* clock running 2x fast
* multimedia/video unable to sync
* anything using SDL fubared

...and more.  Just a friendly warning if anyone decides the 50% CPU reporting is only a minor inconvenience to them ;)

Nick

---

### Post by DAVIUR on 2005-08-17
[QUOTE=UrbanFallout]Thankyou very much. Your advice worked like charm.
It was a little more complicated than I expected so I'll outline my steps here:

1. added the no_timer_check as per your advice above. 
(I know This should have been done last - but I was experimenting, this gave me a substantial speed increase although I was still getting 50% cpu usage by the software interrupt)

2. use synaptic package manager to install kernel-package

3. use synaptic package manager to install kernel 2.6.10-k8 
(This was simply to get the kernel compilation configuration for when I compiled 2.6.12)
2a. Reboot (Got even more of a speedup)

4. Download kernel 2.6.12 from kernel.org 
(In fact breezy did not have kernel 2.6.12 - only kernel 2.6.11 - which I tried and didn't work - maybe I had the wrong repository names...)

5. Untarballed the image and went to its directory and created a debian package as per the instructions at [http://newbiedoc.sourceforge.net/system/kernel-pkg.html](http://newbiedoc.sourceforge.net/system/kernel-pkg.html)
 (I just did a vanilla install) i.e.
5a. cd /untarredDirectory
5b. cp /boot/config-2.6.10-5-amd64-k8 .config
5c. sudo make-kpkg --append-to-version=.050627 kernel_image
(This takes quite a while)
5d. dpkg -i kernel-image-2.6.12.1-amd64-k8_20050627.1_amd64.deb
5e. Reboot

6. Viola - no more 50% cpu usage.

Thank again
Nick[/QUOTE]


Hi UrbanFallout...

is it possible that you could let me see your kernel config (.config)? i am trying to boot after i have exactly done what you wrote, but i am having a kernel panic... 

thanks...
David

---

### Post by DancingSun on 2005-08-17
How come I'm not getting this problem?  Is this limited to laptops?  Maybe this has to do with powernowd?

---

### Post by tseliot on 2005-08-18
[QUOTE=DAVIUR]Hi UrbanFallout...

is it possible that you could let me see your kernel config (.config)? i am trying to boot after i have exactly done what you wrote, but i am having a kernel panic... 

thanks...
David[/QUOTE]

Please, follow my easy guide about Kernel compiling:

[http://www.ubuntuforums.org/showthread.php?t=56835](http://www.ubuntuforums.org/showthread.php?t=56835) 

Tell me if it works for you.

UPDATE: and this is my (complete) guide to solve the double clock speed problem

[http://ubuntuforums.org/showthread.php?t=53094](http://ubuntuforums.org/showthread.php?t=53094)

---

### Post by tseliot on 2005-08-18
[QUOTE=DancingSun]How come I'm not getting this problem?  Is this limited to laptops?  Maybe this has to do with powernowd?[/QUOTE]

I think it depends on your motherboard (actually it depends on how supported your motherboard is by Linux kernels. This is a common Bug.). What's yours?

---

### Post by DancingSun on 2005-08-18
[QUOTE=tseliot]I think it depends on your motherboard (actually it depends on how supported your motherboard is by Linux kernels. This is a common Bug.). What's yours?[/QUOTE]
Chaintech VNF4 Ultra (nForce4 Ultra based).

---

### Post by tseliot on 2005-08-18
[QUOTE=DancingSun]Chaintech VNF4 Ultra (nForce4 Ultra based).[/QUOTE]

Lucky you, this bug is real pain in the neck. The trick works with 64bit kernels ONLY.  32bit kernels require a patch. I remember only PCLinuxOS had a patched kernel by default. I will ask in their forums which kernel patch or settings they use. I'm planning to dual boot Ubuntu 64 and PClinuxOS 32 when I have my computer back from repairings. If I find a way to patch the kernel or the exact settings I'll post them in this forum.

---

### Post by DancingSun on 2005-08-18
For those of you that are having this problem, what motherboards do you guys have?

---

### Post by tseliot on 2005-08-18
Mine is MSI RS480

---

### Post by DAVIUR on 2005-08-18
[QUOTE=tseliot]Please, follow my easy guide about Kernel compiling:

[http://www.ubuntuforums.org/showthread.php?t=56835](http://www.ubuntuforums.org/showthread.php?t=56835) 

Tell me if it works for you.

UPDATE: and this is my (complete) guide to solve the double clock speed problem

[http://ubuntuforums.org/showthread.php?t=53094](http://ubuntuforums.org/showthread.php?t=53094)[/QUOTE]
 Wow it works! finally my laptop booted!!

Thanks thanks tseliot! Having disable "Enable DMA only for disks" works like charm, I did not know anything about that....

David

---

### Post by tseliot on 2005-08-19
[QUOTE=DAVIUR]Wow it works! finally my laptop booted!!

Thanks thanks tseliot! Having disable "Enable DMA only for disks" works like charm, I did not know anything about that....

David[/QUOTE]
I'm glad my guides helped you.  :)

---

