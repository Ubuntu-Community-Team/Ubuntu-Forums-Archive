---
title: "Dual boot Issue"
date: 2007-12-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Awkward on 2007-12-14
I recently installed Ubuntu on its own, but I realized that I need XP for some stuff as well, so i installed it on my second slave drive (ubuntu is on the master). Grub won't detect the xp install however.. how do i go about adding XP Pro to the boot menu?

---

### Post by Snakob808 on 2007-12-14
If I'm not mistaken, you'll actually have to change the boot sequence in the bios if they are on separate drives.

---

### Post by Awkward on 2007-12-14
please elaborate

---

### Post by bernied on 2007-12-14
I think what snakob is saying is that you have to enter the bios settings (this is where you hit the Esc key or one of the F keys, just before an operating system boots) in order to boot your windows.

But the grub bootloader can handle this situation.

Windows likes to be only on the first disk. So it would be useful to know how you installed it at this point.

But in the meantime you can try editing the grub config file manually. The file is at /boot/grub/menu.lst and you need to edit it as the root user. The command, in a terminal:
```
gksudo gedit /boot/grub/menu.lst
```might do this for you. Otherwise find another text editor (my favourite is nano).

So the entry that you can try is this, put it right at the end of the file, after the line that defines the end of the automated section:
```
title Windows
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```Save the file, and reboot, you should have a new option at the end of your boot menu.

So the lines mean this (adjust them if I've got your configuration wrong)
 - The operating system is on ('root') the second disk ('(hd1 ...') in the first partition ('(hd1,0)') - grub starts counting at 0, not 1
- Tell the operating system that the first disk is actually the second
- Tell the operating system that the second disk is the first
- Load the bootloader on the target partition

Try this, let us know if it works.

---

### Post by rsambuca on 2007-12-14
> **bernied said:**
> I think what snakob is saying is that you have to enter the bios settings (this is where you hit the Esc key or one of the F keys, just before an operating system boots) in order to boot your windows.

But the grub bootloader can handle this situation.

Windows likes to be only on the first disk. So it would be useful to know how you installed it at this point.

But in the meantime you can try editing the grub config file manually. The file is at /boot/grub/menu.lst and you need to edit it as the root user. The command, in a terminal:
```
sudo gedit
```might do this for you. Otherwise find another text editor (my favourite is nano).

So the entry that you can try is this, put it right at the end of the file, after the line that defines the end of the automated section:
```
title Windows
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```Save the file, and reboot, you should have a new option at the end of your boot menu.

So the lines mean this (adjust them if I've got your configuration wrong)
 - The operating system is on ('root') the second disk ('(hd1 ...') in the first partition ('(hd1,0)') - grub starts counting at 0, not 1
- Tell the operating system that the first disk is actually the second
- Tell the operating system that the second disk is the first
- Load the bootloader on the target partition

Try this, let us know if it works.

The mapping might work, but the commands to edit the file are incorrect.  You will want to open a terminal and run:

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by bernied on 2007-12-14
> **rsambuca said:**
> The mapping might work, but the commands to edit the file are incorrect.  

My apologies. I've changed the text in my post.

---

### Post by rsambuca on 2007-12-14
> **bernied said:**
> My apologies. I've changed the text in my post.

It is actually still incorrect!  If you need root permissions for a program running in X Server, then you should be using gksudo instead of sudo (although you actually get away with it in this case).

---

### Post by mondy on 2007-12-14
hi listen carefuly. i have an 80 gb hd,i format it then i install winxp first the install unbuntu 6.06 second.when i reboot the pc then grub ask os i want to chose.its that simple.bye

---

### Post by bernied on 2007-12-14
> **mondy said:**
> hi listen carefuly. i have an 80 gb hd,i format it then i install winxp first the install unbuntu 6.06 second.when i reboot the pc then grub ask os i want to chose.its that simple.bye
The question was how to add XP after linux is installed, not before.
It's not necessary to reinstall an entire operating system to achieve this.

---

### Post by bernied on 2007-12-14
> **rsambuca said:**
> It is actually still incorrect!  If you need root permissions for a program running in X Server, then you should be using gksudo instead of sudo (although you actually get away with it in this case).
Like a terrier you are :). I need sleep.

---

### Post by Awkward on 2007-12-14
i actually made the second drive the master just for the install then switched it back to slave. I dont know anything about the terminal, i cant figure out how to edit that file

---

### Post by Awkward on 2007-12-14
Wait, I got it. Worked like a charm, awesome advice guys :)

---

### Post by bernied on 2007-12-15
Superb!

---

