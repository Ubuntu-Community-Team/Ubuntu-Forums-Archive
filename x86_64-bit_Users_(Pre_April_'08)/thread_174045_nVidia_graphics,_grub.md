---
title: "nVidia graphics, grub"
date: 2006-05-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by vincister on 2006-05-11
I've got two problems

1. When I start ubuntu it's ok, I see the loading modules screen, but after it there should be login screen, but I see just a "crash of colors"
I have AMD +3200 & nVidia GeForce 6600 what should I do?
I can access only the console mode, without graphical enviroment.

2. How to configure grub, that Windows is the primary booting system?

I'm really sad cause I can't even test how good is ubuntu, I've used it at school, but I want to know if it's good for my home use.

---

### Post by Seaman on 2006-05-11
[QUOTE=vincister]I've got two problems

1. When I start ubuntu it's ok, I see the loading modules screen, but after it there should be login screen, but I see just a "crash of colors"
I have AMD +3200 & nVidia GeForce 6600 what should I do?
I can access only the console mode, without graphical enviroment.

2. How to configure grub, that Windows is the primary booting system?

I'm really sad cause I can't even test how good is ubuntu, I've used it at school, but I want to know if it's good for my home use.[/QUOTE]
If you type "startx" in you terminal, what error messages do you get?

---

### Post by sargeras on 2006-05-11
I found this too happen on my laptop when the refresh rates were incorrect.  I would check this first.

As for grub, I'm not a pro, but I think that if you edit your grub settings file (I think it's in /boot/grub) to make the windows at the top of the list of boot options it should load by default.  

Hope this helps

---

### Post by sargeras on 2006-05-11
I found this too happen on my laptop when the refresh rates were incorrect.  I would check this first.

As for grub, I'm not a pro, but I think that if you edit your grub settings file (I think it's in /boot/grub) to make the windows at the top of the list of boot options it should load by default.  

Hope this helps

---

### Post by turbojugend_gr on 2006-05-12
[QUOTE=vincister]I've got two problems

1. When I start ubuntu it's ok, I see the loading modules screen, but after it there should be login screen, but I see just a "crash of colors"
I have AMD +3200 & nVidia GeForce 6600 what should I do?
I can access only the console mode, without graphical enviroment.

2. How to configure grub, that Windows is the primary booting system?

I'm really sad cause I can't even test how good is ubuntu, I've used it at school, but I want to know if it's good for my home use.[/QUOTE]

TO MAKE WINDOWS your boot Default: write in a terminal (console) the following:
```
sudo pico /boot/grub/menu.lst
```
A simple text editor should appear. Near the end of this document you should find some lines begining without ##, theese are your List choices as you see them in the Grub menu. Before them add the following : default NUM. where NUM write the number of the Windows choice in your Grub list, counting starts with 0. So if Windows are 4th in order (which should be the case), you should write "default 3".

If you have any question regarding the above, feel free to ask. Just do so before you edit menu.lst ,thus avoiding any trouble.

I hope I was helpfull.

---

### Post by vincister on 2006-05-16
Thanks, I managed to configure Grub (one friend aid me)

but what about that graphical enviroment

> If you type "startx" in you terminal, what error messages do you get?
I tried, but i get just another crash of colors(more green) and hear some music in background. :(

---

### Post by tseliot on 2006-05-16
[QUOTE=vincister]Thanks, I managed to configure Grub (one friend aid me)

but what about that graphical enviroment


I tried, but i get just another crash of colors(more green) and hear some music in background. :([/QUOTE]
Type:
```
sudo nano -w /etc/X11/xorg.conf
```

and set the driver to "vesa" in the Section Device of the file.

CTRL+x to exit (save the file)

Then type:
```
sudo /etc/init.d/gdm restart (or "kdm restart" if you use KDM)
```

Then you'll be able to enter the graphical environment and you should install the nvidia proprietart drivers for better performance and 3d acceleration.

You can use my guide or my script for that:
[http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia]("http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia")

---

### Post by vincister on 2006-05-17
I used something like this:
sudo dpkg-reconfigure xserver-xorg

cause there was no X11 directory before this configuration

now i just need to install nvidia.glx i think, but this will be done when I'll have internet at home.

thanks now i can learn more linux, than just console

---

