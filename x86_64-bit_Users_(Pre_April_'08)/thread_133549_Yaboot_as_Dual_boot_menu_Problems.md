---
title: "Yaboot as Dual boot menu Problems"
date: 2006-02-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by macminiman on 2006-02-20
Hello,
I have just installed Ubuntu and so far it is working great! Yaboot, on the first try didn't install, but I tried again and it worked. I want to make yaboot work as a dual boot menu, and have Ubuntu ('linux') and Mac OS X on the boot menu. I googled it, and found that if I type in 'macosx=/dev/hdb' I could get Mac OS X to boot by typing 'x' (My Externel HD is hdb). I did this, and I rebooted, typed in 'x', and thats where my problems started to come up. After I type it in, it goes to the standard gray screen for about half a second, then comes back to the menu. I heard that using macosx= is only for UFS partitions, and you use brokenosx for HFS, HFS+. It said that you need to have macosx= in place for brokenosx to work, but it doesn't. Here is my current config:
boot=/dev/hda5
device=/pci@f4000000/ata-6@d/disk@0:
partition=6
root=/dev/hda6
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux
label=Linux
read-only
initrd=/boot/initrd.img
append="quiet splash"

image=/boot/vmlinux.old
label=old
read-only
initrd=/boot/initrd.img.old
append="quiet splash"
image=/boot/vmlinux.old
label=old
read-only
initrd=/boot/initrd.img.old
append="quiet splash"
# This line adds a Mac OS X selection to the boot menu
brokenosx
macosx=/dev/hdb

Anybody who can help me at all with this, thank you! :D

- Craig

---

### Post by imacQ on 2006-02-20
you could try moving it up there under "enablecdboot" i don't know if that will make a difference, but that's where mine is.

---

