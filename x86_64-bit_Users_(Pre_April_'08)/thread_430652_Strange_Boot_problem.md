---
title: "Strange Boot problem"
date: 2007-05-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by k8bebop on 2007-05-02
If I let it boot normally, using this boot, the default,

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0674841a-4a69-4689-993f-aa336b755a26 ro
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

it boots up fine, but the keyboard and mouse are not working.

If I choose recovery mode, 

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0674841a-4a69-4689-993f-aa336b755a26 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

and start gdm from there, the keyboard and mouse work.

---

### Post by kuja on 2007-05-02
that's an odd one, in recovery mode, try running "sudo dpkg-reconfigure xserver-xorg. Try selecting a different driver for keyboard and mouse both. Failing this, try changing the video driver too. Hard to say what the problem is ... but this is worth  a try I think.

---

### Post by k8bebop on 2007-05-02
well tried a different keyboard and mouse, but still not working if I use the default.

I don't want to change my video driver (using vesa now, because something is screwed up with my nvidia stuff). Want to get keyboard and mouse working first.

---

### Post by k8bebop on 2007-05-02
I figured out that bluetooth services were running. Should have told you guys that I'm running a wireless mouse & keyboard, and yes they are bluetooth, but the bluetooth services do not work on this machine.

So I disabled the bluetooth service and got my keyboard & mouse back.

---

