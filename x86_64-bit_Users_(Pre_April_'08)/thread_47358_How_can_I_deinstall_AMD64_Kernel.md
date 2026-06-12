---
title: "How can I deinstall AMD64 Kernel"
date: 2005-07-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by pingp on 2005-07-08
I installed Ubuntu with Kernel 2.5.10-5 AMD64 version(I have a A64 Notebook), but I can not got the Cisco VPN Client built on 64bit plattform, and the JDK 1.5.0 64bit and Eclipse 3.01 64bit crashed again and again.
So i have to change Kernel, I deleted the partition(/) and reinstalled Ubuntu. During the there is no chance to chose Kernel, the old kernel would be used again?!

My Question is:
1 Which Kernel should I use, 686?
2 How can I change Kernel (or reinstall with other Kernel), i used apt, but in the list all are A64 kernel package.

I am a newbie, sorry for this question.

---

### Post by jasmuz on 2005-07-08
[QUOTE=pingp]I installed Ubuntu with Kernel 2.5.10-5 AMD64 version(I have a A64 Notebook), but I can not got the Cisco VPN Client built on 64bit plattform, and the JDK 1.5.0 64bit and Eclipse 3.01 64bit crashed again and again.
So i have to change Kernel, I deleted the partition(/) and reinstalled Ubuntu. During the there is no chance to chose Kernel, the old kernel would be used again?!

My Question is:
1 Which Kernel should I use, 686?
2 How can I change Kernel (or reinstall with other Kernel), i used apt, but in the list all are A64 kernel package.

I am a newbie, sorry for this question.[/QUOTE]
 Since major software hasnt been compiled yet on a 64 bit platform, you could try using a 32 bit kernel, thus you will not notice major improvements of 64 bit over 32 bit.

The kernel you might use is the K7 kernel wich is actually used in Athlon's and Semproms.

PLEASE NOTE THAT WHAT YOU ARE GOING TO DO IS EXPERIMENTAL

To download such kernel, you will have to add the 32 bit Ubuntu repotories, via sudo gedit /etc/apt/sources.list

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

When you are done installing, then delete these repositories from your list.

Please tell me how it went.

---

### Post by pingp on 2005-07-08
I always got same error

root@Lebing:/etc/apt # apt-get update
........
........

root@Lebing:/etc/apt # apt-get install linux-k7
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-k7
root@Lebing:/etc/apt #

---

### Post by FluffyElmo on 2005-07-08
I think you're going to have to reinstall to go back to 32bit. You can back-up your home directory and it shouldn't be too painful. 

Incedentally, Ecllipse crashes due to a bug in the Sun JVM. If you use the IBM 1.4.x amd64 JVM it will run fine. I've never used the Cisco VPN client though so I can't help there...

---

### Post by pingp on 2005-07-08
[QUOTE=FluffyElmo]I think you're going to have to reinstall to go back to 32bit. You can back-up your home directory and it shouldn't be too painful. 

Incedentally, Ecllipse crashes due to a bug in the Sun JVM. If you use the IBM 1.4.x amd64 JVM it will run fine. I've never used the Cisco VPN client though so I can't help there...[/QUOTE]

yesyes, i have reinstalled Ubuntu, but Ubuntu is too clever to give me a chance chosing new Kernel... :razz:  :razz:  There is no menu to chose Kernel at 2nd install.

I am a newbie by Linux, so painfully, i can neither deinstall it nor find new package.

---

### Post by FluffyElmo on 2005-07-08
You'll have to download the x86 install disk. It will run on amd64 but with the 32bit kernel. The amd64 install disk only includes the 64bit version.

Once you've installed the x86 version you can install the k7 kernel from Synaptic, replacing the x86-generic one.

---

### Post by pingp on 2005-07-09
[QUOTE=FluffyElmo]You'll have to download the x86 install disk. It will run on amd64 but with the 32bit kernel. The amd64 install disk only includes the 64bit version.

Once you've installed the x86 version you can install the k7 kernel from Synaptic, replacing the x86-generic one.[/QUOTE]

Thanks alot!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
one Question more, in Synaptic I should first uninstall the X86-gerneric(only 1 package?), and install the K7 one? Should I change the Grub to point new Kernel?

I just want to learn more about Linux. There 3 or 4 package which seems as Kernel, and what is restrict mode?

---

### Post by FluffyElmo on 2005-07-09
You can just install the* linux-image-k7* package (name may differ somewhat, can't see the 32bit repositories), it will automatically update grub and replace the generic kernel as your default kernel. Later if you want to free up a little disk space you can remove the generic image, though it is probably useful as a back-up right now in case you have any problems with the k7 kernel you can select the old one from the grub boot menu.

Note the basic linux-image-k7 package will install the most recent kernel package so you don't have to keep installing individual linux-image-2.6.10.x-k7 packages.

The *linux-restricted-modules-k7* package contains non-free kernel modules. That is where you will find Nvidia/ATI graphics drivers, wireless network card drivers and such. I usually install it as it can't hurt and may help:)

---

