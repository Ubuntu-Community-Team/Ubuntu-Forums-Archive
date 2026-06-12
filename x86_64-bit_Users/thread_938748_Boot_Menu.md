---
title: "Boot Menu"
date: 2008-10-05
forum: x86 64-bit Users
---

### Post by Andrew.McKae on 2008-10-05
I am running on windows XP, well I was at least. I wanted to try out ubuntu and have in the past. I am still a noob to linux and things so I'm a little uneducated. I did a dual boot with Windows XP and ubuntu everything went smoothly followed tutorials etc; using 8.04 (I think) it good it auto detects the windows. Only problem now is when I restart the computer the screen goes black for maybe about 10-20 seconds then goes straight to ubuntu without any choice. They are both on one drive with 78gb for ubuntu and the rest (forgot) for windows. I'm not totally sure windows is there anymore because when I go to disk - File Browser is says 235.1 Media.. but that is roughly the size I put for windows... I would be very greatful for some help. I've done my research and It's about the grub? I could just repair windows XP to replace the MBR?

Thanks if you can help. :guitar:

I'm new on the forum and hope to be active!

---

### Post by caljohnsmith on 2008-10-05
Probably your Grub menu is just "hidden", so the next time you start up, try pressing ESC repeatedly until you get the Grub menu. If that doesn't work, then when you are in Ubuntu, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -l
cat /boot/grub/menu.lst
```
Also, if the above "ESC" trick works, you can change your Grub's menu.lst so the Grub menu always shows on start up. But try the ESC trick first and let me know what happens. :)

---

### Post by Andrew.McKae on 2008-10-05
I have sucsessfully got onto windows XP, the only problem now, I've made it worse. I installed the xserver-glu or something to enable the desktop effects, I also installed something to do with my graphics card, now after the ubuntu loading bar it goes black then does nothing. I put in the CD THEN I get the grub, so I'm unsure what I can do now, I could re-install ubuntu then fix the grub?

---

