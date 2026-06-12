---
title: "Error on boot - &quot;kernel panic&quot;"
date: 2005-08-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by filemanager on 2005-08-27
When trying to boot up, right after the "decompressing Linux" part, I get this error:

> Kernel panic - not synching: VFS: Unable to mount root fs on unknown-block(0,0)

Also, when I go into the GRUB menu and press "e" to edit the boot command line thing, here's what it says in there:

> 
root (hd0,4)
kernel /vmlinuz root=/dev/hda6 ro console=tty0 quiet splash
initrd /initrd.img
savedefault
boot



I don't know what that means or how to fix it =\ Last time I shut down my computer normally, and didn't get any errors, so can anyone help so my computer becomes usable again?

---

### Post by essexman on 2005-08-27
[QUOTE=filemanager]When trying to boot up, right after the "decompressing Linux" part, I get this error:



Also, when I go into the GRUB menu and press "e" to edit the boot command line thing, here's what it says in there:




I don't know what that means or how to fix it =\ Last time I shut down my computer normally, and didn't get any errors, so can anyone help so my computer becomes usable again?[/QUOTE]
Are you using a seperate /boot partition?
If not then there is a mis-match in the menu.1st first file.
If / and /boot are on the same partition it would be either hd(0,5) or /dev/hda5, but not hd(0,4) and /dev/hda6. Maybe try using the grub edit to test these two posibilities?  If still no luck, maybe you can post your fstab file?

---

### Post by filemanager on 2005-08-28
I'm not even sure what you just said :P

I have WinXP on one partition, and linux on another.

How do I get to my menu.1st file if I can't get into linux?

---

