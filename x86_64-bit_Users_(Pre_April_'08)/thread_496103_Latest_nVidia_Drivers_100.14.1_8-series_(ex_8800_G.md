---
title: "Latest nVidia Drivers 100.14.1: 8-series (ex: 8800 GTS) and 64-bit Ubuntu 7.04 Feisty"
date: 2007-07-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Bondrake on 2007-07-08
Hello, so for the last few hours I have been trying to get the latest AMD64/EM64T nVidia graphics drivers to work properly in 64-bit Feisty.  I just finally got EVERYTHING working exactly right, so I'm going to post some instructions here AND a pre-compiled driver package so you don't have to recompile the kernel module.  I included 8-series in the title because I had trouble looking for information for my 8800 video card on here, but these instructions should work for any nVidia card.

My system is as follows:
Processor: Intel Core 2 Duo E6320
Motherboard: Gigabyte GA-965P-DS3 (Intel 965P Chipset)
Video Card: nVidia 8800GTS 320MB
Monitors: Two 20.1" wide-screen 1680x1050 LCDs

With these instructions I am assuming you have a fresh install of 64-bit Ubuntu 7.04 (Feisty).  These instructions MAY NOT work If you have attempted to use the nvidia-glx-new package or similar already, even if you've uninstalled them (although feel free to try and let me know).

You will want to run all the auto-update installs before you follow my instructions; I believe one of the updates will break the driver setup, requiring you to go into recovery mode and reinstall the drivers.  (for those with further interest: I'm not sure which auto-update breaks this, but it causes the loaded nvidia kernel module to switch to 1.0-9631, when it should be 100.14.11)
Update - I believe the packages causing this are: 
```
linux-restricted-modules-common
linux-restricted-modules-generic
linux-restricted-moudles-2.6.20-16-generic
```
These packages include the non-free kernel modules included with Ubuntu (which also happens to include the nvidia module).  I recommend you exercise caution in updating these modules in the future while using the proprietary nVidia drivers below. Alternatively, you may remove them if you don't require any of the other drivers supported in these packages (personally, I need with wi-fi drivers).

_HOWTO: INSTRUCTIONS_

Step 1: Download my re-package of the nVidia 100.14.11 drivers.  This package includes a pre-compiled nvidia kernel module for the 2.6.20-16-generic kernel.  You may download from here (right click and save as):     ```
[http://www.entvibes.com/ubuntuforums/NVIDIA-Linux-x86_64-100.14.11-pkg2-2.6.20-16-generic.run]("http://www.entvibes.com/ubuntuforums/NVIDIA-Linux-x86_64-100.14.11-pkg2-2.6.20-16-generic.run")
```

Step 2: Make a backup copy of your current xorg.conf file in case you mess something up in these future steps: 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_preinstall
```

Step 3: Logout of your current Gnome session (click the red power button in the upper-right corner and select Logout).  Once that's complete, press Ctrl-Alt-F1 to go to a console.  From the console, login again (press Enter if you aren't immediately prompted to login).

Step 4: Stop the Gnome Desktop Manager with the following command: 
```
sudo invoke-rc.d gdm stop
```

Step 5: Enter the following command to see which kernel version you are using:
```
uname -r
```
If the output is not "2.6.20-16-generic" then you're using a different kernel than the default 64-bit Ubuntu 7.04 kernel and my pre-compiled package won't work for you (don't despair though, it will just require more work.  check out this thread on nvnews: [http://www.nvnews.net/vbulletin/showthread.php?t=94072]("http://www.nvnews.net/vbulletin/showthread.php?t=94072")).  If the output IS "2.6.20-16-generic" then all is good and you can continue to the next step.

Step 6: You'll need to cd to the directory you downloaded my driver file to (probably your desktop). If it is, this will work:
```
cd ~/Desktop
```

Step 7: Run the pre-compiled driver file and follow the prompts:
```
sudo sh ./NVIDIA-Linux-x86_64-100.14.11-pkg2-2.6.20-16-generic.run
```
When asked if you want to use nvidia-xconfig, select yes.  That way you don't have to manually edit your xorg.conf file with the new driver. (Note: During install I received a warning about the following library being unable to be verified: "/usr/lib32/libGL.so.100.14.11" It stated that it was assumed working though. I received this message after saying yes to the request to install the 32-bit compatibility libraries. This is on a fresh install of Ubuntu 7.04 x64, no updates or additional packages installed. All appears to be working, but I thought I would still mention this for future reference.)

Step 8: Restart the Gnome Desktop Manager and try it out:
```
sudo invoke-rc.d gdm start
```

Step 9: If everything works and you're able to get into your desktop... sweet! Let me know!  Also, make another backup copy of your xorg.conf now that the drivers are installed and all is working with the new file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_postinstall
```
Continue to Step 10 if you need some tips on configuration.

Step 10: The drivers should have installed a tool called nvidia-settings. This is a graphical interface that allows you to configure your xorg.conf file visually (yay!) among other things. Open a terminal and enter:
```
sudo nvidia-settings
```
Since I have two monitors I went to the "X Server Display Configuration" page and enabled the second monitor as a seperate X screen, then set the resolution to auto for both (which properly detects the native 1680x1050... sweetness), then enabled xinerama (which causes both monitors to behave as individual monitors and prevents a lot of funkiness with programs launching half on both screens and whatnot).  After configuring everything as desired on that page I clicked the "Save to X Configuration File" button, which comes up with a window that should have "etc/X11/xorg.conf" in the text box. I unchecked the "Merge with existing file." tickbox; this will create an entirely new xorg.conf file with the information you've provided.  If you had mouse or keyboard customizations in your xorg.conf file, reference against the backups I had you create to restore those.  Once you've recreated the xorg.conf file and saved it you can test the changes by pressing Ctrl+Alt+Backspace to restart GDM (Gnome Desktop Manager).  If it fails, you may need to restart your system in recovery mode and enter the following to restore your backup xorg.conf file:
```
cp /etc/X11/xorg.conf_postinstall /etc/X11/xorg.conf
```
Then just restart and you should be able to get back into Gnome

That's it!  Update to let me know if I'm missing anything or let me know that this works for you!

---

### Post by Sockerdrickan on 2007-07-09
Was the 8800 able run with the nv driver.

---

### Post by Didjit on 2007-07-09
Not trying to rain on your parade, did you try Envy?

 [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Didjit

---

### Post by Cappy on 2007-07-09
yup you HAVE to remove all linux-restricted-modules:
```
sudo apt-get --purge remove linux-restricted-modules*
```

Also, you need additional packages not listed in your post:
[http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386/](http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386/)
second part of the post

oh wait you re-packaged it? o_O

---

### Post by Bondrake on 2007-07-09
> **Tux0r said:**
> Was the 8800 able run with the nv driver.

The one's installed in Ubuntu? Yeah, with minimal features and no acceleration or easy multi-monitor support. :-P

> **Cappy said:**
> yup you HAVE to remove all linux-restricted-modules:
```
sudo apt-get --purge remove linux-restricted-modules*
```

Also, you need additional packages not listed in your post:
[http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386/](http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386/)
second part of the post

oh wait you re-packaged it? o_O

I deed, I deed.... no build dependencies... simple install... kinda the point here. :)


> **Didjit said:**
> Not trying to rain on your parade, did you try Envy?

 [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Didjit

I did not... it appears to only support up to the 9755 drivers.  Does it work with the new drivers?  If not, when I have more time I might talk with him about helping update it.

---

### Post by Bondrake on 2007-07-09
> **Didjit said:**
> Not trying to rain on your parade, did you try Envy?

 [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Didjit
 
Nevermind, looks like he implemented the new drivers in one of the most recent updates: [http://albertomilone.com/wordpress/?p=98]("http://albertomilone.com/wordpress/?p=98")

FWIW, there's a bug report in his bugtracker of someone with a similar setup to me not being able to use Envy, so maybe my little write-up will still help a few people. :)

---

### Post by Sockerdrickan on 2007-07-09
My installer helper works great :P



GET DRIVER

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev

sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common linux-restricted-modules*

sudo rm /etc/init.d/nvidia-*

CTRL+ALT+F6+LOG ON TO YOUR UBUNTU ACCOUNT

sudo /etc/init.d/gdm stop

sudo sh NV (PRESS TAB TO GET THE REST)

GO THROUGH THE INSTALLATION

sudo /etc/init.d/gdm start

---

### Post by armin00as on 2007-07-10
Great guide, Bondrake! 
After 2 days of agony and pain (..oh, well..) you finally solved my Feisty 8800GTS driver nightmares...!  :-)

Even though I'm not running the 64-bit (but 32-bit) version as described in your post, I've made the necessary adjustments on the fly (e.g. driver downloaded from NVIDIA website -->version 100.14.11 nonetheless and file name adjustments) and got it running without any(!!!) problems, at the 1st attempt. WOW!!

For some reason, the otherwise excellent documentations of *Signore Milone's* :) :KS :KS  didn't quite work for me, and neither did the much-praised 'ENVY' :(  
(Since I'm a total newb to Linux/Feisty, I guess I didn't quite get it together correctly...) :lolflag:


Anyways,
[B]Much thanks to you, Bondrake 
- You Rock![/B] :guitar:

A  ; - )


P.S.: Off to installing Beryl now... or so I hope
P.S.2: Well, just realized I'm in the wrong (64-bit) forum.. - Sorry for that, guys. But there seemed to be nothing better available on the 8800GTS driver installation than this thread... so I had to post. - Thx!

---

### Post by armin00as on 2007-07-10
Guess my happiness & excitement didn't last long....

It all crashed & burned after rebooting again. I had to go through the reconfigure xserver-xorg process again b/c I overwrote my safe xorg.conf settings with the new ones... - BIG BUMMER!!!

I guess, Linux/Feisty only comes with a very steep learning curve, huh?


(Just to let you know the final outcome...)
G'Night...

---

### Post by armin00as on 2007-07-11
...my last post here, in the 64-bit section, I promise:  :)

Using tseliot's excellent 'ENVY' tool (v. 0.9.5) the NVIDIA settings for the 100.14.11 driver (manually selected) FINALLY DID STICK for me. No rebooting issues anymore, it seems... 

Just wanted to let other folks know who may also be looking for driver installation solutions for NVIDIA's 8800GTS (by keying "8800GTS" in the search box).


Thanks for your patience, everybody!
A : - )

P.S.:** tseliot, YOU DA MAN !!!**  :-)  :guitar:



My Rigg:
intel E6400 (permanent OC at 4.0 GHz) ++ Thermalright HR-01 HSF ++ eVGA 8800GTS (320MB) ++ 2GB TEAM Xtreme DDR2 (4-4-4-10) ++ Samsung SyncMaster 915N ++ Dual Boot Ubuntu 7.04 / Windoze XP

---

### Post by BobCFC on 2007-07-12
You have to run as root to get the settings to stick after reboot otherwise it can't write to xorg.conf such as

```

gksudo nvidia-settings
```

---

### Post by S3NTYN3L on 2007-07-12
Bondrake, how do I get this to work if I currently have NO video or sound?

The only way I can see anything Ubuntu is to run from the Live CD.

Even then, ONLY AFTER I press F-4, at the Start or Install Ubuntu screen, and change the mode from VGA to the highest res in the list...

I have no idea what I'm doing in Linux, so take it easy on me...

---

### Post by fleenort on 2007-07-12
[http://ubuntuforums.org/showthread.php?t=409345]("http://ubuntuforums.org/showthread.php?t=409345")

I know it seems totally unrelated, but if you scroll down a bit, you'll find this:

First boot up with the Live CD, then:

> Open a terminal (Applications -> Accessories -> Terminal) and type the following, step by step (pressing Enter after each line of course):

```
sudo mkdir /media/ubuntu

sudo mount /dev/sda3 /media/ubuntu

sudo mount -t proc none /media/ubuntu/proc

sudo mount -o bind /dev/ /media/ubuntu/dev

sudo chroot /media/ubuntu /bin/bash
```

You are now chroot'ed into your installed system.

Once you're there, you'll see that in the terminal, you are root.Note: You will still need to sudo or gksudo before commands, even though you are technically root. 

Install/tweak any drivers, etc. that need it and reboot without the cd. \\:D/

---

### Post by S3NTYN3L on 2007-07-12
OK, when you say boot up with the Live CD, do you mean:

Select the "Start or Install Ubuntu" option

or

The "Start Ubuntu in Safe Graphics Mode"?


I ask because BOTH options still run from the CD. (I can see the activity light on the CD drive blinking all the time)...


So, I do what you say...

Then what?

Just follow the tut of Bondrake's?

Will I still be in a GUI, because I don't know how I would follow the link he referenced from the command-line thing. ([http://www.entvibes.com/ubuntuforums...16-generic.run](http://www.entvibes.com/ubuntuforums...16-generic.run))

Also, Bondrake mentions "auto-updating" before I move one.
How is that dome?
I see nothing in the GUI about updating...


I'm so freakin' lost...:(

---

### Post by S3NTYN3L on 2007-07-12
OK fleenort, I'm now root@ubuntu:/#

Now what?

---

### Post by fleenort on 2007-07-12
> **S3NTYN3L said:**
> OK, when you say boot up with the Live CD, do you mean:

Select the "Start or Install Ubuntu" option

or

The "Start Ubuntu in Safe Graphics Mode"?


I ask because BOTH options still run from the CD. (I can see the activity light on the CD drive blinking all the time)...


Yes, either way... I'd just go with "Start or Install Ubuntu"

> **S3NTYN3L said:**
> 
So, I do what you say...

Then what?

Just follow the tut of Bondrake's?


Yep.

> **S3NTYN3L said:**
> 
Will I still be in a GUI, because I don't know how I would follow the link he referenced from the command-line thing. ([http://www.entvibes.com/ubuntuforums...16-generic.run](http://www.entvibes.com/ubuntuforums...16-generic.run))


The short answer is yes, you will be in a GUI. But if you follow my previous post, you'll have a terminal window open, running things at the command line. 
I don't see any reason why you couldn't open Firefox and download the file in question while in the boot cd. BUT - You will definately want to run the junk I showed you first, and save the file in /media/ubuntu somewhere!  If you just save it to the Live CD's desktop, I have no idea how you'd access it from the terminal window, and you'll have to know where it is to sucessfully get thru his tutorial.

> **S3NTYN3L said:**
> 
Also, Bondrake mentions "auto-updating" before I move one.
How is that dome?
I see nothing in the GUI about updating...


Well, if you boot up on the live cd and hit update, it will only update the live cd, which of course won't do anything but waste time.

Unless I'm mistaken, once you have ran the commands I gave you and are root on your installed system you can code (pressing enter after each of course)
```

sudo apt-get update

sudo apt-get upgrade

```

That should get you all updates installed on your system.

> **S3NTYN3L said:**
> 
I'm so freakin' lost...:(

You're not as lost as you think.[-X 

Welcome to the learning curve.:-D

---

### Post by S3NTYN3L on 2007-07-12
Thanks for that!:)

You're right, I'm not feeling AS lost as I was a few hours ago.


OK,

I put in your update and ugrade commands.
It's doing it's thing ATM...

Should I be worried about the proc, ubuntu and dev icons on the desktop?

They'll disappear when I'm done with the Live CD, right?

---

### Post by fleenort on 2007-07-12
Yeah, they'll disappear. Those are just links to your mount points. I wouldn't go messing round in them if I were you.

I've got a ton to do here, but I'll check back @ this post every once in a while today. If you need, you can pm me on here.

Have fun!

---

### Post by S3NTYN3L on 2007-07-12
Thank you for your patience fleenort! :)

I'll try not to screw this up too bad...



Damn, I hate being a newb again... ;)

---

### Post by Crinos512 on 2007-07-12
OK, as a Traitor to the M$ machine for less than a week I am proud to say I was able to compile and get my NVIDIA drivers working! ...YAY!

at least until I rebooted... I got no GUI and was told I had mismatched APIs. :(

---

### Post by fleenort on 2007-07-12
> **Crinos512 said:**
> OK, as a Traitor to the M$ machine for less than a week I am proud to say I was able to compile and get my NVIDIA drivers working! ...YAY!

at least until I rebooted... I got no GUI and was told I had mismatched APIs. :(


Maybe this will help? [http://ubuntuforums.org/showthread.php?t=409710](http://ubuntuforums.org/showthread.php?t=409710)

> **flipside17 said:**
> 
I edited my /etc/default/linux-restricted-modules-common file and disabled "nv". This ended up working with no problem.


---

### Post by S3NTYN3L on 2007-07-12
Umm...

I've got a small problem, I think.

My uname -r output is

2.6.20-15-generic

for me to follow this tut, it needs to be

2.6.20-16-generic


I read, the nvnews link posted by Bondrake, and did the following...

> - first you need to install the build-essentials which includes
development tools like make and gcc.
sudo apt-get install build-essential

- Then you should install the linux-headers package matching the installed Linux kernel.
sudo apt-get install linux-headers-generic #If you use generic kernel

you can look which kernel is in use with the following command

uname -r

it should print something like that
2.6.20-16-generic

My uname -r output is STILL -15- and NOT -16- (even after a reboot)!


What do I do now?

---

### Post by fleenort on 2007-07-12
If it were me - I'd just keep truckin'.

I think he was just giving an example and my best guess is that it will work just as well with 15...

---

### Post by Crinos512 on 2007-07-12
> I edited my /etc/default/linux-restricted-modules-common file and disabled "nv". This ended up working with no problem.

_Silly question:_ How do you disable nv when editing a file? 
(*_note: _this is my 2nd post, and I have < 3 days experience with Ubuntu.)

---

### Post by S3NTYN3L on 2007-07-12
> **fleenort said:**
> If it were me - I'd just keep truckin'.

I think he was just giving an example and my best guess is that it will work just as well with 15...

I guess I skipped ahead...

After i become root and download the re-package Bondrake made, I can't get past step three...

When I logout then try to log back in with:

sudo login

It says permission denied.

Is it trying to log me into the damn Live CD?

How am I do move forward now?

---

### Post by S3NTYN3L on 2007-07-12
Apparently, this cannot be done from the Live CD even while chrooted...

I skipped step 3 and did step 4 just fine.

Step 5 still says -15-

Step 6 doesn't work at all.

Step 7 tells me it can't open the file...



I'm about to :cry:...

---

### Post by fleenort on 2007-07-12
> **Crinos512 said:**
> _Silly question:_ How do you disable nv when editing a file? 
(*_note: _this is my 2nd post, and I have < 3 days experience with Ubuntu.)

```

sudo vim /etc/default/linux-restricted-modules-common

```

That will put you in VIM - the funnest of fun editors. 

Press Insert to type. Move your cursor with arrows to where it says "Disabled_modules"

Make it say this:
```

DISABLED_MODULES="nv"

```

Now, press ESC to exit editing mode
Press Shift-Q to get to command entry mode
Type the letters "wq" which will tell it to write the file and quit.

---

### Post by S3NTYN3L on 2007-07-12
HOLY CRAP!!!

I just re-started the GDM and I was logged out!

The GUI stayed up and I put my username and password in...


I'm now running via the install!!!

I'm going to give this tut another go!

Wish me luck...

---

### Post by fleenort on 2007-07-12
I dont' think it will let you logout of the live cd....

Skip logging out and try Ctrl-Alt-F1 to get to the command line.

... although, I would think that when you get to the command line, you no longer have your mounts....

so prolly have to code them all again...


Do you have no display at all when you boot from your hard drive, or do you get everything but a GUI??

---

### Post by Crinos512 on 2007-07-12
> **S3NTYN3L said:**
> I just re-started the GDM and I was logged out!
I'm assuming this is the "Gnome Desktop Manager", not the "Ghod Darned Machine" :)

> **S3NTYN3L said:**
> Wish me luck...
Good Luck!

---

### Post by S3NTYN3L on 2007-07-12
> **fleenort said:**
> I dont' think it will let you logout of the live cd....
Do you have no display at all when you boot from your hard drive, or do you get everything but a GUI??

I get absolutely nothing when booting from my drive...


Well, no joy.

After stopping the GDM again the screen reverted back to just after I made my second to last post...

I DO, however, have the Live CD currently sitting on top of my desk!

Is there some way I can get the file to run?

It still tells me "Can't run file" while I am root.

In my last post, I was s3ntyn3l@ubuntu and not root...

---

### Post by fleenort on 2007-07-12
I think you'll have to go thru all the trouble of chrooting back in once you're at the command line...

(Don't forget to make sure you're pointing it at the place where you saved it and that you technically have 2 separate file systems while chrooted)...

After that, if you're root and it won't let you run it, try:

```

sudo chmod 775 "the path and filename of the driver file thing"

```

Then try to run it again.....

In the meanwhile, it's time to go home, another day at work sucessfully wasted! :guitar:

Good luck.

---

### Post by S3NTYN3L on 2007-07-12
> 
root@ubuntu:/# sudo invoke-rc.d gdm start
 * Starting GNOME Display Manager...                                     [ OK ]

When I do the above, from the "Live CD" (remember, it's not in the drive anymore) I get logged out and taken to the GUI login screen where I can successfully login...

So, I log into the actual install...
I can run the file just fine except that it tells me I must stop the GDM to continue with the install.

So, I stop the GDM...

> 
root@ubuntu:/# sudo invoke-rc.d gdm stop * Stopping GNOME Display Manager...                                     [ OK ]

Once stopped, I'm taken DIRECTLY back to the Live CD version of the desktop.
Which comes back up on my monitor exactly as I left it...




This is what happens when trying to run the file (it doesn't matter which one. I know now where the one stored in my actual Ubuntu install is located)...

file from the "Live CD" desktop:
> 
root@ubuntu:/# sudo sh /home/ubuntu/Desktop/NVIDIA-Linux-x86_64-100.14.11-pkg2-2.6.20-16-generic.run
sh: Can't open /home/ubuntu/Desktop/NVIDIA-Linux-x86_64-100.14.11-pkg2-2.6.20-16-generic.run
root@ubuntu:/#


and if pointing to the file as stored on my actual hard drive:
> root@ubuntu:/# sudo sh /media/ubuntu/home/s3ntyn3l/Desktop/NVIDIA-Linux-x86_64-100.14.11-pkg2-2.6.20-16-generic.run
sh: Can't open /media/ubuntu/home/s3ntyn3l/Desktop/NVIDIA-Linux-x86_64-100.14.11-pkg2-2.6.20-16-generic.run



---

### Post by fleenort on 2007-07-13
That's where I would do the

```

sudo chmod 775 /media/ubuntu/home/s3ntyn3l/Desktop/NVIDIA-Linux-x86_64-100.14.11-pkg2-2.6.20-16-generic.run

```

Try running it after that... 

I did just sit down and try the whole Ctrl+Alt+F1 on the live cd... you don't have to log in as it says in the tutorial, but rather it gives you ubuntu@ubuntu at the prompt...

At that point you should be going thru the whole chrooting deal, then try running the chmod command above before trying to execute the NVIDIA-Linux-blahblahblah.run file.

---

### Post by mbrady on 2007-07-24
> **fleenort said:**
> Maybe this will help? [http://ubuntuforums.org/showthread.php?t=409710](http://ubuntuforums.org/showthread.php?t=409710)

Doesn't work for me. I am having the same problems as Crinos -- API mismatch after a reboot -- but adding "nv" to the disabled modules list doesn't fix it. Any other ideas? <:(

---

### Post by Big_Frostie on 2007-07-24
Ok, so I followed the instructions in you're first post, and everything worked peachy. Restarted it once, got the Desktop environment to work and restricted drivers enabled. Then, thinking everything was behind me, I dl'ed and installed a few other programs (Pidgin, Songbird...) and tried to get Beryl to work. Now its the next morning, I turn the computer on, annnnnd.... nothing. I get the message on the bottom of the screen that the kernel is enabled and then the monitor shuts off. I restart in recovery mode and try 'invoke-rc.d gmd start', upon which the screen flashes a few times before giving my a blue screen saying "Failed to start the X server." (Wasn't the reason I moved to Linux was to avoid the Blue screen?). 

The Detailed Error message:
Failed to initialize the NVIDIA kernel module! Please ensure that there is a supported NVIDIA GPU in this system, and that the NVIDIA device files have been created properly. Please consult the NVIDIA README for details. 
Screen(s) found, but none have a usable configuration.
Fatal server error: 
no screens found

(I find the last bit rather humorous, considering that I have to read it on something).

Followed by the message saying 'X is now disabled, restart gdm when X is configured correctly'

I've tried to look through the forums and follow some of the advice listed later in this thread and others, but none seems to work. Normally at this point, I'd start over from square one and try to figure out what I did wrong the first time, but I can't even get the Live cd to work now, the gui just dies on me. Help?

---

### Post by mbrady on 2007-07-24
> **Big_Frostie said:**
> The Detailed Error message:
Failed to initialize the NVIDIA kernel module! Please ensure that there is a supported NVIDIA GPU in this system, and that the NVIDIA device files have been created properly. Please consult the NVIDIA README for details. 
Screen(s) found, but none have a usable configuration.
Fatal server error: 
no screens found

There should be a more detailed reason for why it failed to start directly before this message in the log. It's probably going to say "API mismatch"...

---

### Post by Big_Frostie on 2007-07-24
Woops. It did.

Error: API mismatch: driver component 100.14.11, kernel doesn't match

---

### Post by sparks0548 on 2007-07-25
I tried the guide in the following link and worked awesome on a 64-bit machine.  Especially setting the default color depth to 24 versus 16.  That made a huge difference.

[http://ubuntuforums.org/showthread.php?t=458164](http://ubuntuforums.org/showthread.php?t=458164)

---

### Post by BobCFC on 2007-07-28
To all those having the API mismatch problem after reboot when downloading from the NVIDIA website... You may have tried the Ubuntu restricted drivers before and they must be removed FULLY before you install the ones from the nVidia web site.

This happened to me at first and now I'm running compiz-fusion across dual monitors!


UPDATE:
> ..... search for them in synaptic and remove everything nVidia related.....


OK this happened to me again when testing the new Gutsy Gibbon... It was even easier than I remembered to fix... simply **sudo apt-get remove nvidia*** from the command line when X crashed on boot... then crtl-atl-del to reboot and everything worked!

---

### Post by Maria_Firewire on 2007-08-09
THANKS SO MUCH Bondrake for the 'How To', it worked great!  And Thanks BobCFC for that API mismatch fix.

I love Ubuntu people.

-Maria-

---

### Post by TBZ on 2007-08-11
Okay, problem a nooby comment/question (since I am) but... This way wouldn't support GLX would it? How important is GLX? 

Heldal said in another thread:
> Heldal,
nvidia's driver version 1.0.9755 works just fine with 8800GTX/GTS using the original driver-pack from nvidia. I've used it with a 8800GTS since feisty was released using nvidia-glx-new with the missing bits added from nvidia's driver pack.

Ubuntu's problem is that the package maintainers have left out a x-server-module when they created the package. The missing module doesn't affect older GPUs.

The new 100.X driver is required for the most recent 8500, 8600 and mobile chips though. It also fixes a couple bugs for the 8800s but isn't required to make them work.

This is ridiculous. The problem was reported months ago and is still not fixed even though its as simple as a file + possibly a symlink missing in nvidia-glx-new. The current package is simply incomplete.

     So I am wandering, is this for only installing the card via that way? Or does actually support GLX that way? I figure it would be nice to have full support for the 8800GTS if possible... I too have had a hell of a time getting the driver to work. 

     It has been a nightmare, especially me being new to Linux... Last time I tried linux was about 5 years ago or so, redhat 4.0 or mandrake 5.0 , somewhere around there. The way Ubuntu is, I REALLY want to make the final conversion to linux for good this time around, but things like this make me wander if it's the right thing to do... even still, I am very determined and very open to learn and open to any help when I can recieve it.
     
     On a side note, I'm installing your setup now, *hope it works for me* =D

p.s. yay for first post

*UPDATE* works good so far, man thanks alot for posting this, true lifesave, after 2 days of trying, I can finally rest

---

### Post by masoodkamal on 2007-08-12
hi 

I used ur repackeged file but nothing is different from the file from nvidia website. it keep asking for the nvidia kernel file. i am confused wht is the problem :(
and i tried to stop gdm with the invoke command u mentioned but thr is no invoke command in ubuntu.

Plz help man in installing Nvidia driver. i have Geforce 7600 GT, and can we use sli in Ubuntu.

---

### Post by PresidentJFJ on 2007-08-17
> **BobCFC said:**
> To all those having the API mismatch problem after reboot when downloading from the NVIDIA website... You may have tried the Ubuntu restricted drivers before and they must be removed FULLY before you install the ones from the nVidia web site.

This happened to me at first and now I'm running compiz-fusion across dual monitors!


UPDATE:


OK this happened to me again when testing the new Gutsy Gibbon... It was even easier than I remembered to fix... simply **sudo apt-get remove nvidia*** from the command line when X crashed on boot... then crtl-atl-del to reboot and everything worked!

This didn't work for me. When I do "sudo apt-get remove nvidia" i get the message that there is no nvidia package to remove. To make this work do I need to get the glx package then remove it? Thanks.

---

### Post by colo505 on 2007-08-17
Has any of you tried the Cedega OpenGL test after installing the driver? It fails for me..

---

### Post by masoodkamal on 2007-08-18
hi bondi boy :)

man i can get ur repackaged file running . it keep asking for nividia kernel to download. why isnt it picked the one u pack in the file. :confused:

Help m8

---

