---
title: "Installing ATI drivers for HD4870 !!!Please Help!!!"
date: 2008-09-10
forum: x86 64-bit Users
---

### Post by RiPPeR777 on 2008-09-10
I used envyNG to install the ATI drivers and the auto config wouldn´t recognize my ATI HD 4870. So I did a manual install with the 8.6 drivers it had. I then restarted my comp and it worked a little. Ubuntu 8.04 recongnized that i had an ATI Card in my comp but did not enable 3D acceleration. when I turned on the 3D acceleration and restarted, Ubuntu didnt recongzied my video card anymore and ask me to pick a different driver. So i pick fglx thinking it should work. wrong! it only let memy screen go 800 x 600 and dont even think it uised the drivers.can anyone help!!!!!!!!!!!!!!!

---

### Post by Kilz on 2008-09-10
> **RiPPeR777 said:**
> I used envyNG to install the ATI drivers and the auto config wouldn´t recognize my ATI HD 4870. So I did a manual install with the 8.6 drivers it had. I then restarted my comp and it worked a little. Ubuntu 8.04 recongnized that i had an ATI Card in my comp but did not enable 3D acceleration. when I turned on the 3D acceleration and restarted, Ubuntu didnt recongzied my video card anymore and ask me to pick a different driver. So i pick fglx thinking it should work. wrong! it only let memy screen go 800 x 600 and dont even think it uised the drivers.can anyone help!!!!!!!!!!!!!!!
[URL="https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_86_linux.html"]
The 8.6 drivers [/URL]did not support the 4800 series. [The 8.8 says]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_88_linux.html") they support the 4800series. [Perhaps this can help.]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.8.29")

---

### Post by RiPPeR777 on 2008-09-10
thank you for your response and your input. i will try that and reply with and answe. if it worked or not.

---

### Post by PranaNZ on 2008-09-10
Hi,

If your still having problems I found the following very useful.

[http://www.phoronix.com/forums/showthread.php?t=11752](http://www.phoronix.com/forums/showthread.php?t=11752)

I have a HD4850 and used the following install method mentioned by Melcar.  One of the biggest problems was being able to get to the continue button with the auto installer.  I ended up rebooting the computer and at the Grub installer used the recovery mode to allow me to run a better resolution.  I also did not have much success loading the Ubuntu/ hardy specific driver, just used the generic one on the Ati installation page.  I'm pretty new at this, so I'm sure someone else will come up with some better solutions, but at the end of the day it got me up and running!!
Good luck

---

### Post by soxs on 2008-09-11
I am running a Radeon HD 4870 aswell with 8.8. (**[COLOR="SeaGreen"]EDIT: ETQW works with 8.8 now, just personal dumbness, go for 8.8 now![/COLOR]**)

My generic [personal] install method(Note: basic commandline knowledge required):
Required build stuff:
```
sudo apt-get install cdbs build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-$(uname -r)
```
Get the installer from the ati/amd-page.
*_Tipp:_* Move it in a seperate directory, so you can install the resulting packages a lot easier.
Make ati driver installer executable:
```
sudo chmod +x /path/to/installer/...run

```
Build distro specific packages:
```
sudo /path/to/installer/...run --buildpkg Ubuntu/hardy
```
In case you moved the installer to a seperate dir, type:
```
sudo dpkg -i *.deb
```
If not, install them by doubleclicking in the correct order... (hf while checking the dpendencies on each other ;-) )

Done so far: Now you have to edit your /etc/X11/xorg.conf either by hand or with the atitool.
*_Note:_* It won't work unless you you setup your xorg.conf correctly!
See ```
man xorg.conf
``` and/or ```
http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide
``` which you should bookmark ;-)

---

### Post by Reugen on 2008-09-11
What happens when you try and run etqw?? following the instructions mentioned here [http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide") etqw works just fine with my 4870x2. With quake4 I did have to reset everything to default then raise settings without AA, otherwise it would crash.  See here: [http://www.rage3d.com/board/showthread.php?t=33929548]("http://www.rage3d.com/board/showthread.php?t=33929548")

hope that works :)

---

### Post by soxs on 2008-09-12
> **Reugen said:**
> What happens when you try and run etqw?? following the instructions mentioned here [http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide") etqw works just fine with my 4870x2. With quake4 I did have to reset everything to default then raise settings without AA, otherwise it would crash.  See here: [http://www.rage3d.com/board/showthread.php?t=33929548]("http://www.rage3d.com/board/showthread.php?t=33929548")

hope that works :)

Wow, umg.. when I tried to run etqw at my normal ultimate settings, it didn't even start. So I deleted $HOME/.etqw* and after that brute force settings reset, it at least ran again, but as soon as I tried to change the graphical settings (like resolution or quality) I get heavy screen corruption and have to either blindly exit or kill it.

---

### Post by artkochermin on 2008-09-12
Hi guys,

I actually found that 8.8 Catalyst drivers worked for me when I just followed ATI instructions. I didn't even have to build a specific package. With that said, it worked for 8.7 too, but I couldn't run ETQW before. ETQW ran fine with 8.8. Just today I tried following this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.8.29](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.8.29)
and I don't see the difference yet in these 2 methods(except CCC is in a different place).

I do have few issues though that I'd like to ask you about:
1) I get quite high idle temperature. Even after I play ETQW for a while, the temp only goes up by 3-4 degrees
aticonfig --odgt

Default Adapter - ATI Radeon HD 4800 Series
                  Sensor 0: Temperature - 81.00 C
2) I get some strange humming noise from the card when it idles. The period of a humming cycle is about 1-2 seconds. Mind you I had my card for over a month now and it works fine, but I think the fan control is kinda messed up. During computer power up and usually 3-5 minutes after I hear this loud fan noise for about 2-3 seconds. Do you have any ideas on what's going on?

Thanks
Artur

---

### Post by artkochermin on 2008-09-12
Hi soxs,

What do you get if you run etqw from the terminal. Do you see any errors or warnings. I had problems running etqw with 8.7 Catalyst driver. I think the game was looking into some folder that didn't exist and it only reported 128MB of my 512Mb VRAM.

Artur

---

### Post by soxs on 2008-09-12
> **artkochermin said:**
> Hi soxs,

What do you get if you run etqw from the terminal. Do you see any errors or warnings. I had problems running etqw with 8.7 Catalyst driver. I think the game was looking into some folder that didn't exist and it only reported 128MB of my 512Mb VRAM.

Artur

Thx, but lets shift that problem to this thread: [http://ubuntuforums.org/showthread.php?t=902624](http://ubuntuforums.org/showthread.php?t=902624)

---

### Post by abi.allan on 2008-10-21
sure man, why not...

i ill explain you clearly...

all are plucking me here.....

ill send it massonn syea really nice....

---

### Post by scantraxx95 on 2009-10-20
!!please help!! i have the drivers but its not in use. what should i do

---

