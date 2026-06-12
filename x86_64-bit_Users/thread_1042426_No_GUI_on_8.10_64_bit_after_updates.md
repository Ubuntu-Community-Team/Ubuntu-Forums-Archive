---
title: "No GUI on 8.10 64 bit after updates"
date: 2009-01-17
forum: x86 64-bit Users
---

### Post by jimtanis on 2009-01-17
Hi;

I have a EVGA 600isli Motherboard, Intel core 2 dual, dual NVIDIA 8800 GTX (not in SLI) hooked to 2 monitors, and a HDTV .  

I am dual booting one partition on VISTA, the second I am trying to get going is 8.10 65 bit UBUNTU.  

When I first install I have the GUI and all seems fine.  Then I installed the NVIDIA restricted driver, and did the updates.  (all in one step the last time, but have tried (in the past so I am not sure) to install updates without installing the restricted driver first)  

When I reboot, I do not have the GUI, only the text based interface.

I tried downloading and installing NVIDIA's driver 64-180.22.  The install seemed to go correctly, but after rebooting the GUI did not come back.  

Any ideas on where to look?  I assume there is a log that might tell me more.

Thanks!  Jim Tanis, Hays, KS
:confused:

---

### Post by bfinan0 on 2009-01-17
> **jimtanis said:**
> Hi;

I have a EVGA 600isli Motherboard, Intel core 2 dual, dual NVIDIA 8800 GTX (not in SLI) hooked to 2 monitors, and a HDTV .  

I am dual booting one partition on VISTA, the second I am trying to get going is 8.10 65 bit UBUNTU.  

When I first install I have the GUI and all seems fine.  Then I installed the NVIDIA restricted driver, and did the updates.  (all in one step the last time, but have tried (in the past so I am not sure) to install updates without installing the restricted driver first)  

When I reboot, I do not have the GUI, only the text based interface.

I tried downloading and installing NVIDIA's driver 64-180.22.  The install seemed to go correctly, but after rebooting the GUI did not come back.  

Any ideas on where to look?  I assume there is a log that might tell me more.

Thanks!  Jim Tanis, Hays, KS
:confused:

If you have EnvyNG, install and uninstall 177 first using it, then install 180.22  Everything should work right after you do that.

---

### Post by jimtanis on 2009-01-17
I need to know the proper syntax to uninstall and install from envyng  .  Every thing I do gives me some text that appears to be an error of some type.  There are some numbers that include 177, but since I am in the VISTA partition right now, I can not access it to get to the error.

Thanks!  Jim

---

### Post by YuriSEAL on 2009-01-18
I've been having the same issue, it looks like. I've got the Xorg.0.log file. Unfortunately, I erased the contents of the drive trying to give up on 8.10 and install 8.04, so I'm unable to provide other documents. (There were a few problems with the latter, likely due to my trying to rush an install and doing things I knew were unwise. I did have an issue-free 8.04 install on the same computer with the same hardware, apart from a newly installed hard drive, though.)

As soon as I installed any NVidia driver (unfortunately, I didn't test with envy before I gave up) it would immediately cause the same error. envy refuses to run in text-only mode at this point, giving an error message about a list requiring integer values.

Things I tried:
[LIST]
[*]Reinstalling Ubuntu. (Twice.)
[*]Installing using the restricted drivers manager the first time, nvidia-glx the next times.
[*]Attempted uninstalling the nvidia-glx driver and reinstalling.
[*]Attempted uninstalling the nvidia-glx driver and installing a different version. (More specifically, uninstalling nvidia-glx-180, installing nvidia-glx-177, then after that didn't work, trying uninstalling nvidia-glx-177 and reinstalling nvidia-glx-180.)
[*]Attempted sudo nvidia-xconf
[*]Attempted sudo dpkg-reconfigure xconf
[*]Attempted deleting xconf and allowing it to load the failsafe
[*]Attempted trying to delete problematic xconf entries, which didn't work. I don't know a lot about xconf, so I wasn't willing to try more. (I have another computer and no important files on the Ubuntu drive, trashing it is not an issue.)
[*]Attempted to use envy to install nvidia drivers. (It aborts with an error when I attempt to start it, although it does list the 177 drivers as a candidate for installation.)[/LIST]

This is really quite the downer after having had an amazingly positive experience with 8.04 a few months ago.


Just an extra couple tidbits of information:
1) The actual LiveCD seemed to hang while it was shutting down after the installs. Not sure of why. It did the same thing when I shut it down without installing Ubuntu.
2) I'm running SLi.
3) With the initial installations, I had gnome load without issues, played around on the desktop for hours, restarted multiple times, etc - everything but the 3D acceleration seemed to work.

Hopefully there's something diagnostically relevant there.

---

