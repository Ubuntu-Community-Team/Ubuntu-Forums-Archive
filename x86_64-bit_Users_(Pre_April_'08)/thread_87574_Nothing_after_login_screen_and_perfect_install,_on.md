---
title: "Nothing after login screen and perfect install, on powerbook g3"
date: 2005-11-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by youngdaniel on 2005-11-08
Hi all

If anyone could shed the light on this problem I would be so happy to get into the world of linux!!!

Installed the lasted distro of ubuntu on a Powerbook G3, 400mhz, 192mb ram.
Installs perfectly with no issues at all!

Get to the login screen, enter username and password, all is good! 
Then goes through to a brown screen with an ACTIVE mouse cursor! 
It even plays the little jingle to welcome you.

But after that I see no buttons, no icons, no taskbar or anything???

Any Ideas at all???

Please help as I really really want to get in to ubuntu!!

---

### Post by youngdaniel on 2005-11-09
Hey

I have been searching high and low for a solution.

2 possible solutions
[LIST]
[*]DHCP
[*]Time and Date
[/LIST]

During install I did not setup networking, and the date is set up to 1904!!!
Could someone please tell me how to set the time up without entering GNOME??

Thanks

---

### Post by AikenDrum on 2005-11-12
Hi Daniel,

I had this problem with my G3500 ibook - I got around it by;
* boot to the blank background
* crtl-alt F6 (will shift you to a text terminal)
* login with your username / password
* type 'man hwclock'  to check out the hwclock command;  you basically need to;
sudo hwclock --set --date="11/12/05 18:20:00"
sudo hwclock --hctosys

this should fix the clock,  then sudo reboot and you should be sorted !

Scott.

---

