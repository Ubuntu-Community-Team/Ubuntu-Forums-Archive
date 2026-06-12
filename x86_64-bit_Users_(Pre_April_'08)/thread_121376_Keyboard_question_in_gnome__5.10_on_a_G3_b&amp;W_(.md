---
title: "Keyboard question in gnome : 5.10 on a G3 b&amp;W (Azerty and mac compact keyboard)"
date: 2006-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Knightwise on 2006-01-25
Problem With apple Keyboard in Ubuntu 5.10

Hi guys. I've been wondering if somebody else has had the same problem i've experienced.

I'm running UBUNTU 5.10 on an older MAC Blue and White G3 350 Mhz. The keyboard i'm using is an apple compact keyboard.( AZERTY BELGIAN LAYOUT )  

When i'm installing UBUNTU it recognizes the keyboard just fine : The @ and the # are in the right place (top left corner key) As language i use ENGLISH , keyboard layout BELGIAN , location BELGIUM and time zone BRUSSELS.

All is good so far.
However when I boot up ubuntu after the installation ( login screen ) the keyboard layout is changed to QWERTY and the # key is now above the nr 3 ( consistant with a standard 104 key pc keyboard)

Once i log in I try to change the keyboard layout by going to SYSTEM - KEYBOARD - and add the BELGIAN keyboard layout (and set it default). Even if I remove the ENGLISH AMERICAN keyboard layout that is also listen and reboot the machine I STILL get QWERTY at and after the login and experience a standard 104 pc keyboard layout.

My question : What keyboard layout do i choose for my mac compact keyboard (if i change it in keyboard preferences to MACINTOSH i get a GNOME error screen) and how in hells bells can I change the keyboard to AZERTY (and make it stick).

I even want to use a standard 104 pc keyboard if only I can use the AZERTY optioN.

Thanx


KNIGHTWISE

[www.knightwise.com](www.knightwise.com)

---

### Post by Lanrond on 2006-01-25
I had a very similar problem with the live distro on an iMac.
I choose Italian/Italy as language and Italian as keyboard (qzerty), but, after getting into Gnome I realized that the keyboard was not correctly setted (i.e. 'q' and 'a' keys were swapped).
I used System->Keyboard to check what was my configuration and I saw that keyboard type was set to PC-something. I chanded to Macintosh (italian) and all went well.

---

### Post by Knightwise on 2006-01-26
Hi , Just to say : I did manage to get a workaround going.
By editing the xconf.org file ( /etc/X11) i was able to change the US setting to BE and now everything is working. But i did dump the compact mac keyboard because ... there is no insert button and all that ( and working with VI wothout an insert button requires extra keyboard shortcuts) So a classic usb keyboard (104 keys) was drawn into the occasion. After i restarted gnome everything worked. 

Come on people sing with me :
 A z E R T Y

---

