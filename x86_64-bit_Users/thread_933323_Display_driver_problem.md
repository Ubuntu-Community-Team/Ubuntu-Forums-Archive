---
title: "Display driver problem"
date: 2008-09-29
forum: x86 64-bit Users
---

### Post by rajatksi on 2008-09-29
i am having amd athlon x2 with nvidia chipsets but working as 32 bit. problem is my laps resolution is 800*680 only. i downloaded nvidia linux driver. when i try to install it thru terminal it says could not install bcause xterminal is running. my questions
1.is there any way i can log in to ubuntu with out activating Xterminal?
2.is there any alternative for nvidia driver softwares

---

### Post by phlembob on 2008-09-29
NVIDIA drivers are available.  NVIDIA accelerated graphics (latest cards) can be found in Hardware Drivers.  If you try and are not greeted with the emblem that looks like the Hardware Drivers emblem under System > Administration when you power down then power up at the top bar.  Write the description of your computer including nvidia card model among your write up.  We will be able to help you better.

---

### Post by Artemis3 on 2008-09-29
What nvidia card? The newest cards don't work out of the box, but might work with the latest nvidia driver from nvidia page.

---

### Post by Crafty Kisses on 2008-09-29
Post the results of this command:
```
glxinfo
```

---

### Post by Yellow Pasque on 2008-09-30
> 1.is there any way i can log in to ubuntu with out activating Xterminal?
When your system first starts, it should show the GRUB boot menu (you may need to press 'Esc'). Choose the recovery mode and boot to a root terminal when prompted.
OR
For instant gratification, save your work and close all programs, then drop to a terminal (Ctrl+Alt+F1) and:
```
sudo /etc/init.d/gdm stop
```

---

### Post by rajatksi on 2008-10-02
thank you all of you it started working.:guitar:

---

### Post by hmarkg on 2008-10-02
Hi i have been using ubuntu for a few month now and still not really sure about how thing work. Previously i installed ubuntu on my desktop computer without any problem with the driver setup. But now i have my new laptop and have problem installing drivers such as graphic card (nVidia Geforce 9200M GS). I could use a little help here on how to install the driver, a little HOWTO will come in handy. I have read up on nVidia official website on how to install but i still got really get it, though I have tried it. Can someone help me.

---

### Post by TVMA on 2008-10-03
> **hmarkg said:**
> Hi i have been using ubuntu for a few month now and still not really sure about how thing work. Previously i installed ubuntu on my desktop computer without any problem with the driver setup. But now i have my new laptop and have problem installing drivers such as graphic card (nVidia Geforce 9200M GS). I could use a little help here on how to install the driver, a little HOWTO will come in handy. I have read up on nVidia official website on how to install but i still got really get it, though I have tried it. Can someone help me.

What I would recommend, is opening up synaptic package manager

System > Administration > Synaptic Package Manager >

Do a search for "envy" no quotes.

If running gnome, just install the envy-gtk, for KDE do the envy-QT, it will grab the necessary dependency. Install it. Then open it under

Applications > System Tools > EnvyNG

Just select your Nvidia, and let it do automatic detection, make sure you have closed the synaptic package manager at this point. It will automatically download and install your driver, and modify your /etc/X11/xorg.conf file for you, then it will ask you to restart. Then enjoy.

:guitar:

---

