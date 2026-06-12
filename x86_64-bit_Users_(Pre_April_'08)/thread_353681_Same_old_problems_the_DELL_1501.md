---
title: "Same old problems: the DELL 1501"
date: 2007-02-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sebs0r on 2007-02-05
Hi, I have just managed to install Ubuntu onto my Dell1501 notebook using the live cd after a great deal of difficulty (finally having added irqpoll to the boot options). I then got stuck everytime i started the OS and it hung everytime at the loading screen.

I then edited the GRUB option and added irqpoll to the list, and it manages to load after about 20 seconds, which is great. The problem i am now having is when i want to enable networking, Ubuntu doesnt recognise my ethernet card. So i went into the device manager, and found that infact everysingle hardware had a great deal of "Unknowns" in the description and so i was wondering if i needed to install drivers or if they were contained on the cd.

I also wanted to edit the GRUB file on the filesystem so i didnt need to enter irqpoll each time, but it tells me i dont have the sufficient privlages, which is odd since im the only user mentioned. And THEN, when i log out and log mack in again, the graphics goes crazy (horizontal lines everywhere).

So, my question is, how do i get Ubuntu to recognise my hardware. irqpoll seems to work on the harddrive, but the rest doesnt seem to be happening. 

(i would have posted some form of error script, but i don't know where it would be located)

---

### Post by dashnak on 2007-02-12
Instead of using irqpoll use pci=nomsi, it seems irqpoll can cause some errors.... Also, in order to edit grub, you should use sudo, as in:
```
sudo nano /boot/grub/menu.lst
``` or if you want to do it graphically:
```
gksudo gedit /boot/grub/menu.lst
```
Also, to use the wifi card, yo need to use ndiswrapper..... Search the forums, there are guides about this, or go here: [http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html](http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html)
As for the unknowns, the only problem I have right now is beryl, it doesn't really affect anything as far as I can tell.....
For ethernet, if you are using the network manager applet, I have experienced some trouble with it not wanting to enable wired networking, so i use:
```
sudo dhclient3
```
Well, guess that's pretty much it....

---

### Post by Sebs0r on 2007-02-13
Yup, I should have updated: irqpoll just ignores the problem rather than fixing it. The pci=nomsi works real wonders. Its all working and fine. (i did get a problem about permissions at one stage - while trying to share a laptop folder on a windows network. after rebooting i couldn't log in with a message saying $HOME/.dmrc didn't have 644 permissions - logging in at the terminal, i changed it to 644, changed $HOME/<user> to 755 did the chown on everything and it still didnt work. In the end i got so pissed with it i just did a reinstall... i dont think ill ever try sharing linux on windows again just in case)

Thanks for the reply though - a week ago you would have saved me ;)

---

