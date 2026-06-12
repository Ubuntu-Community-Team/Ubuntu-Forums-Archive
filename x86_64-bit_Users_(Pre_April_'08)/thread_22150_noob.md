---
title: "noob"
date: 2005-03-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by juicey on 2005-03-25
i have just loaded warty on and everything has gone well it seems rebooted got all additional downloads from net then went to "ubuntu login" I typed my login...then went to "password" I typed that then it went to 
"Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law."
You have mail.
michael1@ubuntudad:"$
What the hell do i type now...and if any 1 can answer will there b more promts ,what will they b ,and what do i type?

---

### Post by Buffalo Soldier on 2005-03-25
Try **startx**. If that fails to load a GUI, try configuring your xserver by typing **sudo dpkg-reconfigure xserver-xfree86**. It will ask for you password, just enter your user password.

---

### Post by kubla on 2005-04-07
[QUOTE=juicey]i have just loaded warty on and everything has gone well it seems rebooted got all additional downloads from net then went to "ubuntu login" I typed my login...then went to "password" I typed that then it went to 
"Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law."
You have mail.
michael1@ubuntudad:"$
What the hell do i type now...and if any 1 can answer will there b more promts ,what will they b ,and what do i type?[/QUOTE]
 
I had this happen on one of the laptops I was installing recently. I didn't pay particular attention to the install process since it's so hand-off and super slick but after reboot I had shell and no graphical environment.

For some reason, and I really haven't investigated why, the ubuntu desktop environment wasn't installed.

You need to do the following:

1) login to your shell environment as you have done above
2) check that your /etc/apt/sources.list is configured to point to the net and not your cd unless you want to install from your cd and then upgrade later
3) sudo apt-get update
4) sudo apt-get install ubuntu-desktop
5) drink a coffee or a beer or both and wait...
6) login to gnome :)

Ian

---