### Post by jimtanis on 2009-01-18
Sounds like you have went a lot further than I have.  

What I was going to try next was to install a second hard drive, wipe out the first install on a partition of my existing drive.  Install to the new drive, and before I run any updates of whatever, install envyng, and then use the GUI version of envyng to remove the nvidia drivers, and install the new ones.  

Who knows if that will work....  This is my first attempt at any 64 bit operating system.  And I am a newbie to linux also. I have run Ubuntu for a year or so, but when it comes to command line stuff I am really limited in what I know how to do.

Will post further updates.

Jim
:confused:

---

### Post by mckeja on 2009-01-20
I have run into this issue on my system and spent almost an entire day tracking down what the problem was.  The 'fix' appears to be obnoxiously simple.  It seems that on machines with more than one video card, X doesn't know which one is which.  All that is needed, then, is to add a BusID line to any 'Device' sections in your /etc/X11/xorg.conf file.  The BusID line will be related directly to the information you find about your video card from "lspci."

For example: 
```

    wolf@northstar:~$ lspci | grep GeForce
    01:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT 
    04:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT

```

Then, in my /etc/X11/xorg.conf file, I have the following device sections:
```

    Section "Device"
        Identifier     "Device0"
        Driver         "nvidia"
        VendorName     "NVIDIA Corporation"
        BoardName      "GeForce 8500 GT"
        BusID          "PCI:1:0:0"
    EndSection
    Section "Device"
        Identifier     "Device1"
        Driver         "nvidia"
        VendorName     "NVIDIA Corporation"
        BoardName      "GeForce 8500 GT"
        BusID          "PCI:4:0:0"
    EndSection

```
Initially, I only had one 'Device' section. Rather than manually add everything for two devices, I simply set the first BusID line in the only 'Device' section in the file.  Then, I restarted 'gdm' and logged in with only one screen displaying.  Once there, I ran 'sudo nvidia-settings' and used the "X Server Display Configuration" to set up both displays. After clicking "Save to X Configuration File" I restarted X and viola, had both displays up and running beautifully.


That said, there are some other issues I've noticed. My system is a fresh install of Intrepid using the Desktop amd64 CD image with all the current updates. Everything on the main head (Device0 aka PCI:1:0:0) works splendidly. On the other display, however, clicking on icon applications (Firefox, Evolution Mail, Help) cause an instant crash of the gnome-panel without loading said application. Opening the same programs through the Application menu system cause no problems.  The second issues I've discovered is that if you're spending all your time on the second display for whatever reason, the power save and screensaver options kick in as if you were idle. The 'fix' is to occasionally bump the mouse into the first display every so often. Rather annoying, if you ask me.

---

### Post by jimtanis on 2009-01-20
That sounds interesting.  I may explore that .  Thanks!

By the way, On my fresh install I have tried to install ENVYNG-QT and it shows up in applications/system tools , but when I run it, it asks for a password, I type it in, and then nothing happens.  

Ideas?

Thanks  Jim

---

### Post by YuriSEAL on 2009-01-21
The advice posted in the previous post absolutely worked. I had a really generic message, so I typed in device entries formatted like the one in the message.

Probably worth noting is that I did this after attempting to install the 180 drivers from the command line using apt-get install nvidia-glx-180 and I ended up having to revert to the 177 drivers before startx worked. (It claimed that there was a mismatch between the driver I was trying to use and the kernel module, I think.)

Thanks a lot for helping me resolve this!

---

### Post by mckeja on 2009-01-21
I'm glad that worked for you. I'm seeing a lot of people with the same issue. If I could explain things a little more simply, I'd write up a HowTO or something.  

Oh, also, I fixed my lockup problem. It seems that after the initial update, you've got two kernels installed. 2.6.27-7 and 2.6.27-9. When you install the NVidia drivers, either manually or with the System/Administration/Hardware Drivers tool, the kernel module appears to compile with the 27-7 kernel. My "fix" was using synaptic to uninstall the 27-7 kernel, then used the tool to uninstall the hardware drivers, rebooted, and finally used the tool to re-install the Nvidia driver. 

Now the only issue to fix is the stupid World of Warcraft crash when it tries to access memory over 4g.

---

### Post by norwoods on 2009-01-23
thanks bfinan0 for the clue "If you have EnvyNG, install and uninstall 177 first using it, then install 180.22 Everything should work right after you do that."

---

### Post by wiresquire on 2009-01-24
Just a quick note ...

There have been a lot of problems reported with the nVidia 180.22 driver series, eg around screen corruptions/refreshing/tearing, resume from suspend, various Powermizer issues etc. Check out the [nvnews linux forum]("http://www.nvnews.net/vbulletin/forumdisplay.php?s&forumid=14") for more info. I had enough problems with my machine to move back to 177.82.

hth & good luck
ws

---

