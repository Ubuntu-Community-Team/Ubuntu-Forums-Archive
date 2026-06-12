---
title: "How I got the latest NVIDIA 100.14.11 drivers installed"
date: 2007-07-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by six on 2007-07-31
```

How I got the latest NVIDIA 100.14.11 drivers installed
=======================================================

   Tip: press <TAB> to complete long file or directory names
        where possible, ie. NVIDIA<TAB>

1) Download the latest driver from www.nvidia.com, and save
   it to your home directory, eg.

     ~/NVIDIA-Linux-x86_64-100.14.11-pkg2.run

2) Group-select these instructions (in the top code box,
   not the whole HTML page) by left-hold-clicking in the
   upper-left corner, then dragging down to the bottom.
   When all of the text is highlighted in reverse, press
   right-click and select 'copy'.

   Open gedit (Applications->Text Editor), then right-click
   and select 'paste'. Save the contents to a file called
   'how' in your home directory, eg.

     ~/how

   You will then be able to view these instructions as often
   as you'd like after you've quit out of Gnome, simply by
   entering this command at the console prompt:

     less ~/how

   (Use <PgUp>, <PgDn>, <Up-Arrow> and <Down-Arrow> to move
   around in the file).

3) Exit out of Gnome by pressing <CTRL-ALT-F6>, logging in
   at the text prompt, and typing:

     sudo /etc/init.d/gdm stop

   (A confirmation message that Gnome has stopped should
   appear).

4) Backup your current xorg.conf file with:

     sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.justin

5) Enter the following commands:

     sudo apt-get remove nvidia* linux-restricted-modules*
     sudo apt-get install linux-headers-$(uname -r) \
       build-essential pkg-config xorg-dev
     sudo sh ~/NVIDIA-Linux-x86_64-100.14.11-pkg2.run

   Follow the prompts, selecting Y or ACCEPT to everything.
   (Don't worry if a couple of warnings appear, such as
   'Unable to check for libGL.so.1')

6) At this point, if you tried restarting, you would get
   'failed to load module wfb, need libwfb' error messages
   in /etc/X11/Xorg.0.log

   To fix this, extract the files from the Nvidia driver
   package, like so:

     sh ~/NVIDIA-Linux-x86_64-100.14.11-pkg2.run -x

   Copy the missing wfb module over with:

     cd ~/NVIDIA-Linux-x86_64-100.14.11-pkg2/usr/X11R6/lib/modules
     sudo cp libnvidia-wfb.so.100.14.11 /usr/lib/xorg/modules

   Then change directories and create a symbolic link with:

     cd /usr/lib/xorg/modules
     sudo ln -s libnvidia-wfb.so.100.14.11 libwfb.so

7) At this point, if you tried restarting, you would get the
   errors 'lrm-video not found' and 'failed to load the
   NVIDIA kernel module!'

   To fix this, change directories and edit the lrm-video
   file (after changing update permissions) with:

     cd /etc/modprobe.d
     sudo chmod go=rw lrm-video
     sudo vim lrm-video

   Comment out the 'nvidia' line by pressing the following
   keys in this order:

   <DOWN> <DOWN> i # <ESC><ESC> : x <ENTER>

   To examine the edited file, type:

     cat lrm-video

   It should now look like this:

   Code:

     install fglrx /sbin/lrm-video fglrx $CMDLINE_OPTS
     #install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS
     install nvidia_legacy /sbin/lrm-video nvidia_legacy
       $CMDLINE_OPTS
     install nvidia_new /sbin/lrm-video nvidia_new $CMDLINE_OPTS

   Change the permissions back to read-only with:

     sudo chmod go=r lrm-video

8) Now restart Gnome with:

     sudo /etc/init.d/gdm start

   (You should hopefully see an Nvidia logo flash on screen).

   And login at the graphical prompt.

9) You may see a warning about [not] using 'restricted drivers'
   pop up at this point. Click to get rid of it. (Hopefully it
   shouldn't appear again).

   Open a terminal prompt and type:

     sudo nvidia-settings

   Click on the 'X Server Display Configuration' option,
   then set your resolution and colour depth as appropriate.
   (If you set it to 'auto', it should switch to your max.
   resolution automatically).

   Don't forget to click on the 'Save to X Configuration File'
   button to make sure your settings are stored for next time.

10) If you know what you're doing, you might want to tidy
    up your /etc/X11/xorg.conf file at this point, removing
    the old & now unwanted monitor, device & screen sections.
    From the terminal prompt, type:

      sudo gedit /etc/X11/xorg.conf

    As a rough guide, keep the sections with the identifiers
    'Monitor0', 'Videocard0' and 'Screen0'.

    (Or you could leave it alone; it still seems to work OK).
```


