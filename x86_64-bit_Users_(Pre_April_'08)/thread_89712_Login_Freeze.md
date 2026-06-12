---
title: "Login Freeze"
date: 2005-11-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by magic07 on 2005-11-13
Imac G5 17"
Installation Successful, Yaboot Successful, boot successful.
When I reach the login screen for user name i can't type in anything and the system locks up.  Read other posts and it seems to be a graphics driver issue, others suggest time and date issues but I don't think so.  Any suggestions?

---

### Post by nevc64 on 2005-11-17
My machine - iMac 500 Mhz Slot Loading
Video Adapter reported as. ATI Technologies Inc Rage 128 Pro Ultra TR

I have been using Warty & Hoary with my iMac with no problems, However I 
had problems upgrading from Hoary to Breezy. Install seemed to be fine but X was exceptionally slow and unusable. Over a week of anguish and trawling this forum and the net....

(refer [http://www.ubuntuforums.org/showpost.php?p=495998&postcount=8](http://www.ubuntuforums.org/showpost.php?p=495998&postcount=8) )

[COLOR="Blue"]However tonight I stumbled across this thread[/COLOR]
[http://www.ubuntuforums.org/showthread.php?p=13390&mode=linear&highlight=freeze#post13390](http://www.ubuntuforums.org/showthread.php?p=13390&mode=linear&highlight=freeze#post13390)
[http://www.ubuntuforums.org/showpost.php?p=14711&postcount=6](http://www.ubuntuforums.org/showpost.php?p=14711&postcount=6) (thanks Muteaid)
[http://www.ubuntuforums.org/showpost.php?p=45651&postcount=37](http://www.ubuntuforums.org/showpost.php?p=45651&postcount=37) (thanks chascon)

and tried some things I found there.

There was some suggestions about adding some things to /etc/modules and making sure the driver in xorg.conf was "r128" not "ati".

So I...

Added these items to /etc/modules
--start snip
#Added 17/11/2005 NMC to try and fix screen hangs
r128
agpgart
uninorth_agp
--end snip
 
and changed the Driver entry in xorg.conf

Extract from xorg.conf
--start snip
Section "Device"
	Identifier	"ATI Technologies, Inc. Rage 128 Pro Ultra (TR)"
#	Driver		"ati"
        Driver          "r128"
	Option		"UseFBDev"		"true"
EndSection
--end snip

This worked!!! I'm using Breezy now. :) This wasn't very scientific. It could be that one of the changes on there own would have provided the solution. I'll go back and try commenting out bits tomorrow to see if both steps were needed.

Woohoo!!

Neville

---

### Post by fraterf93 on 2005-11-17
I am having the same problem with my iMac G3 600mhz.  PLEASE Nev, give DETAILED instructions on how you did this.  Did you open a shell from the cd, etc.  That seems to be the only way I would be able to do it, as I can't get past the login window.  And please, no shortcuts, or short-hand or anything.  I am a linux newbie, and have no idea what I'm doing.  I have a little bit of experience with a terminal environment, but my only Unix eXperience is with Mac OS X, and that very limited.  Emptying the .Trash of stubborn files with sudo rm -r command, or listing files in a folder with ls, or ls -al.  Things like that.  So what I need Is instructions on how to fix this "ati" video problem, starting from "Press the power button and turn on your computer" ;) 

Thanks a million!

---

### Post by nevc64 on 2005-11-18
fraterf93,

I don't think you will need all the details you have requested. Let's try this:

1. Poweron and let the iMac complete booting until it displays the Log-in Screen.

2. Press cntl-alt-F1 i.e Press cntl-alt together and then press F1. This will take you to a terminal screen. If you machine was behaving as badly as mine then you will need to be patient. Select the keys, wait 10 seconds and if nothing appears to be happening try again.

3. You should be presented with a prompt like **MachineName login:**

4. Login with your user name and password. i.e Enter User name and then press enter. Then enter password and press enter. You should get something like **username@machineName:~$**

5. Now you are going to use a Text editor called Nano to view and edit the files I talked about in my post.

Type "nano /etc/modules" at the terminal prompt and inspect the file to see if the modules I mentioned are listed. Use arrows and page up, page down to navigate within nano. Commands are listed at the bottom of the "nano" screen eg cntl-X to Exit, cntl-O to save changes. If the modules aren't listed then you will need to add them. cntl-X to exit file and return to prompt.

7. To add the modules to the file you will need to edit the file. To do this you need to prefix the previous command with sudo i.e "sudo nana /etc/modules" and press enter. You will be prompted for your password. Enter password and press Enter. nano will open. Add the modules I listed in my post to the file and save with cntl-O and then exit with cntl-X.

8. Use the same procedure to view and then edit the file /etc/X11/xorg.conf and add the r128 driver to the "Device" Section of the file. Also comment out the "ati" driver by adding the # character at the start of that line. Refer to my previous post for how it should look.

9. Check each of the edited files again to make sure that you saved the changes properly eg "nano /etc/modules"

10 If the changes have been saved then reboot. Type "sudo shutdown -r now" press enter and your iMac will start shutting down and will reboot for you. You probably don't actually need to reboot but I am not sure of the commands to use to restart the appropriate programs!!

11. Cross your fingers and toes and think kind thoughts. With a bit of luck the system will bring up the log-in screen and you will be able to log in normally.

Neville

---

### Post by fraterf93 on 2005-11-18
I'm posting from Kubuntu right now!  One thing.  When I went to show off my dual boot Mac OS X Tiger/Kubuntu Breezy Badger iMac G3 to my roomie, it wouldn't boot into Kubuntu.  Nor would it boot from CD.  It just kept booting into Mac OS X, and I had been switching back and forth between Kubuntu and Tiger all day!  He was like "I thought you had Linux on yer Mac." :neutral:  Turns out there were some bad sectors on the Linux volume.  I deleted the partitions and reinstalled, and so far all is well!  I guess its time to replace the hard drive!  Thanks again tho!

---

### Post by Jazzinghen on 2005-11-21
My god, thank you for your help.
I was able to configure an ubuntubox for a friend.

---

### Post by Torrance on 2005-12-04
I have the same issue with the exact same machine as the original poster on this thread.

I have just installed 5.10 on my 17inch iMac G5. Installation was successful etc. etc., but on loading up Ubuntu I get to the login screen and it seems as though there is no ability to make any sort of input, either by keyboard or mouse. I can't type in my login name nor can I restart/shutdown - it feels like I might as well not have the keyboard/mouse plugged in at all.

These 17inch iMac G5's have 64mb GeForce FX 5200 so I don't think the previous fix with the videocard would work. This must be common for this model, so surely people must know a workaround???

Any help would be much appreciated! :)

ADDITION: Attempts to enter the console also seem to fail.

---

### Post by Torrance on 2005-12-04
One final thing I have noticed:

In the moments before the login screen comes up, when the screen has gone completely black and all I can see is the circular icon of the mouse, then I can move the mouse around. But as soon as the login screen appears the mouse freezes and the keyboard does nothing.

Help!

---

### Post by Torrance on 2005-12-04
So in those few moments before the login screen loads and mouse is still responsive, I can load up the console, but it is similarly unresponsive. However, it does start slowly listing some timeout errors every 30 seconds or so, such as follows:

Ubuntu 5.10 "Breezy badger" ubuntu tty1

ubuntu login: [   108.648803] ata1: command 0x25 timeout, stat 0x50 host_stat 0x4
[   138.648794] ata1: command 0x35 timeout, stat 0x50 host_stat 0x4
[   139.576955] mpic_enable_irq timeout
[   168.648798] ata1: command 0x25 timeout, stat 0x50 host_stat 0x4
[   198.648789] ata1: command 0x25 timeout, stat 0x50 host_stat 0x4
[   199.715012] mpic_enable_irq timeout
[   228.648800] ata1: command 0x25 timeout, stat 0x50 host_stat 0x4
[   258.648792] ata1: command 0x25 timeout, stat 0x50 host_stat 0x4
[   288.648799] ata1: command 0x25 timeout, stat 0x50 host_stat 0x4
[   318.648792] ata1: command 0x25 timeout, stat 0x50 host_stat 0x4
[   348.648799] ata1: command 0x25 timeout, stat 0x50 host_stat 0x4
                        :                                 :
                        :                                 :
[   1008.648797] ata1: command 0x25 timeout, stat 0x50 host_stat 0x4


And it just kept on going... I'm assuming this is what is also happening behind the scenes with the frozen login screen. What's happening?

---

### Post by Torrance on 2005-12-04
(sorry! last post till someone else replies!!)

I just found two other threads with people having the same problem on the same hardware:

[http://ubuntuforums.org/showthread.php?t=96564](http://ubuntuforums.org/showthread.php?t=96564)
[http://ubuntuforums.org/showthread.php?t=93243](http://ubuntuforums.org/showthread.php?t=93243)

---

### Post by Achille on 2006-01-08
I don't have a iMac G5 myself. But I found this hint:

[http://www.suseforums.net/index.php?showtopic=19034](http://www.suseforums.net/index.php?showtopic=19034)

---

### Post by limey on 2006-01-12
To nevc64:

use 

sudo /etc/X11/gdm restart

---

### Post by ctt1wbw on 2006-01-12
We appreciate all the help, but the problem with the G5 iMac that I had, and so has everyone else, is that we can't type anything, or hit any key combo to get a console.  I tried about 50 times yesterday and gave up.  I have OS X back on my iMac now so I can use the bloody thing.

I managed to get a :boot prompt somehow, but I can't do anything there.  I tried using a rescue-powerpc64 boot from the installation cd, but I managed to get to an ash shell and typed cd /target to get to my drive and then cd /usr/bin but there was not esd file for me to rename...

I'm lost.  I just hope Dapper can load on this thing.

---

### Post by Achille on 2006-01-12
There is another possibility for you: when you reinstall Ubuntu, choose the option of installation: server. Then Ubuntu is installed without any graphical interface and you get automatically a console when you boot.

Keep the CD in your computer and type:
sudo apt-get install ubuntu-desktop

then you can type:
sudo mv /usr/bin/esd /usr/bin/bakesd

and
reboot

I hope that it will work!

Just another remark: partition your disk so that you don't have to reinstall Mac OS X! Use one partition for OSX and the remaining space for Ubuntu. Choose then to manually edit the partition table when you (re)install Ubuntu.

---

### Post by ctt1wbw on 2006-01-13
Yeah, I might partition this thing.  How does grub do on an os x drive?  I've heard there are problems there, too.  I'll give it a go here soon.  Thanks for the info!

---

### Post by Achille on 2006-01-13
The architecture powerpc doesn't use grub but yaboot.

You have to install first MacOSX. Use Disk Utility with the installer of OSX for partitionning in 2: one partition in hfs+ for OSX and one partition in free space for Ubuntu.

After the installation of OSX, proceed at the installation of Ubuntu. Choose to use the free space for Ubuntu. Ubuntu uses this free space for creating at least three partitions: one bootstrap (1M hfs) for yaboot (the bootloader), one (ext3) for / and one for the swap. You can customize the default.

You can find some help for partitionning here:
[http://www.terrasoftsolutions.com/support/installation/ydl3.0_guide-single.pdf](http://www.terrasoftsolutions.com/support/installation/ydl3.0_guide-single.pdf)

---

### Post by Torrance on 2006-03-10
The problem of the iMac G5 freezing when GDM loads up seems to be related to sound issues. If the sound can be disabled before any program attempts to play sound, then the system doesn't hang.

**My question is, then, is there any way I can disable the sound on an Ubuntu system before it loads up into GDM and presents me with the frozen login screen?** Can I halt the loading process somehow, and work from a base system and disable all sound on the system? (I'm a relative newbie too so please by clear with explanations... cheers!).

---

### Post by ubuser_ on 2006-03-11
The alsa pmac sound driver is causing the complete freezes.

---

### Post by Torrance on 2006-03-11
Sweet, so is there any way one can stop the ALSA sound driver loading up on startup?

I've tried pressing Ctrl-C on startup and stopping services loading up, but the console I'm presented with has read-only privileges so I can't make any changes to the files that way.

---

### Post by Torrance on 2006-03-11
Oh, so I can edit my system with the live-CD in rescue mode.

**So I just need to know how to disable either ALSA from starting up, or to mute ESD, (or something like that...) using a CLI.** Is there a config file I can easily edit or delete??

---

### Post by Torrance on 2006-03-12
Renaming /usr/bin/esd as bakesd didn't work. :cry:

---

### Post by Torrance on 2006-03-12
Finally, SUCCESS!! I'm quite proud I worked this out considering I'm such a Linux newbie!! :-D It seems obvious now that the problems on iMac G5's are to do with sound - to stop them crashing on startup you have to disable the ESD sound server as well as a login sound.

First things first: to access a console, you need to force-quit GDM (Gnome Desktop Manager, ie. the login screen) before it freezes. So, in those few moments before the login screen is fully loaded and you can still move the mouse, you need to press Control-Alt-Backspace. This will kill it, but it'll try coming back - 6 times in fact. Once you've killed it for the 6th time, it'll warn you it's taking a break for 2 minutes before restarting GDM again.

Now you need to move quickly...

1) Login
2) Go to /etc/X11/gdm. (enter "cd /etc/X11/gdm")
3) You need to edit the gdm.conf file, so enter "sudo nano -w gdm.conf".
4) Go down 5 or 6 pages (using control-v), or searchfor the line "SoundOnLogin=True". Make this false. There's another line much closer to the start of the file that mentions sound, but says it won't use a daemon - you may have to comment this in (ie. add a "#" to the start of the line) if the next step doesnt work.
5) Hard reboot. The login screen should now not be frozen.

Now you've stopped the sound at the login, you need to stop the ESD sound server from loading up when you actually login.

1) From the login screen, enter a console once again (you won't have to force quit this time, simply press control-alt-F1).
2) Enter the command: "gconftool-2 --type bool --set /desktop/gnome/sound/enable_esd false"
3) Now go back to the login screen (control-alt-F7) and log in. All should be sweet now. Yay!

This isn't a complete fix, of course. Whatever is still causing the problm with the sound driver is still there, all we've done is stopped a few key programs trying to access the sound drive (still, I'm writing this in Ubuntu). If some program attempts to access the sound driver while you're logged in, the whole system may well freeze again. I hope somebody works out what is actually causing this!!

---

### Post by ggunter on 2007-03-25
The above fixes did not help for me- I found this info:
If video controller is ATI Rage 128 Pro Ultra, Ubuntu boot might be really slow, mouse and keyboard unresponsive. Drop to CLI terminal with CTL+ALT+F1 (you may have to wait for it, due to slow operation) and remove glx module from xorg configuration, either with dpkg-reconfigure xserver-xorg or by editting /etc/X11/xorg.conf directly. (need explicit step-by-step here for restarting the desktop)

from-http://wiki.freegeek.org/index.php/TonysMacJournal_Jan07

and along with lowering the graphics depth from 24 to 16 during the reconfig- my imac g3 500 dv and 600 dv are both running super fast.  I'm curently now upgrading one machine- the 600 to edubuntu from xubuntu with the hope that it will remain fast now that glx is disabled.  I did change the xorg.conf file to include the r128 and something else (I forget from other posts as well) on one machine but not on the other and it seems that the reconfig fixed everything without needing to alter the xorg.conf file.

---

