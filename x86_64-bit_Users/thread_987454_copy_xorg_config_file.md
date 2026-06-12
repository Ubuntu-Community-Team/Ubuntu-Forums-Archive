---
title: "copy xorg config file"
date: 2008-11-19
forum: x86 64-bit Users
---

### Post by zootesh on 2008-11-19
im having trouble installing ibex. Sometimes the installation hangs on starting powernowd. I can get it to install without this happening but there is a problem with xserver or xorg or whatever (ima noob) and restarting gdm fails. Based on other stuff I've read I could potentially fix this by replacing the xorg file but I have no clue really what do do and can't find the commands to do this because I just get command prompt.

So lets say I get hardy running with my graphics card installed and running correctly. I plan on saving the xorg file to a flash drive. Then installing ibex getting the xserver problem then replacing the file from the one on my flash drive.

Anywho...could this possibly work and if so can somebody provide the detailed commands on how to do this.

thanks

ps i have searched the posts already all the solutions i've read seemed way too over my head(ppl didn't give the commands just said what to do)

im running toshiba A305D-S6886. ATI Mobility Radeon HD 3470/ATI Radeon HE 3200 Graphics. AMD Turion 64 Dual-Core Mobile. 4gb ram. AR9281 wireless card.

---

### Post by dabl on 2008-11-19
No.

*buntu 8.10 has a new version of X.org, and it does not use the xorg.conf file in the same way as the X.org that is in 8.04.  So you don't want to try to re-use the old xorg.conf file.

Your post title says "Kubuntu" but then you wrote "restarting gdm". In Kubuntu, the _K_ _D_isplay _M_anager is used, not the _G_nome _D_isplay _M_anager, so it's ```
sudo /etc/init.d/kdm start
``` to start it from the CLI.

You say "installation hangs starting powernowd", but I think you must mean "initial boot of the installed system", right?

If you've got the system installed, even if video isn't working great, you should be able to install EnvyNG and use it to install the radeon or fglrx driver, as appropriate for your hardware.  At the CLI:

```
sudo apt-get update
```

```
sudo apt-get install envyng-core
```

then, when it is installed

```
sudo envyng -t
``` 

and follow the guidance to select your driver.

---

### Post by John Jason Jordan on 2008-11-19
> **zootesh said:**
> im having trouble installing ibex. Sometimes the installation hangs on starting powernowd. I can get it to install without this happening but there is a problem with xserver or xorg or whatever (ima noob) and restarting gdm fails. Based on other stuff I've read I could potentially fix this by replacing the xorg file but I have no clue really what do do and can't find the commands to do this because I just get command prompt.

So lets say I get hardy running with my graphics card installed and running correctly. I plan on saving the xorg file to a flash drive. Then installing ibex getting the xserver problem then replacing the file from the one on my flash drive.

Anywho...could this possibly work and if so can somebody provide the detailed commands on how to do this.

First, the file that you need in Hardy is /etc/X11/xorg.conf. This file contains the configuration for the video, the mouse, and the keyboard. In Intrepid this file was changed so that now all it does is the video. Mouse and keyboard configurations were moved to the Hardware Abstraction Layer, and there are now different utilities for changing them. 

If you upgrade a Hardy installation to Intrepid the upgrade will automatically put remark (#) in front of all the lines relating to the mouse and the keyboard in your xorg.conf file. If you install Hardy, copy the xorg.conf file to a flash drive, then install Intrepid and replace the xorg.conf file with the one from Hardy, it probably won't work.

A better solution would be to figure out what is wrong with the video in Intrepid. A good start would be to search the forums for your video chip. To find out exactly what it is run the command "lspci." 

Programming a GUI is the blackest of black arts.

---

