---
title: "Yaboot didn't install..."
date: 2006-03-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by charriso on 2006-03-27
Hello,

Trying to install Ubuntu 5.10 on my G4, I discovered a faulty CD drive. Only solution was to install from my laptop (iBook G4) with my desktop (G4 AGP) in target FireWire mode. This seems to have worked, except for yaboot, which wasn't installed (I imagine because with my desktop in FireWire target mode, the installer coudn't see a bootable volume?) 

Anyway, Yaboot didn't install, and I can't get it to install from the CD cross FireWire - it just refuses (scary-looking red screen error each time).

Is there any way to install yaboot manually, given that my CD drive on my G4 really won't cooperate with the install disk...

Alternatively, is there another way to launch Ubuntu, which as far as I can tell is fully installed, but the Mac doesn't see it on startup... Some command-line incantations?

I'm a newbie (as if it isn't obvious...)

Colin.

---

### Post by stuporglue on 2006-03-27
Yeah, you can get yaboot installed still.

Boot from a LiveCD, and get comfy with the terminal...


Make a mount point:
mkdir /mnt/ubu

Mount your Ubuntu install on the mount point:
mount /dev/my_ubuntu_partition /mnt/ubu

Mount the proc, sys and dev file systems inside your Ubuntu install
mount -t proc none /mnt/ubu/proc
mount -o bind /dev /mnt/ubu/dev
mount -o bind /sys /mnt/ubu/sys

Chroot into your Ubuntu install system:
chroot /mnt/ubu /bin/bash

Now you're inside your Ubuntu install! Try just installing yaboot...maybe it'll just work?

Try:
mkofboot -v

No luck? 
Try:
yabootconfig
if yabootconfig does something try "mkofboot -v" again

Still no luck? 
Post your error messages here


Assuming it does work, or when you're ready to give up for a while get out of the chroot environment by doing:
exit
umount /mnt/ubu/proc
umount /mnt/ubu/sys
umount /mnt/ubu/dev
umount /mnt/ubu

You can then use the regular liveCd shut down method.

---

### Post by Jawbreaker4Fs on 2006-03-27
Sorry, meant to respond to my post about yaboot not working.. not sure how to delete a post, so I just edited it out

---

### Post by charriso on 2006-03-27
Wow, thanks for the detailed reply...

Only thing is, my dodgy cd drive on the G4 won't run the LiveCD either (already tried). I would have to do all that with the G4 in FireWire target mode from my laptop, same way I did the install...

Will the Ubuntu LiveCD deal with FireWire and still see the Ubuntu partitions on my G4...?  I guess there's only one way to find out, eh... I'l give it a bash (no pun intended).

---

### Post by stuporglue on 2006-03-27
> Only thing is, my dodgy cd drive on the G4 won't run the LiveCD either (already tried). I would have to do all that with the G4 in FireWire target mode from my laptop, same way I did the install...

Will the Ubuntu LiveCD deal with FireWire and still see the Ubuntu partitions on my G4...? I guess there's only one way to find out, eh... I'l give it a bash (no pun intended).

It should, but I'll bet that has something to do with why the yaboot install didn't go as it should have the first time arround.

If yaboot still doesn't install, you might be able to do some open firmware magic to get it booted. I sold my Mac last fall though, so I'm forgetting some of that trickier stuff. 

Q: Why don't you put your laptop into firewire mode and throw the CD in it, the hold down option on your G4 till all the boot options come up? Then you could choose the CD, boot from the install CD on the computer that it's meant to be installed on. G4 supports booting from firewire, doesn't it?

---

### Post by charriso on 2006-03-27
[QUOTE=stuporglue
Q: Why don't you put your laptop into firewire mode and throw the CD in it, the hold down option on your G4 till all the boot options come up? Then you could choose the CD, boot from the install CD on the computer that it's meant to be installed on. G4 supports booting from firewire, doesn't it?[/QUOTE]

That sounded like a really good idea. nearly worked too...  Got to the choice of OS, and Linux was an option. Selecting it made the LiveCD jump around a bit, but just brought me back to the choice of OS page (with slightly corrupted graphics). Persisted stupidly a few more times, but alway round in a loop - wouldn't launch.:( 

if I tried it the other way round (working from the laptop with the G4 in target more) I would need a few more incantations to make sure I was installing things in the right place, eh...

(Provo! I went to a conference in Provo once! Nice town - beautiful mountains!)

---

### Post by staticdisaster on 2006-03-28
Do you only have one hard drive in your G4 tower? 

If so.. boot into Open Firmware, then when the prompt appears type 
boot hd:2,yaboot

Once in Linux, you'll have to re-run ybin so it can run Yaboot on startup

---

### Post by charriso on 2006-03-29
No, I have 2 HD in the tower: the one it shipped with (dev0) which now contains the Linux partitions, and one on the slave bus (dev1) which has OS X on one partition, and storage on the rest...

Not being able to boot from the CD drive in the tower is a real pain, and makes me wonder whether I sholdn't just replace the CD reader...

---

