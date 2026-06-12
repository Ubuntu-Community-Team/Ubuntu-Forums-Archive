---
title: "[SOLVED] Gutsy 64 and Gutsy 32 Dual Boot; GRUB"
date: 2007-10-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by aphirst on 2007-10-21
Today I installed Gutsy 32 into a spare partition alongside Gutsy 64 on my laptop. I have just noticed that my bootloader runs from the Gutsy 32 partition, and not the 64 partition (which I intend to be my primary base of operations; the 32 partition only really being there for 32-bit compatibility and a ready supply of library files to ln -s into /usr/lib32 ).

Does anyone know how to make it so that GRUB is only installed on hda1(64), with no GRUB on hda2 (32); so that the MBR is from the 64-bit version; but can still boot both versions?

I will clarify if I am talking gibberish. :P

---

### Post by aphirst on 2007-10-21
Don't worry, reliable community. My 1337 h4><0r skillz have saved the day again. :P

I simply reinstalled grub
```
sudo grub

grub> find /boot/grub/stage1
 (hdx,y) # this will be the output
grub> root (hdx,y)
grub> setup (hdx)
```

and reconfigured /boot/grub/menu.lst to include the OSs I wanted.

Thanks to PingunZ's tutorial for GfxBoot for the inspiration for the idea! I hoe this helps anyone else as pedantic as me :P

---

