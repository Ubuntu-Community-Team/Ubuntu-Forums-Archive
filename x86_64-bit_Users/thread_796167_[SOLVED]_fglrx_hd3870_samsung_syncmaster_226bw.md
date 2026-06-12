---
title: "[SOLVED] fglrx hd3870 samsung syncmaster 226bw"
date: 2008-05-16
forum: x86 64-bit Users
---

### Post by cemelmaci on 2008-05-16
Hi,

i have in my new computer ubuntu hardy installed.And fglrx ati-driver-installer-8-4-x86.x86_64.run driver installed. But X-server hang on login screen.

my confugration is

sapphire hd3870 512 mb,
samsung syncmaster 226bw,
asus maximus formula se,
quad core 9300,
4 gb ocz ram.(maybe later 8 gb)

thanks

---

### Post by Yellow Pasque on 2008-05-16
How did you install the driver? Did you follow this guide? [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

To get past the hang, press Ctrl+Alt+F1 to get to the terminal and run:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Kilz on 2008-05-16
I am experiencing a similar issue, but it only hangs 1 out of 10-15 boot ups. I have a ati card and a syncmaster 920nw. The keyboard becomes unresponsive so I end up doing a hard boot.

---

### Post by soxs on 2008-05-17
I own a radeonhd 3870 aswell. I use the driver from the repos and it runs pretty fine.
Attached my xorg.conf, DO NNOT copy it completly, this will end up in a black screen

---

### Post by kingtaurus on 2008-05-19
Can you post the specs of your system. The following are important:
Motherboard (Brand + ID)
Amount of Memory
CPU

(I don't think this is an issue with your monitor).

Please also post the following:
/var/log/Xorg.log
/var/log/dmesg

---

### Post by DaTLS on 2008-05-19
I have the same problem. After installing Ubuntu x86_64 (Hardy) everything is fine, after installing the fglrx driver, there is nog login screen until I go to the recovery mode en do xfix.

I tried the following installations:
[LIST]
[*]Popup Message after install for the driver (System > Administration > Hardware Drivers)
[*]Running the ATI installer (ati_etc_etc.run)
[*]Creating a package using the guide for [ATI Driver on Gutsy](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-117effcb5f0fbe8e10f40881bff1dbf7824a77b0)
[*]Installing the driver through Envy
[/LIST]

All result in the same, no more login screen, i run xfix, after normal login I get a complete White Screen (of Doom!). I do Alt+Ctrl+Backspace and go for the Failsafe Gnome.

System specs:
[LIST]
[*]Intel Core 2 Quad,Q9450
[*]Team Elite,1024MB, DDR2. PC6400, 800MHz, 4x
[*]MSI RX3870-T2D512E-OC,512MB, GDDR4, PCI Express x16
[*]GigaByte GA-EX38-DS5,Retail
[/LIST]

Next I'm going to try the in this thread advised:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Let's hope someone has a solution, cause I'm almost thinking about installing windows ...

---

### Post by kingtaurus on 2008-05-19
**DaTLS**
> I get a complete White Screen
I think this is an issue with compiz (assuming that your keyboard is still responsive (i.e. numlock still works). Try the following:
<alt>-F2 metacity --replace <return> (if using gnome)
<alt>-F2 kwin --replace <return> (if using kde)

Although, if the lock up causes the keyboard to be unresponsive you may have to disable memory mapping or fiddle with your mtrr settings (not familiar with this ... but there are other threads which discuss this).

**cemelmaci**
> asus maximus formula se
Can you try the following, in the bios disable memory mapping (it should be under north bridge configuration (I think). With this disable you will only have access to about 3.3 GB of memory (instead of 4GB) but the drivers will still work (If you need to have 4GB of memory ... you can always try editting your mtrr settings).

---

### Post by kingtaurus on 2008-05-21
I've looked through your log files and I think the issue is related to this:
(WW) RADEON(0): Failed to set up write-combining range (0xd0000000,0x10000000)

I think this is due to mtrr not being configured properly when the BIOS does memory remapping (or whatever its called in your BIOS ... its related to PCI devices and how the kernel address them -- if I recall properly).

see: [http://ubuntuforums.org/showthread.php?t=768426]("http://ubuntuforums.org/showthread.php?t=768426")
[http://ubuntuforums.org/showthread.php?t=770205]("http://ubuntuforums.org/showthread.php?t=770205")

> **DaTLS said:**
> I have the same problem. After installing Ubuntu x86_64 (Hardy) everything is fine, after installing the fglrx driver, there is nog login screen until I go to the recovery mode en do xfix.

I tried the following installations:
[LIST]
[*]Popup Message after install for the driver (System > Administration > Hardware Drivers)
[*]Running the ATI installer (ati_etc_etc.run)
[*]Creating a package using the guide for [ATI Driver on Gutsy](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-117effcb5f0fbe8e10f40881bff1dbf7824a77b0)
[*]Installing the driver through Envy
[/LIST]

All result in the same, no more login screen, i run xfix, after normal login I get a complete White Screen (of Doom!). I do Alt+Ctrl+Backspace and go for the Failsafe Gnome.

System specs:
[LIST]
[*]Intel Core 2 Quad,Q9450
[*]Team Elite,1024MB, DDR2. PC6400, 800MHz, 4x
[*]MSI RX3870-T2D512E-OC,512MB, GDDR4, PCI Express x16
[*]GigaByte GA-EX38-DS5,Retail
[/LIST]

Next I'm going to try the in this thread advised:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Let's hope someone has a solution, cause I'm almost thinking about installing windows ...

---

### Post by cemelmaci on 2008-05-21
this is my Xorg.log file.
yes i need to have 4GB of memory and my graphic card for blender, 
how can i editting to my mtrr settings?

---

### Post by kingtaurus on 2008-05-21
I think this is discussed in this thread: [http://ubuntuforums.org/showthread.php?p=4766662]("http://ubuntuforums.org/showthread.php?p=4766662"). However I haven't done this myself (since I'm okay with using 3.3 GB of memory).

---

### Post by cemelmaci on 2008-05-23
thanks. Problem solved.> **kingtaurus said:**
> I think this is discussed in this thread: [http://ubuntuforums.org/showthread.php?p=4766662]("http://ubuntuforums.org/showthread.php?p=4766662"). However I haven't done this myself (since I'm okay with using 3.3 GB of memory).
```
echo "disable=2" >| /proc/mtrr
echo "disable=1" >| /proc/mtrr
echo "disable=3" >| /proc/mtrr
echo "disable=4" >| /proc/mtrr
echo "disable=0" >| /proc/mtrr
echo "base=0x00000000 size=0x80000000 type=write-back" >| /proc/mtrr
echo "base=0x80000000 size=0x40000000 type=write-back" >| /proc/mtrr
echo "base=0xC0000000 size=0x10000000 type=write-back" >| /proc/mtrr
echo "base=0x100000000 size=0x20000000 type=write-back" >| /proc/mtrr
echo "base=0x120000000 size=0x10000000 type=write-back" >| /proc/mtrr
```

---

