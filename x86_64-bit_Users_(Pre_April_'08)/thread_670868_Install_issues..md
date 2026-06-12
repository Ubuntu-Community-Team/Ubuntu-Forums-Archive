---
title: "Install issues."
date: 2008-01-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Visceral Monkey on 2008-01-17
Wow, where to start. OK, I can't boot the x86-64 live cd without hitting f6 and them removing quiet and adding nosplash instead of splash. After that, it boots and I can install..but upon booting up I get nothing but a black screen when it starts to load. I've tried editing the grub file by removing quiet and adding nosplash but it makes no difference, I will start to boot and then a black screen..nothing. 

Oh, if I hit "safe mode" it does boot..but of course I have no internet, etc because I'm assuming it doesnt load any driver at all. Video card is a 8800gts.


Any ideas?

---

### Post by Cappy on 2008-01-17
When GRUB is booting hit 'e'
then hit the down arrow and hit 'e' again (you should be hitting 'e' on the line named "kernel" at this point).
Take off "splash" and put in "nosplash".
Hit enter.
Hit 'b'.

Once you are in ubuntu you can edit the file /boot/grub/menu.lst by running
> 
sudo mv /boot/grub/menu.lst /boot/grub/menuold.lst; sudo sed 's/ splash/ nosplash' /boot/grub/menuold.lst > /boot/grub/menu.lst

---

