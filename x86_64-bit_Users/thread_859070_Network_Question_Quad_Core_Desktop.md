---
title: "Network Question: Quad Core Desktop"
date: 2008-07-14
forum: x86 64-bit Users
---

### Post by fletc900 on 2008-07-14
Hi there, 

I just got an HP Pavilion Elite PC m9340f. This is an Intel Core 2 Quad Core processor Q6700 with 6 GB of ram; this is my first 64-bit machine. The system comes with an onboard LAN which seems to be incompatible with Linux. The worst thing about this computer is that all the expansion ports (PCI) have been occupied. There is Windows Modem on the PCI-32 port which I won't use. I was thinking about getting a new [network card (link)]("http://www.bestbuy.com/site/olspage.jsp?skuId=3195642&st=Network+Card+PCI&lp=1&type=product&cp=1&id=1051384122901") an place it on the PCI-32 port. My question is: would a ubuntu 64 have any problems recognizing a network card on a [COLOR="Red"]PCI-32[/COLOR] port? 


Here are the specs for the machine: [link]("http://reviews.cnet.com/desktops/hp-pavilion-elite-m9340f/4507-3118_7-33109780.html").

I appreciate your help.

:confused:

---

### Post by soxs on 2008-07-14
What makes you sure your network card doesn't work?
Did it spit any errors out?
Did you try to configure anything?
How do you connect to the internet?
Did you try to connect to another PC via a corssed LAN cable?

---

### Post by DRomeo521 on 2008-07-18
I also bought the same machine (m9340f), and am having the same problem.  First thing I did was dual boot to Kubuntu 8.04.  Neither the NIC nor wireless card are being recognized.  The wirless card is a Ralink.  I'd appreciate any advice on how to work around this issue.  (I won't be able to actually try anything for another couple of days.  I will be back Monday July 21)

Thanks in advance

---

### Post by John.Michael.Kane on 2008-07-18
> **DRomeo521 said:**
> I also bought the same machine (m9340f), and am having the same problem.  First thing I did was dual boot to Kubuntu 8.04.  Neither the NIC nor wireless card are being recognized.  The wirless card is a Ralink.  I'd appreciate any advice on how to work around this issue.  (I won't be able to actually try anything for another couple of days.  I will be back Monday July 21)

Thanks in advance

Could you post the output of either command listed below.

```
lshw -short
```

```
lspci -nn
```

Here are some guides that may help you with your ralink device.

[WiFiHowTo]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo")
[WifiDocs-RalinkRT2500]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500")
[WifiDocs-RalinkRT73]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73")

---

### Post by kuja on 2008-07-18
> **fletc900 said:**
> Hi there, 

I just got an HP Pavilion Elite PC m9340f. This is an Intel Core 2 Quad Core processor Q6700 with 6 GB of ram; this is my first 64-bit machine. The system comes with an onboard LAN which seems to be incompatible with Linux. The worst thing about this computer is that all the expansion ports (PCI) have been occupied. There is Windows Modem on the PCI-32 port which I won't use. I was thinking about getting a new [network card (link)]("http://www.bestbuy.com/site/olspage.jsp?skuId=3195642&st=Network+Card+PCI&lp=1&type=product&cp=1&id=1051384122901") an place it on the PCI-32 port. My question is: would a ubuntu 64 have any problems recognizing a network card on a [COLOR="Red"]PCI-32[/COLOR] port? 


Here are the specs for the machine: [link]("http://reviews.cnet.com/desktops/hp-pavilion-elite-m9340f/4507-3118_7-33109780.html").


I appreciate your help.

:confused:

I personally wouldn't go with that card ... if you go somewhere else, probably somewhere like newegg online you could get a better card for about the same price. The Intel 10/100/1000  NICs seem to be fantastic.

---

