---
title: "Bring Back Screens and graphics Please!"
date: 2008-11-13
forum: x86 64-bit Users
---

### Post by cochingeek on 2008-11-13
My sony LCD was working in full resolution of 1280x1024 (Nvidia -gforce 8600GT)in Hardy64x with the help of screens and graphics menu where you could manually show the LCD monitor.In 8,10 intrepid screens and graphics menu is not there. My Sony LCD 17" is now identified as CRT monitor and I get a max resolution of 1024x968. You have to have back screens and graphics menu at least for people like me. ( please note that my Nvidia 177 driver is active).Please bring back Screens and Graphics menu. ....Hope somebody out there hears...

---

### Post by prshah on 2008-11-13
> **cochingeek said:**
> .Please bring back Screens and Graphics menu. 

First, install it, either by [clicking here]("apt://displayconfig-gtk"), or by opening a terminal (Applications-Accessories-Terminal) and giving the command```
sudo apt-get install displayconfig-gtk
```

Then, press Alt+F2, and give the command ```
gksudo displayconfig-gtk
``` and you should have your favorite "screens and graphics perperties" window.

---

### Post by cochingeek on 2008-11-13
But I get, 


> unni@Ibex64x:~$ sudo apt-get install displayconfig-gtk
[sudo] password for unni: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package displayconfig-gtk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package displayconfig-gtk has no installation candidat

---

### Post by prshah on 2008-11-13
> **cochingeek said:**
> But I get,

Ok apparently it is deprecated for Hardy and cannot be installed. ```
sudo apt-get --download-only --reinstall install displayconfig-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of displayconfig-gtk is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

I guess it's available for me since I upgraded from Hardy->Intrepid Beta->Intrepid RC->Intrepid.

You will probably have to download the .deb from elsewhere.. 

This raises an interesting point.. what do you use in Intrepid as a replacement for displayconfig-gtk?

---

### Post by cochingeek on 2008-11-14
**Ok, I was able to bring back Screens and Graphics menu into Intrepid 64x.**
 First I downloaded and installed guidance-backends(amd64) from
 [http://packages.ubuntu.com/hardy/amd64/guidance-backends/download]("http://packages.ubuntu.com/hardy/amd64/guidance-backends/download")   

 Then I downloaded and installed displayconfig-gtk (all) from
    [http://packages.ubuntu.com/hardy/all/displayconfig-gtk/download]("http://packages.ubuntu.com/hardy/all/displayconfig-gtk/download")

Now the screens and graphics menu came in the "others" section in Main Menu.
I  showed my sony LCD manually in screens and graphics and set the resolution to 1280x1024 and 75Hz

System was restarted and I now get the full resolution of 1280x1024.

 n.b -thanks prshah for all the tips and giving me the idea..

---

### Post by xen-uno on 2008-11-14
> **prshah said:**
> ... This raises an interesting point.. what do you use in Intrepid as a replacement for displayconfig-gtk?

Wouldn't that be System>Preferences>Screen Resolution? It can also be changed with System>Administration>NVidia X Server Settings if NVidia's proprietary driver is installed.

---

### Post by dsiembab on 2008-12-07
You would think so but it will not if you have an old monitor and doing what cochingeek did, sure does help others out. If you have an old monitor that is not picked up by System>Preferences>Screen Resolution and it leaves you with no choice of selecting a display driver that can sort of match your monitor.

---

### Post by And1945 on 2009-01-05
> **xen-uno said:**
> Wouldn't that be System>Preferences>Screen Resolution? It can also be changed with System>Administration>NVidia X Server Settings if NVidia's proprietary driver is installed.

Its not intirely the same. Im running 2 computers via a kvm switch. I could always make it install my compaq p1220 crt monitor, but the leaving of "Screens and graphic" has left me no real way of doing this. But I will try prshah's method, once my aptitude has done its updating. 2 synaptics at once .... :)

---

### Post by dsiembab on 2009-01-05
I'm using an antique compaq presario monitor from 1997, wouldn't find it. :lol:

---

### Post by mhcare on 2009-01-05
I came to learn about.

---

