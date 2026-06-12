---
title: "Getting Flash and nVidia drivers working"
date: 2009-10-05
forum: x86 64-bit Users
---

### Post by bohunk on 2009-10-05
Hello everybody.  I have recently installed Ubuntu so that I can use OpenFOAM and other applications.  However I am having troubles installing the Adobe Flash player as well as nVidia drivers.  I have tried every method that I have found (including the ones on this forum) and can not get any of them to work.  I am likely missing something simple for both of my problems.  Could anybody give a newb like me some help?

---

### Post by FunkyRes on 2009-10-05
Use the 64 bit plugin.
Download it from Adobe:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

At bottom of page:

libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz

it should download to your desktop.

Open a terminal

```

cd Desktop
tar -zxf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so /usr/lib64/mozilla/plugins/

```

restart your browsers and you should have flash.

---

### Post by FunkyRes on 2009-10-05
Note - if you installed the 32-bit plugin through synaptic or apt, remove it, you don't want it.

---

### Post by HappyFeet on 2009-10-05
Remove any flash you may have installed.

For flash, get the 64bit flash file. [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz)

Then right click and **extract here**. You will now be left with **libflashplayer.so** file. Copy it. Open your home folder and do Ctrl-H. You will now see your hidden directories. Go to the **.mozilla** folder and open it. Create a new folder called **plugins**. Open it. Then paste the libflashplayer.so file there. Close out and restart firefox.

For the Nvidia drivers, go to system>administration>hardware drivers and install the driver from there.

---

### Post by bohunk on 2009-10-05
Ah thankyou FunkyRes!  Now I just need to sort out the sound and nVIDIA drivers.  Happyfeet every time that I do that, it doesn't download anything and prompts me to restart.  When I do and check hardware drivers, they still say that they are not in use.  Also when I download the driver fom nVIDIA and try to run it I get an error.

---

### Post by lidex on 2009-10-06
For nvidia drivers go here:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates")

Click on the link "Technical details about this PPA" for how to add this PPA to your repositories. Once that is done open synaptic and click "Reload". Now in the search box type in "nvidia". In the results make sure to apply any updates. Also make sure these packages are installed - if not right-click and select "mark for installation':

```
jockey-common
jockey-gtk
nvidia-180-kernel-source
nvidia-180-libvdpau
nvidia-180-modaliases
nvidia-common
nvidia-glx-180
nvidia-settings
xserver-xorg-video-nv
```

Click "Apply". When done reboot and go to Hardware Drivers to enable.

---