### Post by justtrying on 2008-07-19
I also bought the same computer, the problem is that, the network chip on the motherboard is made by realtek, it is a newer chip than what is being supported (model: r8168 ),and even though realtek has a linux driver on thier site, for some reason it does'nt install correctly, so i searched goole and it took me some time to finnaly make it work..These are the instructions that i found that helped me, just download the drivers first then copy and past the commands in your terminal:
1 - Downloaded current driver from :
[http://www.realtek.com.tw/downloads/...&GetDown=false](http://www.realtek.com.tw/downloads/...&GetDown=false)
2 - Unpacked on the Desktop
3 - $ sudo mv r8168-8.006.00 /usr/src
4 - $ cd /usr/src/r8168-8.006.00
5 - $ sudo make clean modules
6 - $ sudo make install
7 - $ sudo depmod -a
8 - $ sudo insmod ./src/r8168.ko
9 - $ lsmod -a | grep 8186 #just to check it was there
10 - $ cd /etc/modprobe.d
11 - $ sudo touch blacklist-network
12 - $ vi blacklist-network # add "blacklist r8169" to the file
13 - $ sudo update-initramfs -u #to make the change permanent
14 - reboot
15 - ethtool -i eth0 #to see new driver assigned
don't gorget to ghange the number for the driver if you down load a newer driver.
As far as the wireless i have not tried but the linkes mentioned above should help,  the ting that is driving me crazy is no matter what i do i can not get the tv card to work at all even after installing the mercurial v4l drivers
It is a good machine but i hat the case and the lack of expansion slots, you almost can't do anything to upgrade that machine
BTW, i also had to use Envy to install the latest Nvidia driver because the resticted drivers that came with Ubuntu do not support 9600 chip
wish you good luck, and if anybody knows how to get that tv card to work pleeease help

---

### Post by DRomeo521 on 2008-07-21
Justtrying, thanks for the advice.  I'm held up at step 5 though.  I get some errors...

dan@dan-kubuntu:/usr/src/r8168-8.006.00$ sudo make clean modules
make 

-C src/ clean
make[1]: Entering directory `/usr/src/r8168-8.006.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers rset
make[1]: Leaving directory `/usr/src/r8168-8.006.00/src'
make -C src/ modules
make[1]: Entering directory `/usr/src/r8168-8.006.00/src'
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
scripts/Makefile.build:41: /src/Makefile: No such file or directory
make[3]: *** No rule to make target `/src/Makefile'.  Stop.
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/r8168-8.006.00/src'
make: *** [modules] Error 2
dan@dan-kubuntu:/usr/src/r8168-8.006.00$


I'm not sure what to do from here.  Any ideas?

Thanks

---

### Post by DRomeo521 on 2008-07-21
> **John.Michael.Kane said:**
> Could you post the output of either command listed below.

```
lshw -short
```

```
lspci -nn
```

Here are some guides that may help you with your ralink device.

[WiFiHowTo]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo")
[WifiDocs-RalinkRT2500]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500")
[WifiDocs-RalinkRT73]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73")

Thanks for the websites

---

### Post by justtrying on 2008-07-23
I remember getting stuck at the same step(its been a while),don't remember exactly what i did, but i think i had to change the working directory for that command to:
/usr/src/r8168-8.006.00/src
instead of 
/usr/src/r8168-8.006.00
as suggested by,realtek,in step 4 
To be truthful, i don't remember if i did that only for step 5 or in other steps too,but i think it was only for step 5.
Try it only for #5 first,if that doesn't work, search for "r8168.ko",after you hopefully finish step#7 r and use that module's path, when you get to step#8
Good luck,

---

### Post by DRomeo521 on 2008-07-23
Problem Solved.  This thread has it all...

[http://ubuntuforums.org/showthread.php?t=799662](http://ubuntuforums.org/showthread.php?t=799662)

Including a link to... [http://www.jamesonwilliams.com/hardy-r8168.html](http://www.jamesonwilliams.com/hardy-r8168.html)

Thanks for pointing me in the right direction justtrying.  I just needed to install patch from the cdrom, and everything fell into place.

---

### Post by justtrying on 2008-07-24
I am glade you got it working. actually this onboard card is not a bad performer.

---

### Post by maximus659 on 2008-08-27
did anyone get the wireless to work?  Please help.

---

### Post by katzer1 on 2008-09-03
Hi all, 
this is my first post to this forum.
I came across this great forum while working on making my new hp m9340f to play nicely with ubuntu.
After a fresh install (I blew away the windows partition first thing), the state was loud fan noise, 800x600 resolution and no networking.

For wired network, the following instructions were spot on:
[http://www.jamesonwilliams.com/hardy-r8168.html](http://www.jamesonwilliams.com/hardy-r8168.html)

For wireless, I followed the instructions here:
[http://ubuntuforums.org/showthread.php?t=683085&page=5](http://ubuntuforums.org/showthread.php?t=683085&page=5)
Take a close look at post 41 and 47.
To make sure I could update "buid-essentials" I had to use the wired connection. Once everything was updated, I followed post 41 and since the my wireless connection works fine.

Last but not least, you would need the NVIDIA driver ([www.nvidia.com](www.nvidia.com)).
I was told that you also get the package called nvidia-glx or something like that, I haven't tested it yet. I downloaded the driver, booted into root shell, ran the installer (didn't mind the warning about level 1, it was the only way I knew to get it to start without X11).

The procedure worked smoothly, and the fan on the video card calmed down and now things are nice and quite.

Question:
The ralink rt2860 is wireless draft-n but I was only able to get it running at 54G. Is it possible to have it running at draft-n speed on linux?

Cheers,

 Erez

---

