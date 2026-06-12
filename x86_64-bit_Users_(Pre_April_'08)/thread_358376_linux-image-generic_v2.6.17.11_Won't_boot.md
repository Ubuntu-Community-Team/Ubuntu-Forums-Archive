---
title: "linux-image-generic v2.6.17.11 Won't boot"
date: 2007-02-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by Crypto-138 on 2007-02-10
For some reason, when I updated my system, and booted up the latest Kernel, I got strange errors, about the Usplash and something about /sbin/.
I reinstalled it, but that didn't fix it.
I don't exactly know how I can get logs of this, but the error is something like:
> cannot find /sbin/usplash_write
Maybe it has to do with the Ubuntu Splash screen?

I'm running Edgy on a 64-bit AMD Athlon Processor.

---

### Post by ANTDx1 on 2007-02-11
I've had trouble with 2.6.17.11 too.  .10 worked just fine, and 2.6.18.1 also works fine.  However, both 17.11 and 18.5 seem to fail, wtih 18.5 messing up my 3d graphics acceleration, and 17.11 messing up 3d graphics, and making it so that the top bar with my applications, places, and admin menus doesn't even show up.  I guess I'll be on 18.1 for awhile and hope that an upgrade to Feisty in April won't kill too many things.

---

### Post by Crypto-138 on 2007-02-12
I updated the information on the first post. I hope I'm not the only one with this problem, because I have no idea if something's wrong with my computer or if I'm using the wrong kernel

---

### Post by bender5788 on 2007-02-12
all  mine did was make it so i could not possibly set up an xserver (trust me i tried) so all i did was boot back in to my 17.10 kernel and remove the 17.11 kernel from the boot menu i may try it again when it appears stable.

---

### Post by slowcoach on 2007-02-12
nvidia-glx is incompatible with the new kernel, that's the bad news... the good news is that the proprietary nvidia drivers now work perfectly with the new kernel.
To fix the problem reboot and press Esc at the Grub menu, select the old kernel, that will get you into xserver, next edit /etc/X11/xorg.conf changing nvidia to nv, reboot and this time choose the new kernel at the Grub menu, now you can run envy against the new kernel.  Fixed.

---

### Post by s_spiff on 2007-02-13
What about non server installations? I had this problem after installing the driver for nvidia i ended up with a blue screen saying X loading failed. I had this on Dapper Drake, now before I do a fresh install of Edgy, I thought I'll ask. Btw, I'm on a 64bit iDNa series motherboard with Nvidia Geforce 6200 onboard graphic card. Any precautions before I install the driver?

---

### Post by PatrynXX on 2007-02-13
Whatever's going on it ain't kewl.  The new update gives me an unknown inturrupt or failure in the terminal before Ubuntu even launches.  By mistake I figured out how to go from GRP then typing Exit and it lanches there.  How can I fix this then?  :( :confused:

---

### Post by emakris on 2007-02-13
I'm having the same issue with a no boot. I don't know what happened. If you find out anything or fix it, can you update the thread?
I'm really wishing I hadn't updated the kernel at this point :(

Thanks
Ernie

---

### Post by slowcoach on 2007-02-13
> **s_spiff said:**
> What about non server installations? I had this problem after installing the driver for nvidia i ended up with a blue screen saying X loading failed. I had this on Dapper Drake, now before I do a fresh install of Edgy, I thought I'll ask. Btw, I'm on a 64bit iDNa series motherboard with Nvidia Geforce 6200 onboard graphic card. Any precautions before I install the driver?
I'm using a PCI GeForce 6200 card myself. Re-installing the nvidia-glx package fails to load xserver at boot so use Envy instead [http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717) magic!

---

### Post by PatrynXX on 2007-02-20
> **slowcoach said:**
> I'm using a PCI GeForce 6200 card myself. Re-installing the nvidia-glx package fails to load xserver at boot so use Envy instead [http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717) magic!

Tried this, but after restart get the same unknown interrupt or failure.  Have to continually use the GRP option for 2.6.17.10 recovery mode.  :(

---

### Post by t_anjan on 2007-02-21
When the Ubuntu update manager updated my kernel to 17.11, I was still using the "nv" driver, i.e. the drivers that came with the OS. After logging on to the new kernel, I then used Alberto Milone's "Ubuntu's Bleeding Edge Driver" repository to install the latest nvidia driver. Everything works fine.

For more info about updating to the latest nvidia driver via Synaptic, go here: [http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

