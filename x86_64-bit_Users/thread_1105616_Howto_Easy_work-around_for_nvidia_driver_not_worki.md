---
title: "Howto: Easy work-around for nvidia driver not working with 64-bit Ubuntu"
date: 2009-03-24
forum: x86 64-bit Users
---

### Post by le_jawa on 2009-03-24
I've had the same problem a lot of folks have had with Ubuntu 8.04 (and I believe other releases) and new nVidia cards:  The Ubuntu-built proprietary driver doesn't work (for me, it didn't even show up in the list) and building it yourself wouldn't ever completely work either.  In my case, I could download the driver package (180.29), build it and install it, and everything was hunky-dory during that session.  If I logged out or rebooted, everything hosed up again when gdm loaded; I would get the silly "Low resolution" dialog box and all that jazz.

It seemed like gdm and GNOME were handling the the driver and settings separately, so I built the driver one more time, and started X manually, and it worked, even after a reboot!  So for anyone who wants to do the same, but doesn't know how, here you go:

[LIST=1]
[*]Exit from the GUI.
[*]Hit <Alt><Ctrl><Fx> to load a virtual console (x is a number from 1 to 6).
[*]Login at the command line.
[*]Stop gdm with ```
sudo /etc/init.d/gdm stop
```
[*]Change directories to /etc/rc2.d.
[*]Change the name of S30gdm to s30gdm.  This will keep gdm from loading.
[*]Compile the nVidia driver again, and let the script install the driver.
[*]Start X Windows manually with ```
startx
```
[/LIST]
And there you go!  If you have the same problem I do, GNOME will now work with the nVidia driver.  There are some downsides though:

[LIST]
[*]You have to login at the command line from now on, and run startx every time (or put it in your .bash_rc).
[*]Without gdm, the user switcher applet no longer works (I never use it anyway.)
[*]Also without gdm, you must shutdown and restart the system from the command-line.  Sleep and hibernate still work from within GNOME, however.
[*]Remember that even though a screen saver lock will protect your GNOME session, there is no such lock (that I know of) for the command line, and you will stay logged in at the command line during you GNOME session.   This *may* make this workaround a violation of policy (or just a bad idea) at your workplace, but should be fine for home use.
[/LIST]
I've searched the forums and haven't found a solution for this problem that worked, so I'm putting this here in hopes that it will help someone else.  Mods: if you feel this helpful for the community, feel free to make it sticky.

:confused:
Now, here's my question:  If gdm and GNOME are getting their X settings from two different places, where are those two places?  One of them is obviously reading from /etc/X11/xorg.conf; presumably that's the X server underlying GNOME.  So what is the other reading from?  If I can find that out, I may be able to get both working.
:confused:

Also, for those who are curious, I'm using an evga GeForce 9800GTX+ video card with an evga nForce 780i motherboard.

Good luck everyone!
-Jason

---

### Post by 3Miro on 2009-03-25
The way I did the nVidia driver on two machines:

1. Install Ubuntu/Kubuntu
2. Install driver 1.77 from the Hardware manager
3. After reboot, go to the package manager (synaptic/adept) and install nvidia-180-modaliases, nvidia-180-kernel-source, nvidia-glx-180 and nvidia-glx-180-dev (last one is probably not needed).
4. reboot and now the Hardware manager shows up the 180 driver and that I am using it.

Hope this helps.

Note: step 2 takes care of all the settings of xorg.conf and such so you don't have to go trough all the trouble of editing it yourself. In general, I think you only need to edit xorg.conf to get everything working, but I am not sure of the exact syntax. I have made my share of mistakes in it by not using the Hadrware manager as I am supposed to.

---

### Post by ethoxyethaan on 2009-03-25
i tried to install 180 on kernel 2.6.29 and it diden't create the syslink libglx.so as a result i couldent play dungeon keeper 2.

back to good old 2.6.26

---

