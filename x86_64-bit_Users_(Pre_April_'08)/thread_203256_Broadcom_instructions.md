---
title: "Broadcom instructions?"
date: 2006-06-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-06-24
I am now on my sixth reformat, reinstall, try again of Dapper on my Compaq R3240 amd64 laptop. This laptop ran Breezy for about six months and everything worked, including wifi with ndiswrapper. (OK, I had to chroot Firefox, Realplayer and Adobe Reader, but they WORKED.) 

I made a fresh install of Dapper on an unused portion of the hard drive. I played around with it for a while and was happy. Then I decided to do any upgrade of my Breezy. That resulted in a Breezy that will no longer boot, due to unmet dependencies. I'm going to have to wipe it out and start fresh. (I do have complete backups.)

Before wiping out Breezy and starting fresh in its old partition I decided to take my new fresh Dapper and be sure that wifi would work. That was six reinstalls ago. Everything I have tried results in a system that hangs on booting. Mouse and keyboard both dead. Recovery mode might help if there were some error messages that would give me a clue what is wrong. The only thing I know is that this always happens after I try to get the Broadcom 4306 working.

I found these instructions and read all the way through them, but can't find anywhere that it says they are for 64-bit or 32-bit Ubuntu. Hence, I must assume they are for 32-bit:

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

Before I end up with one more dead install, can some kind person please point me to the CORRECT instructions for getting a Broadcom 4306 working in Dapper-64?

---

### Post by devan on 2006-06-25
[QUOTE=John Jason Jordan]I am now on my sixth reformat, reinstall, try again of Dapper on my Compaq R3240 amd64 laptop. This laptop ran Breezy for about six months and everything worked, including wifi with ndiswrapper. (OK, I had to chroot Firefox, Realplayer and Adobe Reader, but they WORKED.) 

I made a fresh install of Dapper on an unused portion of the hard drive. I played around with it for a while and was happy. Then I decided to do any upgrade of my Breezy. That resulted in a Breezy that will no longer boot, due to unmet dependencies. I'm going to have to wipe it out and start fresh. (I do have complete backups.)

Before wiping out Breezy and starting fresh in its old partition I decided to take my new fresh Dapper and be sure that wifi would work. That was six reinstalls ago. Everything I have tried results in a system that hangs on booting. Mouse and keyboard both dead. Recovery mode might help if there were some error messages that would give me a clue what is wrong. The only thing I know is that this always happens after I try to get the Broadcom 4306 working.

I found these instructions and read all the way through them, but can't find anywhere that it says they are for 64-bit or 32-bit Ubuntu. Hence, I must assume they are for 32-bit:

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

Before I end up with one more dead install, can some kind person please point me to the CORRECT instructions for getting a Broadcom 4306 working in Dapper-64?[/QUOTE]

Hey there. I'm brand new to Ubuntu (3 days) and I have the exact same laptop as you. I got wifi to work fine in both 64-bit and 32-bit builds of Ubuntu on this laptop.

All I had to do was:

sudo apt-get install bcm43xx-fwcutter

after installing that, i ran the script provided:

sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh

After this step, I could successfully enable eth1 (my wireless adapter) under System -> Networking. I entered my SSID, WEP Key, and Static IP fine as well.

I have to run one more command at every reboot however:

sudo iwconfig eth1 ap any

My wireless card will connect to my router fine, but cannot surf until I type that command. A little bit of a hassle, but not considering how frustrating these cards can be at times!

I realize you may have tried all this already, but it worked fine for me, with the same laptop.

I have a question for you too... were you able to successfully load drivers for the modem? I use dialup the odd time when I am at the lake, and haven't been able to get ANY success with this.

Cheers!

---

### Post by John Jason Jordan on 2006-06-25
[QUOTE=devan]Hey there. I'm brand new to Ubuntu (3 days) and I have the exact same laptop as you. I got wifi to work fine in both 64-bit and 32-bit builds of Ubuntu on this laptop.
I have to run one more command at every reboot however:

sudo iwconfig eth1 ap any

My wireless card will connect to my router fine, but cannot surf until I type that command. A little bit of a hassle, but not considering how frustrating these cards can be at times!
I realize you may have tried all this already, but it worked fine for me, with the same laptop.
I have a question for you too... were you able to successfully load drivers for the modem? I use dialup the odd time when I am at the lake, and haven't been able to get ANY success with this.Cheers![/QUOTE]
First, since I posted that I got it running. I had spent half the day trying everything in every forum and all I managed to do was get the computer to freeze up and then hang on rebooting. I reinstalled so many times I lost count. Then I saw a command I hadn't tried yet -- "sudo modprobe bcm43xx." It didn't give me any error messages when I ran it. I rebooted, opened Network Settings, and there was my Wireless Connection, listed as eth1 and ACTIVE!! Not only that I can reboot without hanging. I may have hit the magic key here. Of course, I have done so many things before running that command that who knows if something else needed to be done and I just happened to have done it.

I might add that when I reboot it is still right there, active, and without needing to do any additional commands.

I should also add that this happened at about 9 pm here, and I don't have wifi at home, so no way to test it. Tomorrow I will take the computer to the university to see if it really works. EVERYONE CROSS YOUR FINGERS FOR ME!!

As for the modem, I have never bothered with it. I have cable at home and wifi at the university and everywhere else, so I have no need of dialup. It might be useful for receiving and sending faxes, but I hate faxes, so I just tell people I don't have a fax machine and they'll have to e-mail me. That also eliminates the problem of getting on junk fax lists. About three or four times a year I really need to send someone a fax, in which case I stop and a quick-print shop and give them a few coins to do it for me.

Still, if you do ever get it working, post back. It might be handy some day. I think I remember reading some posts about it. Unfortunately, I did not bookmark them. :(

After being sure the wifi is working tomorrow, I'm going to install the Nvidia video driver so I can watch movies. The open source driver works just as well for everything except playing movies. What I love about this computer more than anything is the 1680 x 1050 15.4 inch widescreen. People walking by just stare at the screen it's so beautiful. 

Time for bed. I'll post back with the results of tomorrow's journey to the university.

---

### Post by John Jason Jordan on 2006-06-25
[QUOTE=John Jason Jordan]... this happened at about 9 pm here, and I don't have wifi at home, so no way to test it. Tomorrow I will take the computer to the university to see if it really works. EVERYONE CROSS YOUR FINGERS FOR ME!![/QUOTE]
OK, bad day. Went to the university, but it does not work.

To refresh everyone's memory, I had tried all kinds of things, none of which worked. Then I saw a post where someone had done "sudo modprobe bcm43xx." Since I had't tried that before, I did. And afterwards the wifi was listed as Active when I opened System > Administration > Networking.

I went to the university today where there is wifi just about everywhere. I opened System > Administration > Networking and in the Network Settings dialog box I selected "Wireless connection." Then I clicked on Properties, because usually one has to see the university wifi system and click to connect to it. But this time, the instant I clicked on Properties, something totally hung the computer. No keyboard, no mouse, nada. The only button that still worked was the power button. To get out I had to power down and then reboot. I tried several more things, but nothing worked. The instant I clicked on Properties, the computer hung.

Back to the drawing board.

---

### Post by John Jason Jordan on 2006-06-26
Well, duh! Sometimes I can be so stupid! I found the solution:

sudo rmmod ndiswrapper

Works fine now. I love Dapper!

---

### Post by devan on 2006-06-27
[QUOTE=John Jason Jordan]Well, duh! Sometimes I can be so stupid! I found the solution:

sudo rmmod ndiswrapper

Works fine now. I love Dapper![/QUOTE]

congrats! glad its working. how did the install of the nvidia driver go? do you have the Geforce 4 440 Go 64 Meg card on that machine?

---

### Post by John Jason Jordan on 2006-06-27
[QUOTE=devan]congrats! glad its working. how did the install of the nvidia driver go? do you have the Geforce 4 440 Go 64 Meg card on that machine?[/QUOTE]
Aaah, not there yet. More problems with wifi to solve first.

Originally I had Breezy-64 on a 60 GB partition and 20 GB unused space. I use 8 GB of the free space for a fresh install of Dapper-64 as a test bed. That's the one I got wifi working on.

Having satisfied myself that everything would go well, U used "sudo apt-get dist upgrade" to upgrade the Breezy-64 installation to Dapper-64. Big mistake. I ended up with a hopelessly broken installation. Will boot, but with lots of error messages and X won't come up. Unmet dependencies, chiefly with ia32-libs. I read everything here but all the stuff that worked for everyone else did not work for me. Eventually I reformatted the Breezy-64 partition and just installed another copy of Dapper-64 as a fresh, new installation. That was several hours ago. And I can't get the wifi working. I got it working on the test bed installation, but it won't go on this one. I followed the instructions here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

The strange thing is that it's doing exactly what the last one did -- I can activate it, I can sudo modprobe bcm43xx and I don't get any error messages, yet the instant I select the wireless and then click on Properties, it locks the computer up tight. Have to hit the power button. Now, last time it was because ndiswrapper was also running, so it got all confused. But this time ndiswrapper has never been installed. If I sudo modprobe ndiswrapper it gives me an error message that there is no such module. So I know it's not the problem this time.

So here I sit, trying to figure it out. In the meantime I've been reinstalling programs and recovering my personal config files from the test installation. I've got most of that done. Tomorrow morning after the first cup of coffee kicks in I'll tackle the wireless again. Maybe overnight my brain will dream up the solution.

Then I'll use Automatix for most of the rest. It worked perfectly last time. And yes, I do have the same video card. It really turns heads when people see it in 1680 x 1050 on a 15.4 inch widescreen.

---

### Post by devan on 2006-06-27
thats weird dude. sorry to hear all the troubles you are having. i don't know why it worked so easily for me both times ive installed ubuntu. like i said all i had to do was type those three commands and i was up and running both times.

i went to install the nvidia driver yesterday, and I noticed my device manager is showing my card as the Geforce 4 Go 420 32 meg version. Our laptop's have the 440 64 meg version however. I installed the driver successfully, but i've noticed video quality in movies is TERRIBLE now! 

I found another website with instructions on our cards.

> 
7) If you own a GeForce4 420/440 Go or a GeForce4 MX 440 you should follow these steps:
Code:

```
sudo nano /etc/modprobe.d/options
```


Add this option at the end of the file:
Code:

```
options nvidia NVreg_SoftEDIDs=0 NVreg_Mobile=1
```


CTRL+O to save CTRL+X to exit

Edit your xorg.conf:
Code:

```
sudo nano /etc/X11/xorg.conf
```


Get to the "Section Screen" and add the following options
Code:

```
Option "ExactModeTimingsDVI" "TRUE" 
Option "ModeValidation" "DFP-0: NoEdidDFPMaxSizeCheck, NoVesaModes"
```


If you added the options that section should (approximately) look like the example below:
Code:

```

Section "Screen"
Identifier "Screen[0]" 
Device "Device[0]" 
Monitor "Monitor[0]" 
DefaultDepth 24 
Option "ExactModeTimingsDVI" "TRUE" 
Option "ModeValidation" "DFP-0: NoEdidDFPMaxSizeCheck, NoVesaModes"
SubSection "Display" 
     Depth 16 
     Modes "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
  EndSubSection 
SubSection "Display" 
     Depth 24 
     Modes "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" 
  EndSubSection 
EndSection

```

If those options do not work then you may replace them with the following:
Code:

```
Option "ExactModeTimingsDVI" 
Option "UseEdidDpi" "FALSE" 
Option "ModeValidation" "NoEdidDFPMaxSizeCheck, NoVesaModes"
```


If that did not work for your card you can try setting the following option instead of the one you put before in your /etc/modprobe.d/options:
Code:

```
options nvidia NVreg_SoftEDIDs=0 NVreg_Mobile=4
```


I will give this a shot and see how it goes. Not sure if it will make a difference at all but currently videos are unwatchable. Very blocky and pixelated.

---

