---
title: "Jaunty 64bit = the apocalypse [Help]"
date: 2009-09-01
forum: x86 64-bit Users
---

### Post by ApEkV2 on 2009-09-01
I don't know if it's because I used update manager to go from 8.10 to 9.04, but my system is almost useless now.

Problem is on startup random scripts essential to the desktop gui fail on startup.

[color=red] At least three scripts fail at random times on startup resulting in having to shutdown the computer by holding in the power button. [/color]

[color=blue] Another bizarre creature spawned from this disaster is whenever these scripts fail, it notifies me that they fail, and asks me to delete them! [/color]

[color=green] Now though all of a sudden firefox decides to smoke some crack and not scroll very smoothly (sorta like a fresh windows install before the graphics card drivers are installed) [/color]

Any suggestions other than reinstall from a live cd would be great.
(I really don't want to ruin all my configurations and what not-only to have it not work still)

ati radeon hd 2400 pro card is being used 

EDIT: forgot to mention the fact that the following programs are limited or no longer working: converting formats using ffmgeg, 
totem randomly refuses to play videos and music, recordmydesktop, xvidcap, istanbul, and apache freezes after performing a server restart.

EDIT: [color=red] Now compiz isn't working (the cube and that stuff), and instead of usually 500mb being loaded into ram on startup, now there's only 300mb [/color]

[color=red] EDIT: Now root authentication doesn't work comes up with "Error copying '/home/mccarty/.Xauthority' to '/tmp/libgksu-NzbO3b': Permission denied" [/color]

---

### Post by ApEkV2 on 2009-09-01
.

---

### Post by falconindy on 2009-09-01
> **ApEkV2 said:**
> (I really don't want to ruin all my configurations and what not-only to have it not work still)
Backing up your $HOME folder should cover the majority of your config.

I'm a little confused though -- were you previously running Intrepid 32-bit? If so, you made your own bed. Though your first impression of Jaunty has been a sour one, I assure you its a wonderful beast.

---

### Post by ApEkV2 on 2009-09-01
i was using 64 bit ubuntu from the start

I don't here alot of problems with 32bit ppl

[color=red] I used update manager to upgrade to Jaunty [/color]

---

### Post by bford16 on 2009-09-02
Suggestion:

Boot in Recovery Mode. Remove your ~/.gnome2 and ~/.gnome2_private folders, any session backup files, and your ~/.Xauthority file (make sure they are the ones in /home/mccarty). Then try booting normally. Also, you may have to reconfigure the X server with "dpkg-reconfigure -phigh xserver-xorg." You should do this in Recovery mode, too.

---

### Post by ApEkV2 on 2009-09-02
"Boot in Recovery Mode. Remove your ~/.gnome2 and ~/.gnome2_private folders, any session backup files, and your ~/.Xauthority file (make sure they are the ones in /home/mccarty). Then try booting normally. Also, you may have to reconfigure the X server with "dpkg-reconfigure -phigh xserver-xorg"

Thanks fixed part of the problems.  Now firefox scrolls the way its suppose to.  And i haven't had a problem with sudo yet (cross fingers)

[color=red] Compiz still doesn't work and the compiz-check still brings up [/color]

".....[color=blue] Driver in use:         radeon
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) [/color]...."



Tried 32bit ubuntu and that is failsauce too.  I tried kubuntu, but the gui doesn't appeal to me as much as gnome did.
So this gives me the opportunity to try out many other distributions of linux xD
Next is xubuntu
then after that slackware 13 * (a dvd iso xD) *
after that well nobody knows

---

### Post by interval1066 on 2009-09-08
> **ApEkV2 said:**
> 
[color=red] Compiz still doesn't work...[/color]


Well there's your problem. Just kidding. There's a point at which fail > recovery possibility, might need to re-consider a fresh install of the version you want.

---

### Post by ApEkV2 on 2009-09-08
I got rid of my current setup and installed xubuntu 9.04 64bit on ext4. xD
I had the same graphics problem that I had in regular ubuntu, but fixed it by following a tutorial about installing the newest ati linux driver.
[color=red] [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide) [/color]
Although now I had to make scripts that mount my other ntfs drives......but
I must say xubuntu ** is ** a lot faster than regular ubuntu, but i do miss compiz.

---