### Post by lidex on 2009-10-06
I got Flash working on my install by removing any and all flash related plugins/packages and installing "flashplugin-installer". Check out this thread: [http://ubuntuforums.org/showthread.php?t=1271385&page=2]("http://ubuntuforums.org/showthread.php?t=1271385&page=2")

---

### Post by bohunk on 2009-10-06
lidex I tried that method, however I am not sure if it supported Hardy Heron or not, I tried it either way but it didn't get past the reload.

---

### Post by lidex on 2009-10-06
What display driver is currently in use in your system? What is your video card?

---

### Post by RedRat on 2009-10-06
> **bohunk said:**
> lidex I tried that method, however I am not sure if it supported Hardy Heron or not, I tried it either way but it didn't get past the reload.

I don't know if the following applies to you or not. However, I managed to trash my Firefox and after screwing around with it for about a half day, I just plain removed it completely via synaptic. Then I went in and re-installed from Synaptic. 

When I went to Youtube, no video and the usual you must have java script, blah blah.....

As i have remarked here before, apparently some think the Adobe Flash player in the repos is screwed up. So I went in and completely uninstalled Adobe Flashplayer via synaptic. then reinstalled it from the Adobe site. STill no joy in Firefox. Then I remembered something from another blog here. I went to the Adobe Flash deb file and opened is and extracted the file libflashplayer.so

I also had kept my old /.mozilla folder by renaming it .mozillax and compared the two folders. The old folder, .mozillax, had a subdirectory called plugins. In the new installation, no such folder existed. I had made at least 4 attempts to install Adobe Flash Player and none created that plugin folder. I don't know whether this is a bug in Hardy installation or what. Hmm. So I created the plugins folder under .mozilla and copied the libflashplayer.so file into it. Wow. Flash now worked.

At least it worked for me.

---

### Post by lidex on 2009-10-06
bohunk: how about an update? Seems you had more than one issue - is anything fixed?

---

### Post by bohunk on 2009-10-06
Well Adobe Flash is now working, I still need to sort out not hearing sounds through the browser though.  I am still having problems with my vid card drivers.  I am using an nVidia 8800GTX at the moment.  Mostly I want to get this working so that I can get my dual monitors set up properly.

Also perhaps some more system information is required.  It is Ubuntu 8.04, and even though I created a new partition for it, I believe it installed along side of my XP media center as the partition I created is still shown as empty.  Every time I try to run a download I get an i386 error.

---

### Post by lidex on 2009-10-06
What driver is enabled and what problems are you having?
Are you able to boot XP? What is the exact error message and what exactly are you doing when it appears?
Are you using x64 Firefox as browser? Pulseaudio enabled?

---

### Post by bohunk on 2009-10-07
I am not sure what driver I am using at the moment, but I was trying to upgrade drivers so that I may eventually get the dual monitors working correctly (rather than one a copy of the other).  XP boots fine, and when I tried logging into Ubuntu a minute ago, it showed that the OS loaded, but then showed an "initinput" line and prompted me for an entrance (which I have no idea what to enter).  I haven't checked which Firefox I had been using, and I haven't enabled pulseaudio.

---

### Post by lidex on 2009-10-07
Have you installed Enlightenment (E17)? If you can get to a command prompt run this command:
```
sudo dpkg-reconfigure gdm
```
You can run recovery mode from grub. At some point it should ask you if you want to drop to command line.

---

### Post by bohunk on 2009-10-14
Ok sorry about the late response been busy lately.  Turns out the reason it wouldn't launch correctly is because XP wasn't properly shut down.  When I relaunched XP and shut it down Ubuntu launched perfectly.

---

### Post by bohunk on 2009-10-14
This is the error I get when I try to launch the nVIDIA driver install:

> Could not open the file /home/john/Documents/nVI&#8230;x86_64-185.18.36-pkg2.run.
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

---

### Post by lidex on 2009-10-14
You're trying to open a binary file in gedit. Follow these instructions:
[https://help.ubuntu.com/community/InstallingRunPackage]("https://help.ubuntu.com/community/InstallingRunPackage")

You should think about upgrading to a more recent ubuntu - jockey makes things much easier.

---

### Post by tuxxy on 2009-10-14
bohunk listen if the restricted hardware manager is palying up for you then you can install the driver for that nvidia card using envy-ng.  This will identify the correct driver and download it for you.  Its available in the repos so search for envyng-gtk using Synaptic or type in terminal

```
sudo apt-get install envyng-gtk 
```To install that file you have there it has to be done in the terminal and manually configured, it would be a lot easier to envy bud but if you want to have a go using the binary then you would do this 

1.  Open a terminal. Applications > Accessories > Terminal.
2. Navigate to the directory of the .run file. For example if its on the desktop then type in 
```
cd Desktop
```3. Then make the file executable by typing
```
chmod +x x86_64-185.18.36-pkg2.run
```4.  Now run the installation by adding a ./ to the start of the filename
```
./x86_64-185.18.36-pkg2.run
```You will need to edit the packagename in those examples though as I only included some of the name you would need the full one

---

### Post by bohunk on 2009-10-15
thanks tuxxy, the second method said it required me to run the program from root, however the first one got the drivers working properly.  I now need to solve my in browser sounds not working and how to setup dual monitors, if anybody would like to help yet some more :-k

---

### Post by lidex on 2009-10-15
Tutorial with video here:
[http://vasir.net/blog/ubuntu/set-up-dual-monitors-with-ubuntu-804/]("http://vasir.net/blog/ubuntu/set-up-dual-monitors-with-ubuntu-804/")

---

