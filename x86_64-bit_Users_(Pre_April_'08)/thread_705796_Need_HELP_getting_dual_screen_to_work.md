---
title: "Need HELP getting dual screen to work"
date: 2008-02-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by on4now4 on 2008-02-23
I am net to the whole Ubuntu Os but i got rly pissed at windows and decided to give it a try but after installing it i cant get anything to display on my second screen i am new to Linux so i really have no clue what i am doing in the settings it does say that i have 2 displays and that it should be working but after i enabled it instead of having dual monitor i got a second desktop that i can scroll over to on my single monitor.

---

### Post by Sam Lars on 2008-02-23
I think you confused a desktop for a monitor...
What kind of video card do you have?

---

### Post by on4now4 on 2008-02-23
i have a 7900 gs

---

### Post by Sam Lars on 2008-02-23
Do you have the restricted drivers enabled?
Try using nvidia-settings.  See if the save configuration works.  If it doesn't, you can set up the xorg.conf manually.

---

### Post by on4now4 on 2008-02-23
i do have the nvidia accelerated graphics driver enabled but i don't think that this is the actual driver for my card when i try to install the actual driver that i get from nvidia's site it wont install this could be part of the problem

---

### Post by Sam Lars on 2008-02-23
No, that driver should be right.
Try using nvidia-settings, can you get dual monitor through that?

---

### Post by on4now4 on 2008-02-23
how do i get to the nvidia setting as i said i am new to linux

---

### Post by Sam Lars on 2008-02-23
Open a terminal or press Alt+F2 and type
```
nvidia-settings
```
Go to the second option, X Server Display Configuration, and you should see both monitors... try setting it up for TwinView there.

---

### Post by on4now4 on 2008-02-24
i tried that and i get this message

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

---

### Post by Sam Lars on 2008-02-24
So run
```
sudo nvidia-xconfig
```
Log out and press Ctrl+Alt+Backspace
When it comes back up, log in and try it again.

---

### Post by on4now4 on 2008-02-24
no that did not change anything also when i ran that new code nothing appeared to run it just kinda closed the run box is that what it is supposed to do

---

### Post by Sam Lars on 2008-02-24
Yes, it really shouldn't show anything.  Post your xorg.conf again to make sure it did what it was supposed to.
So what do you get in nvidia-settings?

---

### Post by on4now4 on 2008-02-24
ok well i don't now what i did but now i can get into the nvidia settings
so now that im there i have a new prob i can get a picture to display on both my screens but i cant get it to display my primary on the right screen

---

### Post by Sam Lars on 2008-02-24
I'm not sure what you're saying... is the secondary screen set to think it's on the wrong side?
Or do you want your second screen to be the primary?  You may have to switch the cables on the card.

---

### Post by on4now4 on 2008-02-24
it is set so that what i want the primary to be is the secondary i have tried just switching the cables and when i do that it is just black also i have done everything in the settings i have seen that should make them switch but they just don't switch whatever i do nothing changes like it should.  to sum it up when i change it to the right setting it just changes itself back to what it used to be and doesn't change anything

---

### Post by Sam Lars on 2008-02-24
Switching the cables should change what the computer uses as its primary.  Are both monitors the same?  You may have to reconfigure X if they aren't.
Does nvidia-settings change which monitor is primary, or is it wrong from the start?

---

### Post by on4now4 on 2008-02-24
no both monitors are not the same one is a crt and the other is an lcd and when i switch the cables than both of them are black it does not show any picture

---

### Post by Sam Lars on 2008-02-24
Okay, try switching the cables and then running
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and follow the instructions.  They should then work with startx or a boot.

---

### Post by on4now4 on 2008-02-24
that did not seem to do anything

---

### Post by Sam Lars on 2008-02-24
So they are both black still?

---

### Post by on4now4 on 2008-02-24
oh no there not black but there still in the same spots it dident switch the primary

---

### Post by Sam Lars on 2008-02-24
If you go into nvidia-settings, disable the primary screen, then enable it as TwinView, place it, and apply, does that change it?

---

### Post by ryanhaigh on 2008-02-24
I don't know if the concept of primar/secondary applies here. You can use the Position option in nvidia settings to place the second monitor to the left of the first if that is what you are after. You can then just move the panels to the screen you want if that is what you are referring to as far as primary/secondary,

---

### Post by on4now4 on 2008-02-24
when i try to apply that i get this message
"The XRandR X extension was not found.  This extension must be supported by the X server and enabled for display configuration settings to be dynamically applicable."

---

### Post by ryanhaigh on 2008-02-24
I do not get that message but it seems as though its saying you can't apply the changes to a running x-session so backup your current configuration, run nvidia-settings as root and save the changed configuration to X configuration file and then restart X.

open terminal Applications>accesories>terminal then to 

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-settings
change the monitor configuration as required and press the Save to X Configuration File
close nvidia-settings and the terminal
restart the X server by pressing ctrl-alt-backspace

---

### Post by on4now4 on 2008-02-24
alright i am new to Linux so i don't entirely understand what u said what "backup your current configuration, run nvidia-settings as root and save the changed configuration to X configuration file and then restart X.  how do i do this and what is restart x

---

### Post by Sam Lars on 2008-02-24
To back up you configuration:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.back
```
That just makes a copy so that you can go back to it if you really mess things up.
Then
```
sudo nvidia-settings
```
sudo will run it as root.  Set it up how you want it, apply to test it, and then Save Configuration.
To restart X, log out and then press Ctrl+Alt+Backspace.  You don't have to log out, but it's a good idea.

---

### Post by ryanhaigh on 2008-02-24
The instructions at the end of my post cover what you will need to do.
> **ryanhaigh said:**
> 
open terminal Applications>accesories>terminal then to 

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-settings
change the monitor configuration as required and press the Save to X Configuration File
close nvidia-settings and the terminal
restart the X server by pressing ctrl-alt-backspace

---

### Post by on4now4 on 2008-02-25
thanks that seems to have worked now at least i have what i want as the primary screen but the log in screen still pops up on my secondary monitor i dont know if trying to fix this is pushing my luck but if either of u know how i could change the screen tha the login pops up on that would be helpful

---

### Post by Sam Lars on 2008-02-25
So you switched cables and it's still on the secondary screen, or now it's on the secondary screen?
I'd suggest what ryanhaigh said; get the login on the screen you want and then move the panels to the screen you want... would that do what you want?

---

