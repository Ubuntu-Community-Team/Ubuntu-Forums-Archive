---
title: "Can't login to GNOME after upgrading from Breezy to Dapper"
date: 2006-04-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by MarkHn on 2006-04-08
Hardware: 
Fujitsu Siemens Amilo A1650 Laptop AMD64 with 
ATI Radeon Xpress200M graphics card. 

I had problems getting the GUI to work with this card when I installed Breezy, I finaly got it working in the end after 3 days of going from newbie to learning how to recompile the kernel and get fglrx drivers working. 
After that experience I didn't even try to get my built in WiFi card working.

Now after upgrading to Dapper I get the GUI login screen but cannot login. 
If I try to login as a user, it accepts my username and password and then the screen changes to a browm background. I can still move the mouse pointer around the screen. But it doesn't load any further.

If instead of logging-in I select Options (bottum left of screen) then Configure Login Manager, I enter the root password: It appears to login, I see the configuration menu for a second then it returns to the GUI login screen.
Any Ideas?

---

### Post by amohanty on 2006-04-08
1. From the grub menu (where you have the option to select the kernel to boot into) select the "Recovery' option
2. On the command prompt login as yourself
3. type **startx** to fire up the UI.
4. try logging in to display the behaviour you mentioned above
5. Once you are stuck use Ctrl+Alt+Backspace to exit out of X
6. Post the contents of **/var/log/Xorg.0.log** and the output of **dmesg | tail -n 50**

AM

---

### Post by MarkHn on 2006-04-08
The files are attached. I hope they are useful.
When I typed startx, the GUI started and displayed a grey screen but did not go any further. the mouse pointer worked, a black X, I could move it around the screen.

---

### Post by amohanty on 2006-04-10
Ok try this on the recovery console:

**sudo dpkg-reconfigure xserver-xorg**

Select defaults till the screen that prompts you to select modules or something to that effect. If **dri** is selected, de-select it and continue through to the end.

Restarts X using **startx** and if you are still having trouble, repost the log file and dmest output as you did above.

HTH
AM

---

