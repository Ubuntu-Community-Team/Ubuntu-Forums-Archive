---
title: "starting ubuntu"
date: 2009-10-25
forum: x86 64-bit Users
---

### Post by Tadcrazio on 2009-10-25
Okay i think i posted here before but i just dont understand. I'm dual booting Vista and Ubuntu. I'm loving ubuntu and i installed kubuntu too. Welll last night i shut off my computer and this morning when i booted i had three options to boot ubuntu, all leading to the same place, not including the recovery mode.. In noobie terms, how do i solve this? and what caused the third one to just come up. I know the second one was caused by trying uninstall then reinstall..

---

### Post by bedtime_with_the_bear on 2009-10-25
> **Tadcrazio said:**
> Okay i think i posted here before but i just dont understand. I'm dual booting Vista and Ubuntu. I'm loving ubuntu and i installed kubuntu too. Welll last night i shut off my computer and this morning when i booted i had three options to boot ubuntu, all leading to the same place, not including the recovery mode.. In noobie terms, how do i solve this? and what caused the third one to just come up. I know the second one was caused by trying uninstall then reinstall..

Are you using Wubi, or is it a regular install?

If a regular install, did you perform a system update? If it installed a new kernel, that will add a new grub menu option but will not remove old ones automatically. If everything is working OK, you can remove the older kernels, or leave them there, your choice.

If using Wubi, it'll be necessary to edit the Vista BCD configuration - that's a bit more complicated, but we can get you there.

---

### Post by Tadcrazio on 2009-10-25
i did a new install, it use to only have 2 in the grub but now there is 3. I don't know how to delete it from the grub menu.

---

### Post by bedtime_with_the_bear on 2009-10-25
First thing to do is get the version number of the kernel you want to remove - at the Grub menu, just make a note of it, for example 2.6.28-11.

Using your favorite package manager, (synaptic, adept, aptitude, etc...) search the installed packages for linux-image-2.6.28-11 and linux-headers-2.6.28-11 and flag each for removal. Finally, apply the removal action. This will remove the packages, which will also automatically remove the Grub entries.

Please be sure to only flag the kernel you want to remove - you shouldn't be able to remove all your kernels, but it's worth being careful.

I use aptitude, so I would do:


[LIST=1]
[*]Start a terminal session
[*]Type sudo aptitude
[*]Enter my password if necessary
[*]Type /linux.*2.6.28.11.*
[*]If the found result line begins with 'i', type _, otherwise type 'n' and repeat this step until you cycle back to the first result again
[*]Type 'g' twice - the selected kernels will be removed
[*]Once complete, type 'q' and select Yes to exit aptitude
[/LIST]
Obviously, throughout, replace 2.6.28-11 with the kernel version you made a note of earlier.

---

### Post by Barriehie on 2009-10-25
> **Tadcrazio said:**
> i did a new install, it use to only have 2 in the grub but now there is 3. I don't know how to delete it from the grub menu.

You'll need to edit the file /boot/grub/menu.lst    You can do this from the terminal using the command:
```

gksudo gedit /boot/grub/menu.lst

```

Once gedit opens the file you scroll down to the part that look like this:
```

.
.  ***Lines not shown here***
.

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-25-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=eb027411-9ea7-465a-b1a5-0ca148616c8a ro quiet splash
initrd		/boot/initrd.img-2.6.24-25-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-25-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=eb027411-9ea7-465a-b1a5-0ca148616c8a ro single
initrd		/boot/initrd.img-2.6.24-25-generic

title		Ubuntu 8.04, kernel 2.6.24-24-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=eb027411-9ea7-465a-b1a5-0ca148616c8a ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=eb027411-9ea7-465a-b1a5-0ca148616c8a ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title			WindowsXP
rootnoverify	(hd0,1)
makeactive
chainloader		+1

### END DEBIAN AUTOMAGIC KERNELS LIST

```

Simply put #'s in front of the entry you do not want to see.  This will comment them out.  Save the file with ctrl-s, close the file with ctrl-w, and quit with ctrl-q.  Your done! :)

Barrie

Edit: Along the lines of what the Bear is saying it's a good idea to leave 2 kernels in their;  I do for awhile after a new one is installed in case of any issues that way you can verify operation before deleting one.

---

### Post by Tadcrazio on 2009-10-25
thanks guys, now would there be any benefit over deleting it rather than just the # in front he entry.. And why did a third all of a sudden appear?

---

### Post by bedtime_with_the_bear on 2009-10-25
> **Tadcrazio said:**
> thanks guys, now would there be any benefit over deleting it rather than just the # in front he entry.. And why did a third all of a sudden appear?

The third probably appeared because you updated your system and it added a newer kernel - an update will add kernels, but never remove them so occasionally, you may have to do that manually. The reason is safety - if it removed all but the latest kernel, and that kernel happened to have a bug that prevented you from booting for example, you'd have big problems. I'm not on my Ubuntu install right now to check, but I believe Grub will only show to first 10 kernels (different menu entries for the same kernel don't count - so yuou'll still get at least a regular and failsafe menu item), so theres a limit to the number of kernels you'll see regardless of how many are installed.

Commenting out is obviously a more manual process, but it leaves the kernel files on your system so that's good if you want to tide up your Grub menu but would like to keep the older kernels in case you need to go back to them later.

Removing is good because it will remove the Grub menu entries for you and saves you a bit of disk space, but the big advantage is the safety net that it won't allow you to remove every kernel on your system so you can always boot to at least one kernel.

By commenting out, you have the ability to comment out all your kernels (stupid, yes, but there is nothing at all to stop you) and you would then need a livecd to uncomment them in order to boot normally again. You'd have to try really hard to mess it up so bad you remove all your kernels since it should be pretty obvious what you're doing once you get to that point.

Both methods will give you what you want, so go with whichever you're most comfortable with unless you are *really* short on disk space, in which case I'd recommend the uninstall to get you by, but we're only talking a few tens of MB, so it's not really that much by todays standards.

---

