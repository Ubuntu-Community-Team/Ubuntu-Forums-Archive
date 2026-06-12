---
title: "Booting to command line after enableing Nvidia GFX drivers"
date: 2009-07-13
forum: x86 64-bit Users
---

### Post by Kjeksr on 2009-07-13
So i instaled ubuntu 9.04 64bit on my desktop. everything went fine during instal and had no problems whit instaling flash and codecs. But when i downloaded the Nvidia drivers for my GFX cards something wierd happend (instaled them through the driver manager or whatever its called). when i did the necesary reboot i got the loading screen and when it had loaded i did not get any interface. instead i got this:
> [I]19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/byuuid(oec613ed-bb2d-438b-a00e-14ece932e5cb) = dev(8,5)
Kinit: trying to resume from /dev/disk/byuuid(oec613ed-bb2d-438b-a00e-14ece932e5cb
kinit: No resume image, doing normal boot..[/I]then i where able to login through the command line and got some basic info like last login, instaled version of ubuntu, that the software included are free, no warranty and where to find documentation. after that i just the command line.

it could be that i messed whit some setting while configing but as i where able to boot into the interface using the Ubuntu 9.04, kernel 2.6.28-11-generic. and get exactly the same result when enabeling the GFX drivers, which to me seems like a problem whit the drivers not the config? or could it be that im running SLI? so whould taking out the second card make any sense? And is there a way for me to boot into the UI whitout reinstaling (some comand to disable the drivers?)

Comp specs:
CPU: Amd64 6000+ Dualcore
MOBO: MSI K9N SLI Platinum
RAM: 2x Crucial DDR2 BallistX PC6400 2GB CL4 in dual channel
GFX: 2x XFX GeForce 9800+
HDD: 1x 250GB Sata 7200RPM (formated during install) 1x 500GB Sata 7200RPM (NTFS) 1x 750GB Sata 7200RPM (NTFS)

---

### Post by unutbu on 2009-07-13
I don't have enough knowledge or confidence to help you directly, but I think you would benefit from reading this excellent guide: [http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)
Near the end it tells you commands to run if X fails to start (which is what I believe is happening to you). Then post the nvidia-bug-report.log.gz in the above thread and hopefully you will get more knowledgable help.

---

### Post by Kjeksr on 2009-07-13
Did the 
```
grep -n "^(EE)" /var/log/Xorg*log
```and got```
/var/log/Xorg.0.log:134:(EE) No devices detected
/var/log/Xorg.failsafe.log:131:(EE) No devices detected
```Does that mean that Xorg doesnt recognice my GFX cards? Or could it be me doing it wrong? meaning i have no idea what a tty console is, so i did it in the command line.

Edit:
Seems the tty thingy is what i refer to as the command line if i understod [http://en.wikipedia.org/wiki/Virtual_console_(PC)]("http://en.wikipedia.org/wiki/Virtual_console_%28PC%29") correct

---

### Post by b.a.w on 2009-07-13
Could you post your /etc/X11/xorg.conf file?

---

### Post by Kjeksr on 2009-07-13
If you could tell me how to get it. As when i do the ```
/etc/X11/xorg.conf
``` command i get "no such file or directory"

---

### Post by b.a.w on 2009-07-13
Hit Alt + F2 and type

```
gedit /etc/X11/xorg.conf 
```

That will open a read only version in gedit. Copy and paste that.

---

### Post by Kjeksr on 2009-07-13
> **b.a.w said:**
> Hit Alt + F2 and type

```
gedit /etc/X11/xorg.conf 
```That will open a read only version in gedit. Copy and paste that.

doesnt work. when i use that command i get ```
 (gedit:5621): Gtk-WARNING **: cannot open display
```

---

### Post by b.a.w on 2009-07-13
Oh duh. You don't have an x-server so running that isn't going to work. Run

```
nano /etc/X11/xorg.conf
```Find the devices section and see if it says something about Nvidia.

If it doesn't run as root

```
nvidia-xconfig
```that should configure xorg.conf to work.

---

### Post by Kjeksr on 2009-07-13
The 
```
/etc/X11/xorg.conf
``` file is just a blank file. no info in it. doing the 
     Code:
     ```
nvidia-xconfig
``` gives me an Vadlidation error: data incomplete + Error unable to write to directory

---

### Post by dagrump on 2009-07-13
Look for "GUI doesn't load after installing nvidia drivers" it's on the 2nd page half way down. It will tell you what to do.

---

### Post by Kjeksr on 2009-07-13
> **dagrump said:**
> Look for "GUI doesn't load after installing nvidia drivers" it's on the 2nd page half way down. It will tell you what to do.

Tryed both methods suggested in that post and neither works. whne i tryed the  envyng thingy at the last step```
startx
``` i got an "Fatal server error: no screens found" and then some info about where to get help. then i get this message:```
ddxSigGiveUp: Closing log
giving up
xinit: No such file or directory (errno 2): unable to connect to X server
xinit: No such process (errno 3): Server error.
```at the Xorg config file every time i config the file there seems to be some kind of error when trying to use```
sudo nvidia-xconfig
``` which states that one of the lines contains an error. which is probably caused by the difference in cards me and the guy who suplied the file has. and as i have no idea about how to config the file to my needs im stil stuck.

Edit:
Removing the second Card worked. But id be verry happy if anyone could help me getting the SLI to work

---

### Post by dagrump on 2009-07-13
No, you can't just use my xorg file, you needed to create your own. Then make the modifications to the device section. Just add the BusID line to tell them machine which card to use & Option "SLI" "SFR" line.

---

### Post by Kjeksr on 2009-07-13
> **dagrump said:**
> No, you can't just use my xorg file, you needed to create your own. Then make the modifications to the device section. Just add the BusID line to tell them machine which card to use & Option "SLI" "SFR" line.

Thanks for you help, got it working now :D

---

### Post by dagrump on 2009-07-13
Good for you:)

---

