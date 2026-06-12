---
title: "Problems with dual-boot Breezy/macos9.2"
date: 2006-04-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Aurora on 2006-04-24
Greetings,

I had dual-boot working fine with Warty, but since I upgraded to Breezy I haven't been able to get MacOS to boot.  I edited yaboot.conf to point to the MacOS partition but it did no good.  Here is yaboot.conf as it is now:

boot=/dev/hda5
macos=/dev/hda7
defaultos=macos
device=/pci@80000000/mac-io@10/ide@20000/disk@0:
partition=6
root=/dev/hda6
timeout=500
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
fgcolor=black
bgcolor=light-cyan
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

See anything amiss? The only thing I remember being different in my previous install was the color of the yaboot screen/text.  I might have messed up the partitions.  How do I look at them and copy the table to a message here?

--Paul

---

### Post by Lanrond on 2006-04-24
Assuming your partition table is right, I think that the missing line here is:
```
enableofboot
```

---

### Post by Aurora on 2006-04-26
Lanrond,

enableofboot added, nothing changed.

This might be a clue:  despite the lines

fgcolor=black
bgcolor=light-cyan

It still boots with the default white text on black background.  It seems to use a default Ubuntu configuration no matter what is changed in /etc/yaboot.conf .

Curiouser and curiouser:confused:

---

### Post by Lanrond on 2006-04-26
[QUOTE=Aurora]Lanrond,

enableofboot added, nothing changed.

This might be a clue:  despite the lines

fgcolor=black
bgcolor=light-cyan

It still boots with the default white text on black background.  It seems to use a default Ubuntu configuration no matter what is changed in /etc/yaboot.conf .

Curiouser and curiouser:confused:[/QUOTE]

Did you remember to type```
sudo ybin -v
```after you edited /etc/yaboot.conf?

---

### Post by Aurora on 2006-04-27
[QUOTE=Lanrond]Did you remember to type```
sudo ybin -v
```after you edited /etc/yaboot.conf?[/QUOTE]

:oops: D'oh!

pad@iTux:~$ sudo ybin -v
ybin: Finding OpenFirmware device path to `/dev/hda5'...
ybin: Finding OpenFirmware device path to `/dev/hda7'...
ybin: Installing first stage bootstrap /usr/lib/yaboot/ofboot onto /dev/hda5...
ybin: Installing primary bootstrap /usr/lib/yaboot/yaboot onto /dev/hda5...
ybin: Installing /etc/yaboot.conf onto /dev/hda5...
ybin: Setting attributes on ofboot...
ybin: Setting attributes on yaboot...
ybin: Setting attributes on yaboot.conf...
ybin: Blessing /dev/hda5 with Holy Penguin Pee...
ybin: Updating OpenFirmware boot-device variable in nvram...

Penguin Pee? It really says that; it really is the, ahem, output.

Thanks for pointing out the obvious.

--Paul

---

