---
title: "New user need help with ubuntu and 64 bit"
date: 2008-01-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by ncubano on 2008-01-21
Hello, 

I am new to ubuntu and linux. After doing some research I decided to give it a try since I like the open source community. I have a laptop (Compaq Presario R3000) with a 64bit amd athlon, 512 ram, and 60gb (12of which are free). I decided to try out wubi to install linux that way I could keep windows and run ubuntu. When I first d/l the program everything worked fine but my roommate told me that it was an out dated version. So I decided to upgrade to the newest version. Instantly I began to have problems. 
1st issue- my Ethernet Internet did not want to work and I tried everything in the help manual and even had a few friends take a look at it. When i try to go into hardware information to find out about my drivers, the window opens and closes immediately!
2nd issue- is a internal error message that I receive at boot up. It states that "failed to initialize HAL! I know this issue has been discussed before but the people that have this issue seem to have problems with booting up and using usb ports etc. I do not have that problem. The only thing that does not work is my Internet and the computer takes sometime to open such things as network config. and to shut down the computer. 
3rd issue- I know this does not have to do with ubuntu, but was thinking someone here could answer it. I have not been happy with writer from openoffice. I misspell simple words such as "spel" and the spell check does not pick anything up. I was wondering if this is common or do I just have a bad version. Also are there any upgrades that I can install for open office to make it a little better such as grammar check etc.

Thank you in advance for your time and help!

---

### Post by Yellow Pasque on 2008-01-21
I have a feeling that solving the HAL issue will bring back your Interweb. Try starting HAL manually and see what output you get. From terminal:
```
sudo /etc/init.d/hal restart
```
If it starts, it may be a problem with your system trying to load HAL before one of its dependencies (DBUS) loads. To remedy that:
```
sudo mv /etc/rc2.d/S12hal /etc/rc2.d/S13hal
```

---

### Post by ncubano on 2008-01-21
Thank you for your help. Last night I just decided to reboot the older version of ubuntu and it is working just great, but I do want to update it in the following days so I will definitely try this out. Thank you once again for your time!

---