For example, the lower part of my xorg.conf looked like this:

```
[I]Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "NEC 20WGX2"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8800 GTS]"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G80 [GeForce 8800 GTS]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0; 800x600 +0+0; 640x480 +0+0"
EndSection[/I]
```


So I tidied it up to look like this instead:


```
[I]Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "NEC"
    ModelName      "20WGX2"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0; 800x600 +0+0; 640x480 +0+0"
EndSection[/I]
```

---

### Post by Shinobi326 on 2007-07-31
I'm still a newb here but that seems like a lot of gyrations to get the drivers working.  Is this because of a difference between the 64 & 32-bit OS's?  The reason I ask is because I have the exact same cards and I don't remember having to do all of this stuff to make it work for me (on 32-bit Ubuntu 7.04 Feisty).

I do admit that the 8800GTS cards appear to still not conform to any normal means to get installed (restricted drivers, ENVY, etc.).  I've always had to compile mine manually from the drivers off the NVIDIA website.  This was the biggest pain for me to understand being a new Ubuntu user a few months back.

I hope this post works out for those searching for a step-by-step and have tried the other regular means first.

---

### Post by six on 2007-07-31
The gyrations are necessary to cover bugs/problems in Ubuntu, and to remove any previous attempts at installing restricted drivers through the repositories.

Ideally, it would just be a matter of invoking **sudo sh NVIDIA_Linux_x86_64-100.14.11-pkg2.run**, but steps 4 and 5 are necessary to get around Ubuntu.

I installed 32-bit Ubuntu only temporarily yesterday, until I found out how to boot the 64-bit live CD, so I've never attempted to install the 32-bit Nvidia driver. I can't say if you'd have to do the same or not.

But at least you won't have to compile manually with the 100.14.11 driver; it does all that for you.

---

### Post by jirah on 2007-08-01
This is a great how-to; clear, concise and written in newb-friendly terms. Just follow the steps and you are home free. I do have to point out to the author. that in steps 3 and 4, you have mistakenly placed "_" instead of "-" in the name of the driver and consequently the name of the extracted folder. This could lead to some confusion and frustration if the reader does not notice the error and simply copies verbatim. Otherwise, this how-to has saved my butt twice now with a Gutsy_x64 install and I greatly appreciate the time and effort that went into the writing.

Jirah

---

### Post by TimsterC on 2007-08-02
This is pure "GENIUS".

Thanks for the guide. It worked on my T61 perfectly.

---

### Post by six on 2007-08-02
> **jirah said:**
> I do have to point out to the author. that in steps 3 and 4, you have mistakenly placed "_" instead of "-" in the name of the driver and consequently the name of the extracted folder.

Oops! Apologies - duly corrected.

And thanks for the kind comments, guys!

---

### Post by erico on 2007-08-02
Nice bit of info. I guess I am just too used to using Windoze . I used the Envy script to install the driver for my 8600GT card. It was a painless install...no gyrations required.

---

### Post by six on 2007-08-04
[Edited - this part now included in cleaned-up original instructions]

---

