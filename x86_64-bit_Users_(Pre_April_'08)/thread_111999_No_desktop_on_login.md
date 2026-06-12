---
title: "No desktop on login"
date: 2006-01-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by ikst on 2006-01-03
Hello, 

i just installed ubuntu on my powerbook g3 pismo. Installation process went by without errors. But when i want to login i only here gnome chimes and i only see mouse pointer. No desktop, nothing. On failsafe gnome there is no difference.

Anyone have any ideas ?

---

### Post by stuporglue on 2006-01-03
See if the same happens when you log in and start X11 from the console. 

Switch to a console (ctrl+alt+F2) and log in there. 

Stop GDM:
$ sudo /etc/init.d/gdm stop

Make Gnome start when you log in
$ echo "xterm &" >> ~/.xinitrc
$ echo "exec gnome-session" >> ~/.xinitrc

Start X11:
$ startx

What happens, and what are the error messages, if any?

---

### Post by ikst on 2006-01-04
Same thing. When i run startx there is that gnome sound again and xterm shows but no desktop.

I tried to reinstall and same thing happens.

---

### Post by Peter76 on 2006-01-04
try : sudo dpkg-reconfigure xserver-xorg
good luck

---

### Post by slux on 2006-01-04
Sounds like your system date is currently set to early 20th century. There's a known bug with GNOME that causes it to behave as you describe on Macs if the clock is too far (?) off.

---

### Post by gdgardnerw on 2006-01-05
[QUOTE=ikst]Hello, 

i just installed ubuntu on my powerbook g3 pismo. Installation process went by without errors. But when i want to login i only here gnome chimes and i only see mouse pointer. No desktop, nothing. On failsafe gnome there is no difference.

Anyone have any ideas ?[/QUOTE]

I had some similar problems on my G3 iMac (333 MHz) when using Ubuntu Live. The following instructions helped me which turned out to be a refresh rate issue.

[QUOTE=twongkee]
drop to console (ctrl - option F1)
** this means once you boot up to a blank screen hit the 'ctrl' key, the 'option' key and the F1 key all at the same time. you'll be in a terminal window. **

** if you need to log in use the name ubuntu to log in. **

and edit the X config file as follows:

** type this in exactly as you see it (vi is a terminal editor)**
sudo vi /etc/X11/xorg.conf

change the frequencies in monitor section as follows:
** find this part in the file you are now in (xorg.conf) and make these changes **

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 60-60
VertRefresh 43-117
EndSection

** after the changes then hit the 'esc' or 'escape' key, then type ':wq'
** no 'quotes' -- but yes the ':' is part of the command
** that will write the changes to the file and quit from vi **

** restart X by typing: sudo /etc/init.d/gdm restart
** or maybe just hit 'ctrl' 'alt' 'delete'
that should be it. now ubuntu should start right up.
[/QUOTE]

If it is a date issue, drop to console and change the system date with the command:

[QUOTE=book-linux]
sudo date mmddHHMMYYyy

so
date 121520152005
Dec 15 8:15 2005

or date 010309392006
Jan 3 9:39 2006

Yes for some reason debian and ubuntu are very date sensitive. Even apt-get will not work if you have the incorrect date.[/QUOTE]

Good Luck!

---

### Post by berniej on 2006-02-20
Thanks a lot gdgardnerw!  The trick on changing dates helped me out of a conundrum that caused me to reinstall Ubuntu "Breezy" on my ancient clamshell iBook.

---

### Post by Flash9000 on 2006-02-20
I installed Ubuntu the other day on my G5 with dual monitors and the screen went black after boot up.  I just unplugged one of the monitros and now everything is great.

---

### Post by Flipper on 2006-02-20
If you have any sound problems, check my previous post :) 

[QUOTE=Flipper]Hi, I removed my ibook clamshell's battery and Breezy booted to login normally, and when i entered my username/password it went to a brown blank screen..

I searched in the forum and i found out that the problem was related to the date of the system cause it was reset to jan 1 , 1900.. so i pressed Ctrl+alt+F1 and changed the date with the date --set command, startx and wverything was nice and clean again except for the sound :| 

The problem is:

I can hear the sounds ( so it isnt hardware ) but when i open the sound icon (near the clock) i get an error that says:

"Registry is not present or it is corrupted, plase update it by running gst-register"

Can anyone help me? do i have to re-install any package or something?[/QUOTE]
[QUOTE=Flipper]Solved! reiinstalled the GSfilters and everything is fine now[/QUOTE]

---

### Post by johnnylinux on 2007-04-10
Ok After Much Searching ;i Have Solved The No Desktop Problem!
On A Mac G3 Powerbook! You Have To Reinstall Your Mac Os 9.2 ; You Can Use Os 8 Also ; After Reinstall Of Mac Os ,reboot To Mac Os Open Control Panel, Set Time And Date!! Place Ubuntu (i Have Breezy Badger)in Cd Tray
And Reboot When You Hear The Chime Press The  C  Key Untill You See The
Boot Screen! And Reinstall Ubuntu!!! Thats It!! Once Installed, Open System Updates And Update Ubuntu! This Will Take Some Time! After Fully Updating Ubuntu You Can Open Add Or Remove Programs And Add What You Like;then Open Synaptic Package Manager Go Thru And Pick What You Want This Will Take Some Time Then Mark All Updates And Apply. Open System Update And Scan For Updates! You Will See A Version 6.06............. Do Not Install Updated Ubuntu!!!! As There Is A Bug You Will Lose Your Wireless Adapter!!!!!!!!!.i Hope This Helps!!!!

---

