---
title: "Cannot install Ubuntu 9.04 64"
date: 2009-04-28
forum: x86 64-bit Users
---

### Post by JonLittle on 2009-04-28
Well, I have had an AMD 64 for awhile, but had not really tired to use it.  with the launch of Jaunty, I figured I should see what it is like to run a 64 bit ubuntu. After downloading the ISO, I burned it to a disc and started to install Jaunty. 

Here is the problem. The disc boots, and I get the language chooser. I choose English and then the Live CD option. It shows the loading bar, and then after the loading bar gets full it shows the command line. What do I do now? do you install the 64 version from the command line? I typed in startx but it fails (I have attached a picture of the output) Even when I hit F4 and choose safe graphics mode I still get the command line and the error(s) when I type startx.

---

### Post by eidoslinux on 2009-04-28
you have to give us more data about you system and set up and copy of 9.04 that you are using.

---

### Post by JonLittle on 2009-04-28
> **eidoslinux said:**
> you have to give us more data about you system and set up and copy of 9.04 that you are using.
What data about my system do you need? I have an unmodified eMachines W5243 pc. It has an AMD Athlon 64 CPU and 2 GB of RAM. The graphics card is built in and is a NVIDIA GeForce 6100 nForce 405.  The copy of Ubuntu I am using is "ubuntu-9.04-desktop-amd64.iso"

---

### Post by dabl on 2009-04-28
> **JonLittle said:**
> 

 After downloading the ISO, I burned it to a disc 


Probably the error happened here.

- verified md5sum?
- set burn speed down to 4X?
- used DAO mode?
- don't use R/W disc?

---

### Post by sanderj on 2009-04-28
> **JonLittle said:**
> Well, I have had an AMD 64 for awhile, but had not really tired to use it.  with the launch of Jaunty, I figured I should see what it is like to run a 64 bit ubuntu. After downloading the ISO, I burned it to a disc and started to install Jaunty. 

Here is the problem. The disc boots, and I get the language chooser. I choose English and then the Live CD option. It shows the loading bar, and then after the loading bar gets full it shows the command line. What do I do now? do you install the 64 version from the command line? I typed in startx but it fails (I have attached a picture of the output) Even when I hit F4 and choose safe graphics mode I still get the command line and the error(s) when I type startx.


Do you also have a pciture of the first CLI, before you try to startx by hand?

Have you also tried Ubunut 8.10 64-bit?

Reason: Ubuntu 9.04 has a new X server, and that could be the problem. So maybe Ubuntu 8.10's X server works OK ...

---

### Post by JonLittle on 2009-04-28
> **dabl said:**
> Probably the error happened here.

- verified md5sum?
- set burn speed down to 4X?
- used DAO mode?
- don't use R/W disc?
I did verify the md5sum, and it was fine. 

The disc was burned at 1X.

I used InfraRecorder, and I did not have the option for DAO. I used SAO (the default). It also had the options of TAO, TAO with zero pregap, Raw writing (raw96r), (raw16), and (raw96p).

I used a DVD for it (that is all I have on hand).

I tried to do a USB, but my computer doesn't seem to be able to boot from that.

---

### Post by JonLittle on 2009-04-28
> **sanderj said:**
> Do you also have a pciture of the first CLI, before you try to startx by hand?

Have you also tried Ubunut 8.10 64-bit?

Reason: Ubuntu 9.04 has a new X server, and that could be the problem. So maybe Ubuntu 8.10's X server works OK ...

I'll get a picture up shortly. 

I have not tried 8.10 64-bit. I might try that if I cannot get this one to work. I assume that I can upgrade the 64-bit 8.10 just like I did my 32-bit?

---

### Post by JonLittle on 2009-04-28
Here are the pictures of the CLI before the startx command.

---

### Post by sanderj on 2009-04-28
> **JonLittle said:**
> Here are the pictures of the CLI before the startx command.

Ouch! Those "buffer i/o error on device sr0, logical block" seem to be a CD read problem. See [http://ubuntuforums.org/showthread.php?t=999549](http://ubuntuforums.org/showthread.php?t=999549) and [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/266951](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/266951)

See the tips there: change CD, change burn program, and/or change CD drive.

HTH

---

### Post by dabl on 2009-04-28
> **JonLittle said:**
> 

I used a DVD for it (that is all I have on hand).




If you burned a CD ISO image to a DVD, then I would expect this type of problem. There are DVD ISO images for *buntu -- you'd have to burn one of those to a DVD if you only have blank DVDs.

---

### Post by Slim Odds on 2009-04-28
> **dabl said:**
> If you burned a CD ISO image to a DVD, then I would expect this type of problem. There are DVD ISO images for *buntu -- you'd have to burn one of those to a DVD if you only have blank DVDs.

Yes, the problem is definitely read errors (which might be caused by this).

---

### Post by JonLittle on 2009-04-30
I finally fixed it. I still used a DVD, but I used Nero to burn it instead. Everything went fine, now the only thing is getting 64 bit drivers for the wireless adapter I use. 

Thanks for all of your help.

---

### Post by cariboo on 2009-04-30
Unless you have an bleeding edge off-shore wireless device, the drivers should already be loaded. Open an applacations-->Accessories-->Terminal and type:

```
sudo lshw -C network
```

enter your password when asked, the above command will print out a listing of your network devices, and show whether it is detected properly. Paste the output in your next post.

---

### Post by JonLittle on 2009-05-08
> **cariboo907 said:**
> Unless you have an bleeding edge off-shore wireless device, the drivers should already be loaded. Open an applacations-->Accessories-->Terminal and type:

```
sudo lshw -C network
```

enter your password when asked, the above command will print out a listing of your network devices, and show whether it is detected properly. Paste the output in your next post.


Here is the ouput: 

```
*-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 10
       serial: 00:1e:90:19:f4:d5
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 66:70:36:fa:cd:06
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

I had to use NDIS or something like that for it to work in my 32 bit version.  I tried that again, but when I add the INF file it says that it cannot see if hardware is present. 

It is a Trendnet TEW 424UB

---

