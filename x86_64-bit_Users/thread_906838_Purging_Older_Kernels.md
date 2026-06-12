---
title: "Purging Older Kernels"
date: 2008-08-31
forum: x86 64-bit Users
---

### Post by TimothyLuke on 2008-08-31
Hi All,

Newb question - How do I purge older kernels?

I installed via a Server CD as I could not use the Live or alternate CD's to install, then installed ubuntu-desktop for 7.10.  After that I upgraded to 8.04 and it converted my server kernels to ordinary desktop kernels of which I was happy at.  I now have a list of about 10-15 kernels all of different versions that are sitting in my grub menu.  How can I safely purge the older ones leaving the latest 1 or 2?

---

### Post by aheckler on 2008-08-31
Search Synaptic for "linux-image" and delete old versions, but be careful, as always.

---

### Post by james_vanb on 2008-08-31
To remove old kernel options from your grub list:

```
sudo gedit /boot/grub/menu.lst
```

After - ## ## End Default Options ## - you will see all the kernel versions listed as well as dual boot options (If you are using dual boot) - Delete the kernel versions you don't want to see anymore.  I keep the current and the last (Just in case there is problem with the new kernel and I have to boot into the old) along with recovery mode as well as the memory test.  Mine looks like this:

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=22930e3e-d2fb-4970-957c-6e70a268019a ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=22930e3e-d2fb-4970-957c-6e70a268019a ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=22930e3e-d2fb-4970-957c-6e70a268019a ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=22930e3e-d2fb-4970-957c-6e70a268019a ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Kilz on 2008-09-01
If you uninstall the linux-image in synaptic you will not have to edit the menu.list. It will automatically remove them from it. Editing it does not remove them from your system but only hides them from the boot list. You can also make your system unbootable if you make a mistake.
I also recommend leaving 2 kernels in place, because if you get a bad upgrade (it has happened) you can boot into the older one that works.

---

### Post by Oldsoldier2003 on 2008-09-01
> **Kilz said:**
> If you uninstall the linux-image in synaptic you will not have to edit the menu.list. It will automatically remove them from it. Editing it does not remove them from your system but only hides them from the boot list.
I also recommend leaving 2 kernels in place, because if you get a bad upgrade (it has happened) you can boot into the older one that works.

+1 

very sound advice. I always leave at least 2 kernel versions on my machines in case of a bad kernel upgrade.

---

### Post by Kilz on 2008-09-01
> **Oldsoldier2003 said:**
> +1 

very sound advice. I always leave at least 2 kernel versions on my machines in case of a bad kernel upgrade.

Hard lessons learned, the one bad kernel upgrade happened days after I cleaned out all but one kernel. It ended up being a reinstall.

---

### Post by Jozza The Wick on 2008-09-02
Thanks, aheckler. If anyone's interested, this also works for kernels you compile yourself from source, as opposed to install from a repository. If you select 'remove completely', the source & config files are also purged for you.

---

