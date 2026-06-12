---
title: "Mobility 9700 Gaming Performance"
date: 2008-03-27
forum: Wine
---

### Post by rickatnight11 on 2008-03-27
Well, I just got back from a presentation at my school (VCU) by Richard Stallman!  It was such a great talk, and I really learned a lot about the origins of GNU and Linux (until today I was under the common misconception that Linus did it all.  Hardly!)  Well, as a new Ubuntu user (haven't transitioned fully yet, have my drive partitioned in half, Gutsy/Vista) I left the presentation feeling fully charged to leave my Windows ways...which brought me back to one problem I'm having with Wine and gaming.

I have an ATI Mobility 9700 chip in my laptop.  I followed [this]("http://ubuntuforums.org/showthread.php?t=580748&highlight=ati+mobility+9700") thread to get the desktop working well with all the Compiz Fusion bells and whistles, and it's working like a dream.  I installed Wine, installed Steam, and symlinked the steamapps folder to the one on the Vista partition so as not to have to redownload (and restore) all the game files.  I can't get Counter-Strike Source to run without appending the -dxlevel 8 to the launch options, and it *does* load, but in the lowest resolution possible.  I have only gotten the game to start a map once, but with performance at less than 1 fps.  I have tried playing with wincfg and searching for any useful threads, but alas have not been successful in fixing my conundrum.  Could anyone help me get Wine configured properly with my card to get 3D acceleration working?  I do understand it won't run as fast as in native Windows, but certainly I should be getting better performance than this.  Thanks in advance for any help! :)

---

### Post by rickatnight11 on 2008-03-28
Well, now it's no longer an issue with gaming performance, as once again I have made things worse.  I tried downloading the proprietary drivers for my Mobility 9700 from ATI's website thinking that it might help my graphics performance.  Of course I was wrong.  After rebooting I could only get a resolution of 640x400.  I tried uninstalling compiz and xgl, and disabling and enabling the ATI driver from the Restricted Drivers Manager.  After rebooting it would at least give me normal resolutions again, but 3d acceleration (and 2d for that matter) is totally disabled.  Desktop effects can be enabled but are *very* sluggish and slow.  I guess I just need a guide to properly get my graphics card working.  This is giving me nightmares from Dapper Drake all over again.  Can anyone help me?

---

### Post by mikedep333 on 2008-03-29
Try going to the command line while X is not running
```
(ctrl +alt + f1)
(login)
sudo /etc/init.d/gdm stop (replace gdm with kdm if you are running kubuntu)
```
and then running:
```

sudo dpkg-reconfigure xserver-xorg.

```
From it, select fglrx as your driver and chose to have it auto-detect stuff when asked.
Then start the graphical session back up again
```

sudo /etc/init.d/gdm start
(hit ctrl + alt + f7 if necessary)

```
If that doesn't work, go repeat the process but select ati as your driver. This will get you the limited functionality open-source driver. From the X session, you can then retry to install the ATI proprietary fglrx using envy.
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

BTW: Ubuntu 8.04, which has X.org 7.3 with autoconfiguration, should prevent problems like these. Don't try replacing 7.10 until it is released though.

---

### Post by rickatnight11 on 2008-04-01
Thanks for the guide!  Unfortunately when I switch over to terminal the resolution is all out of wack.  The letters a very large and the lines go way off the screen so I can't see more than the first three lines (and only half of those.)  Any way to fix the resolution for the command line?  Here's a picture of what it looks like:

[ATTACH]64513[/ATTACH]

---

