---
title: "Feisty Good News Story w/NVIDIA and Beryl"
date: 2007-04-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tanker Bob on 2007-04-20
I made the jump from a stable 32-bit edgy setup to 64-bit feisty yesterday based on discussions here over the last several weeks.  Because of the upgrade from 32- to 64-bit, I was advised to replace the 32-bit setup completely from the 64-bit CD.  Since my /home is its own partition, all my data and most of my settings survived the install.

Feisty installed fine and came up initially with no problems, recognizing my NVIDIA 8800GTS card and installing the proper open source driver.  I prepared written references for when I would install the proprietary 8800GTS NVIDIA drivers, and sure enough, I needed them.  The restricted repository NVIDIA install seemed to work but gave me a blank screen on restart.  Using recovery mode, I installed the drivers directly from NVIDIA and achieved success.  Beryl's install went very smoothly.

Firefox, Thunderbird, OpenOffice.org, and other apps all picked up their previous settings and data without a hitch.  Using Kilz' HOWTOs and others' posts, I got Flash 9 in 64-bit Firefox, Wine, NVU, VMware (thanks Petr Vandrovec), and other 32-bit stuff running over the last day.  I now sit with an almost complete 64-bit setup (haven't started on the scanner yet).

While this should probably go in the Testimony forum, I'm posting here because Kilz, Petr, and other frequent here and I want to personally thank them all.  The update had challenges, but I was able to find answers to almost every issue already posted here.  And Kilz, you were right that the move to 64-bit would be worth it.  I've found the 64-bit package significantly faster than the 32-bit one, and it seems more stable as well.  Also congratulations to the developers on a very nice feisty release.

Thanks to all for your contributions to the community!  :KS

---

### Post by tibbar_eht on 2007-04-20
Hey Tanker could you help me out a bit.  I am tring to do the same thing with the same vid card.  I am not familiar with loading drivers manually.  Is there some place I can go to find a how to?

Cheers,

---

### Post by Tanker Bob on 2007-04-20
> **tibbar_eht said:**
> Hey Tanker could you help me out a bit.  I am tring to do the same thing with the same vid card.  I am not familiar with loading drivers manually.  Is there some place I can go to find a how to?

Cheers,
I found a post somewhere here but I can't put my finger right on it.  Here is the sequence I used from the restore/recovery shell, logged in as myself.  This assumes that you already downloaded the 9755 drivers.

```
sudo sh NVIDIA-Linux-x86_64-1.0-9755-pkg2.run
sudo nvidia-xconfig
```

It will ask you a bunch of questions during the install.  I ran into a message that said I was running at the wrong level, but the install program also gave me the command to fix that.  I don't remember the command, but you'll see it on the screen if you encounter that issue.  Also, allow the install program to write the configuration to xorg.conf.  If you want to run Beryl, someone recommended the following instead of the generic config command above:

```
sudo nvidia-xconfig --add-argb-glx-visuals --composite
```

I did that and it worked fine.

After all was said and done, though, the X server wouldn't remember my settings across restarts.  I had to manually add my preferred resolution and vertical scan rate into the /etc/X11/xorg.conf file with root permission.  After that, it worked fine.  I'm still using an older analog monitor--you may not encounter that issue if you have a digital monitor.

Once you get the Ubuntu/Kubuntu desktop to load, ensure that you go into the NVIDIA setup program from the menu system to set you settings there as well.  Also ensure that you set the image quality to "High Quality."  I couldn't get Beryl to load in edgy without setting that.  I loaded Beryl from the repository and it worked fine after install.

I hope that this helps.

---

