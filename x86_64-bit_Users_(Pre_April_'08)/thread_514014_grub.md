---
title: "grub"
date: 2007-07-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by nzadLithium on 2007-07-31
Hey

I'm trying to change my grub config. I'm attempting to modify the line that says 
kernel		/boot/vmlinuz-2.6.17-12-generic root=/dev/hda2 ro quiet splash
and change it to
kernel		/boot/vmlinuz-2.6.17-12-generic root=/dev/hda2 ro vga=normal

i'm doing this because this is meant to fix multicolored screen problems on shutdown and switching tty while using the nvidia drivers.

Everytime i modify this file i then save it. (i am accessing as root)
It seems to save fine.
I then do 
sudo update grub

It says all is good but it cant find the splash image. Well i don't really care about that as im trying to get rid of it!

Then i restart.
I'm not sure which image the splash image is but its either that one that comes up saying ubuntu with the loading bar along the bottom or the one that comes up when its loading the nautilus etc.

Neither of these had dissapeared and i had expected one too (altho im not sure which one because as i said i don't know which one is the splash image lol) :(
I then went and took a look at the menu.lst file again and it says 
kernel		/boot/vmlinuz-2.6.17-12-generic root=/dev/hda2 ro quiet splash

wtf is up with this?
why is it resetting itself?

thx

---

### Post by 5-HT on 2007-07-31
Running update-grub will reset the kernel boot options to those specified in # kopt=, # defoptions=, and # altoptions= (depending on how your menu.lst is setup). The boot options you see for each kernel entry are put there by the update-grub script. To automagically append vga=normal and remove splash & quiet from your primary kernel lines after running update-grub (either manually or after a kernel upgrade), you'll need to modify your # defoptions line instead of directly editing the kernel lines themselves (the update-grub manual covers all of this).

e.g.,
```
# defoptions=vga=normal
```If you don't want to edit # defoptions, then just make the changes to the kernel lines and make sure update-grub is not run (it's set to run after a kernel update), or place your entries after the end of the ### END DEBIAN AUTOMAGIC KERNELS LIST (you'll need to manually update the file after updating your kernel though).
cheers,

---

### Post by nzadLithium on 2007-07-31
lol k thx

im a bit stupid :)

i try that

---

### Post by nzadLithium on 2007-08-01
Yep that worked perfect.

Just got to hope it fixed it now [-o<

---

