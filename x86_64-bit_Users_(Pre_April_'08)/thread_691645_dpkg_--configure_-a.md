---
title: "dpkg --configure -a"
date: 2008-02-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by arthyko on 2008-02-08
I got this error:

richi@AMD:~$ sudo apt-get install -f
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
richi@AMD:~$ sudo dpkg --configure -a
Configurando initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Configurando linux-image-2.6.22-14-generic (2.6.22-14.51) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
Failed to create initrd image.
dpkg: error al procesar linux-image-2.6.22-14-generic (--configure):
 el subproceso post-installation script devolvió el código de salida de error 2
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: el subproceso post-installation script devolvió el código de salida de error 1
richi@AMD:~$ 

**Can you help me to fix this problem?**

---

### Post by JoshuaRL on 2008-02-08
Try:

```

gksu synaptic

```

and then go into the broken filter and see if you can reinstall.  If not, you might need to remove and reinstall.  If it's something that may break Xorg, make sure you write down what it is so you can use apt-get from the terminal.

---