### Post by p1977p on 2007-08-09
i have installed the Nvidia driver for my GeForce 6100 card. During shutdown, the black screen (with messages on it) appears blurry with abnormal color at the borders and duplicate characters (like seeing two overlapping screens placed asynchronously). can this be corrected?

---

### Post by iAndrew on 2007-08-09
Hmm. Maybe this might work. On boot up, do you see a grey background with a nvidia logo you see?

---

### Post by six on 2007-08-16
Improved version you can copy to a text file to look at outside of Gnome as you're going along, or print out and keep.

Now includes commands to quit out of Gnome (and restart) without rebooting.

The instructions might appear long, but they are detailed. And they work! (I've just followed them again for a fresh install of Feisty.)

They should only take around 5m or so.

---

### Post by nicolasdiogo on 2007-08-17
Hi,

just to say THANKS for the info.
just bought a new Geforce 8600GTS and had to install Nvidia driver from their website as Ubuntu default driver does not support this card yet.
And you instruction were so right saving a lot of hasle.  i had spent quite some time trying to understand the missing modules..
i finally have dual DVI monitors working with Linux.

Cheers!

TAG: NVIDIA UBUNTU DRIVER XORG MODULE HOWTO

---

### Post by s_spiff on 2007-08-18
Hey, I'm yet to try. I'm on a fresh Feisty install, and when I tried the command to apt-get istall build-essentials, I got an error saying there was no candidate for build-essentials or something like that. Are some repo's to be added or included? Right now, I'm back inside gnome, will update the repos and try again.

---

### Post by tbeehler on 2007-08-18
This worked perfectly on my 8800GTS.  Thanks!

---

### Post by s_spiff on 2007-08-18
dude, absolutely fabulous! Worked for my 6100 onboard nvidia graphic card on a Gigabyte motherboard! Thanks for the great how to. Incase I do learn how to script, I shall make one based on this. Or if you do know how to make one, would suggest you make a script for this!

---

### Post by s_spiff on 2007-08-19
Looks like I spoke too soon! My comp just froze [ I hadn't restarted after installing the driver and other default updates and was downloading firefox32 ] and then I had to restart manually. And when booting up, I ended up getting a blue screen that said that xorg or something wasn't able to find a usable screen or something like that. unfortunately the error was pretty long, hence didn't get down to write it and all. I'll reinstall everything and try envy this time :(. Anyways, thanks for the how to, was great while it lasted :P

---

### Post by nicolasdiogo on 2007-08-20
> **s_spiff said:**
> Looks like I spoke too soon!

hi,

why don't you try reinstalling the driver from a command window.

click CTRL + ALT F2 (F3, F4..) login and follow the howto again.

by trying to fix it you can only learn, post any questions here.

good luck..

---

### Post by nowashburn on 2007-08-23
does anyone know how to get this driver working without uninstalling restricted modules? i need restricted modules for other things,... like my wireless card!

---

### Post by el_jefe_99 on 2007-08-24
Exellent guide!  I had some problems updating the driver.  Cratered my Beryl\Emerald (GLX module died and failed to install correctly).  Here are the steps taken from my history and where your guide played a role.

Use ENVY uninstall pulse.py nvidia uninstall 
gedit /var/log/Xorg.0.log
apt-get remove emerald-themes --purge
apt-get remove beryl --purge
apt-get remove nvidia-glx --purge
rm /etc/init.d/nvidia-glx
rm /etc/init.d/nvidia-kernel 
rm /etc/init.d/nvidia-kernel 
rm /lib/linux-restricted-modules/.nvidia_new_installed 
sudo dpkg-divert --rename --remove /usr/lib/xorg/modules/extensions/libglx.so
sudo aptitude purge envy
sudo dpkg-divert --rename --remove /usr/X11R6/lib/libGL.so.1.

<FOLLOW YOUR GUIDE HERE>  ...I have a x32 Ubuntu build.  So instead of NVIDIA-Linux-x86-100.14.11-pkg2.run ..... I used NVIDIA-Linux-x86-100.14.11-pkg1.run

sudo nvidia-settings
sudo apt-get update
sudo apt-get install beryl
sudo apt-get install emerald-themes
beryl-manager

Hope this helps and thanks for the guide.  Great work! :KS

---

### Post by Ruazinn on 2007-08-25
Great how-to!  This is why I love Ubuntu.  Thought I'd add my notes.  First of all, my system is an AMD Athlon 64 X2 Dual Core with NVidia GeForce 7500LE video.  Got it for a song last weekend on craigslist and have been geekin' out with feisty AMD64 all week.

Before running your procedure, I already had Nvidia drivers installed from Automatix2, but they weren't the latest, so I decided to upgrade.  Everything went smoothly following your exact procedure, except for one minor deviation:  

Step 6.  sudo ln -s libnvidia-wfb.so.100.14.11 libwfb.so

This failed, because libwfb.so already existed as a symlink to ibnvidia-wfb.so.1, which itself was a symlink to libnvidia-wfb.so.100.14.11.  Guess I could've made libwfb.so directly link to libnvidia-wfb.so.100.14.11, but I just left it the way it was.  Maybe the install program put it that way for a reason.

The other thing I noticed is that your procedure launches graphical programs using sudo.  It's preferable to use "gksudo" for GUIs that need admin privileges.  Doing it with sudo can change the ownership of the app's config file to root, which messes things up when you run the same program without sudo, because the program can't update the file.  I think I had the problem when I ran "sudo gedit" once.

But, big deal.   Great job!

---

### Post by BobCFC on 2007-08-26
> **s_spiff said:**
> Looks like I spoke too soon! My comp just froze [ I hadn't restarted after installing the driver and other default updates and was downloading firefox32 ] and then I had to restart manually. And when booting up, I ended up getting a blue screen that said that xorg or something wasn't able to find a usable screen or something like that. unfortunately the error was pretty long, hence didn't get down to write it and all. I'll reinstall everything and try envy this time :(. Anyways, thanks for the how to, was great while it lasted :P



When it fails on reboot and says cannot launch X  error API mismatch... it means that you did not uninstall the ubuntu restricted drivers 

try    sudo apt-get remove nvidia*

---

### Post by Ruazinn on 2007-08-26
Looks like I spoke to soon as well.  Been having problems with the computer locking up since I went through the procedure yesterday.  With the older Nvidia drivers I installed last week through Automatix2, the only time it locked up was when I tried to change the resolution with desktop effects enabled.  Now it tends to lock up after a while if one of the fancier screensavers is active.  So I set the screen saver to blank.  How boring...

When it locks up, I can't really do much of anything 'cept get medieval on the computer's *** and yank the plug.  Ctrl-Alt-Del doesn't work, and the button on the front of this computer just tries to make it go into standby.  

Anyone remember how to set up ctrl-alt-del for rebooting?  I don't see any entry for "Reboot" in System->Preferences->Keyboard Shortcuts.  I think I'll set up a ssh server, so I can at least try to login from another computer and restart.  Yanking the cord just seems too..., well, winblozy.

---

### Post by Ruazinn on 2007-08-26
Well, I got my old Xubuntu system logged into the new one via ssh.  So next time it freezes, I'll try restarting gdm from the xubuntu xterm.

---

### Post by Ruazinn on 2007-08-27
Well, restarting gdm from the other computer didn't work on the next freeze.  The ssh session was non-responsive.  I guess the system really was stone dead.

I tried adding the boot options "noapic nolapic", and that seemed to help.  I couldn't trigger a crash using any of the screen savers.  But then while resizing the sidebar in Firefox, I got another freeze.  This time the mouse pointer would still move and ctrl-alt-backspace tried to do its thing.  But X didn't restart successfully, and I had to ctrl-alt-delete.  But at least I didn't have to yank the power.

One thing I didn't do from the original procedure was tidy up my xorg.conf file.  So I did that and also rebooted with "noapic nolapic".  We'll see what happens...

Hope gutsy gets rid of these issues...

BTW, I ran a multihreaded Java app I wrote that does a lot of number crunching using all the available processors and processor cores.   Since those boot options have something to do with how work is allocated to the processors, I wanted to see the effect.  The program got faster -- it went from 13 seconds to 12.  On my dual processor intel xeon at work, which looks like 4 processors to Java, the best time I can get is 30 seconds.  And those processors are 3.3GHz while this AMD Athlon is 2.4 GHz.  I guess a 64 bit OS really does makes a difference!

---

### Post by Marat Galiev on 2007-08-27
I have worked my 8600GT card with this way:
```

Only 27 steps:)
1)Install packages xserver-xorg-dev,pkg-config,libc6-dev.
You an find them at packages.ubuntu.com.
2)Press ctrl+alt+F2.
3)sudo nano /etc/init.d gdm stop
4)cd /there/your/driver/location
5)sudo sh NVIDIA-100.14...-xxx.run --ui=none
(without GUI menu).
To the question with nvidia-xconfig answer "Yes".
6)sudo nano /etc/default/linux-restricted-modules-common
Edit line
DISABLED_MODULES="nv nvidia_new"
7)sudo cp /lib/modules/2.6.20-15-generic/kernel/drivers/video/nvidia.ko /lib/modules/2.6.20-15-generic/volatile/
8)sudo modprobe nvidia
9)/sbin/ldconfig
10)/sbin/depmod -aq
11)reboot
12)step 7
13)cd /lib/modules/2.6.20-15-generic/volatile/
13)sudo insmod ./nvidia,ko
14)sudo modprobe nvidia
15)step 9
16)step 10
17)sudo /etc/init.d/gdm start
18)reboot
19)cd /lib/modules/2.6.20-15-generic/kernel/drivers/video/
20)sudo cp nvidia.ko nvidia_new.ko
21)sudo insmod ./nvidia.ko
22)step 9
23)step 10
24)ctrl+alt+F7
25)sudo nvidia-xconfig
26)reboot

```

OK!So,please check you glxinfo command.
You can see what:
[B]OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 8600 GT/PCI/SSE2
OpenGL version string: 2.1.1 NVIDIA 100.14.11[/B]
Thank's.

---

### Post by Ubuntiac on 2007-08-29
> **nowashburn said:**
> does anyone know how to get this driver working without uninstalling restricted modules? i need restricted modules for other things,... like my wireless card!

Same here...

Right now I seem to have a choice between beautiful 3d acceleration for games, blender etc, or...
Having an internet connection (as my card uses Madwifi / Atheros)

Now if there's a way to get both, I'll be a very, very happy camper!

---

### Post by DruNierer on 2007-08-30
I have installed the latest nvidia driver 100.14.11 using the method outlined by six and compiz fusion works great!  But any OpenGL screensaver is choppy and CPU usages goes to 100%.  Neverball is just a black screen, nothing is displayed.  I have experienced the same problems with the 9639 driver and restricted modules.  I have a GeForce FX 5700 Ultra.  I can't be the only one experiencing these problems.  I have searched forums for hours...please help!!!

---

### Post by BobCFC on 2007-09-01
I had 100% cpu use once when my IDE hard drives were not using DMA... do you use IDE drives and is it slow to copy big files?

---

### Post by DruNierer on 2007-09-01
Yes, I am using IDE drives.  How do I ensure they are using DMA?

---

### Post by mlitty on 2007-09-02
Thank you so much.  I had just accepted the kernel upgrade by the Ubuntu update manager when my nvidia kernel failed.  I'd tried several other HowTo's, but yours was the only one that worked.

Thank you.

---

### Post by Kxpress on 2007-09-02
> **mlitty said:**
> Thank you so much.  I had just accepted the kernel upgrade by the Ubuntu update manager when my nvidia kernel failed.  I'd tried several other HowTo's, but yours was the only one that worked.

Thank you.


Which one ? the 27 steps HOW TO or else ?

:confused:

---

### Post by eleim7 on 2007-09-03
Followed your instructions but the GUI failed to load, said that it failed to load NVIDIA kernel module and that the x-server is disabled until it is fixed (typing from memory here on my Windows installation, excuse the mistakes).  Any suggestions?  

Everything seemed to work fine until I got to step 8.  I had a little trouble with step 5 cause I didn't know what \ meant, but went back in, got it to install, but it still has not started the GUI.  

After typing: "sudo /etc/init.d/gdm start"
I think it says "Starting Gnome...... [OK]"
and then goes back to prompt.  

I have a Nvidia GeForce 6800 GS, AMD Athlon 64 3700+ 2.21 GHz, 2 GB RAM... if that helps anything.

At this point I wouldn't mind just reverting back to the working gnome session and use the old Nvidia restricted-modules driver, but I don't know how to do that either.

---

### Post by BobCFC on 2007-09-03
> **DruNierer said:**
> Yes, I am using IDE drives.  How do I ensure they are using DMA?


You can do a disk speed test from the console with Applications->Accessories->Terminal and typing:

```
sudo hdparm -iTt  /dev/hda
```

Where  /dev/hda  is you hard disk...
On mine it says among other things:

> 
.....
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 ***udma6** 
 ......
 Timing cached reads:   7120 MB in  2.00 seconds = 3562.99 MB/sec
 Timing buffered disk reads:  214 MB in  3.02 seconds =  **70.93** MB/sec


The important bits are in bold.. the star is next to UDMA6  instead of PIO mode  and speed is 70.93  when DMA was not enabled for me the speed was  1.6mb/s  lol!


To enable DMA try  

```
sudo hdparm -d 1 /dev/hda
```

Where  /dev/hda  is you hard disk... you can search the forums for other solutions about modules of it doesn't work such as here:  [http://www.ubuntuforums.org/showthread.php?p=93238#post93238](http://www.ubuntuforums.org/showthread.php?p=93238#post93238)

---

### Post by BobCFC on 2007-09-03
> **eleim7 said:**
>  I had a little trouble with step 5 cause I didn't know what \ meant



This is a critical step because you have to remove the old ubuntu restricted drivers to use the drivers from the NVIDIA website.  (the  \  symbol just means that before and after it should be joined together in one long command on not separate lines.. if you cut and paste the computer will join them)

Typing this should remove the restricted drivers:

```
sudo apt-get remove nvidia*
```


Then you can reinstall the ones downloaded from the website:

```

sudo sh NVIDIA.xxx.run
```

You can use tab to autocomplete here.. type the first few letters NVI<tab>...  note it is cAse Sensitive.

Also the website drivers need a certain amount of maintenance, if you uprage to a new version of linux kernel or xserver they need to be reinstalled but this is not very common, such as when gutsy gibbon replaces feisty fawn.

NOTE:  for my part I have never had to do steps 6 or 7  on two different PCs..  although I have had a harmless missing lib.so warning which didn't matter

---

### Post by eleim7 on 2007-09-03
would it matter if the driver is not in the home directory? like if it was on the desktop, wouldn't you just change the path of the file from:

~/NVIDIA-Linux....

to:

~/Desktop/NVIDIA-Linux...



That's the only mistake that I am completely sure about.

---

### Post by gtdaqua on 2007-09-05
Thanks to the author of the guide! I now have the 100.14.11 drivers working on my Kubuntu Feisty 64! 

The link to how I got it working could be found here:
[http://ubuntuforums.org/showthread.php?t=541880&page=2]("http://ubuntuforums.org/showthread.php?t=541880&page=2")

---

### Post by BobCFC on 2007-09-05
> **eleim7 said:**
> would it matter if the driver is not in the home directory? like if it was on the desktop, wouldn't you just change the path of the file from:

~/NVIDIA-Linux....

to:

~/Desktop/NVIDIA-Linux...



That's the only mistake that I am completely sure about.



No you can install the file from any directory.  It runs a wizard for you where you just choose OK,OK,OK.

---

### Post by gregili on 2007-09-06
I am newb at the forum ..Worked just fine for me.I have an Acer Aspire 1522wlmi.Nvidia GeForce Fx Go5700.Thanks a lot !

---

### Post by timzak on 2007-09-07
For the topic starter:

> sudo apt-get install linux-headers-$(uname -r)

Don't you have to put your actual kernel version here, in place of uname -r?  If so, you should make that clear for newbies.  I seem to remember copy/pasting some driver installation instructions awhile back and borking my install because I didn't do this.  Then I ended up overwriting my -generic kernel with the -i386 and couldn't understand why both of my Core2Duo cores weren't showing up.

---

### Post by puttingau on 2007-09-09
Another newb, this worked well for me, on my onboard GeForce 6150SE nForce 430
whereas other howtos didn't.

I don't understand why the kernel update caused this problem in the first place, though?

---

### Post by glee on 2007-09-09
Great information. Thanks! (If only I had discovered it sooner...)

---

### Post by twicebjorn on 2007-09-11
> **eleim7 said:**
> Followed your instructions but the GUI failed to load, said that it failed to load NVIDIA kernel module and that the x-server is disabled until it is fixed (typing from memory here on my Windows installation, excuse the mistakes).  Any suggestions?  

Everything seemed to work fine until I got to step 8.  I had a little trouble with step 5 cause I didn't know what \ meant, but went back in, got it to install, but it still has not started the GUI.  

After typing: "sudo /etc/init.d/gdm start"
I think it says "Starting Gnome...... [OK]"
and then goes back to prompt.  

I have a Nvidia GeForce 6800 GS, AMD Athlon 64 3700+ 2.21 GHz, 2 GB RAM... if that helps anything.

At this point I wouldn't mind just reverting back to the working gnome session and use the old Nvidia restricted-modules driver, but I don't know how to do that either.

I was having the same problem as eleim. The log I was given said something about a fatal problem with the NVIDIA kernel, and being able to find no viable monitor to use. Switching to any of my xorg.conf backups didn't make a difference, which pretty much left me right out of ideas...

So I ran the installer again.

I don't know what it did, but it did it, alright! Seems to be working fine, touch wood.



[Edit:]

I think I may have spoken way to soon. All that did was get me a working GUI. There's still no sign of the drivers working.

I'm way too tired for this. Trying again tomorrow.

---

### Post by twicebjorn on 2007-09-12
Just an update...

I got this working through sheer dumb luck. I got a working GUI by messing about with the installer and backed up xorg.conf files (just played with it until it worked), then got the NVIDIA drivers working by telling nvidia-settings to overwrite my xorg.conf file again.

For some reason it worked. Oh, the joys of exploratory noobness!

Thanks for the guide, by the way! Coming from someone who's still pretty new to this whole deal, it was a great little romp through the system!

---

### Post by whb on 2007-09-12
All I did, after all kinds of aggravation, was to go to the NVidia README, followed the instructions for Ubuntu and there it was working perfectly on Gutsy AMD64 Tribe 6 (the non released one) and my 8800GTS,

Hunter

---

### Post by Tech^CF on 2007-09-23
After passing vga=791 to the kernel at boot (black screen problem on my 8800gts) and getting through to KDE/GNOME, and followed the guide. I now got accelerated graphics on my desktop.

But, it seems that my Atheros wireless card was running restricted drivers, which got uninstalled during one of the first steps of your guide. Any way to have both restricted wireless drivers *and* new NVIDIA drivers?

---

### Post by eccheng on 2008-03-31
Someone please sticky this post to be on first page.  Really one of the best instructions i've ever seen.  Got my 8600gt working flawlessly.  This man is a genius.  Thank you!!!!

:KS:lolflag:

---

