---
title: "X server not starting :("
date: 2005-12-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by kb_ganesh on 2005-12-02
The power tripped and so, my comp went off as i dont have a UPS...and next time i started ubuntu, i get an error that X-Server could not be started...from what i understood from the log file it showed, it says Nvidia Kernel module hasnt been installed...though my computer has been running ubuntu 5.04 amd64 without any problems whatsoever for the past 1 and a half months or so..can someone look into the log file and let me know what the problem is and how i can solve it? (i have done a lot of customization on my 5.04 ...thats why i still havent shifted to 5.10..)

thanks

---

### Post by xmastree on 2005-12-02
Presumably your xorg.conf calls the nvidia driver.
```
Driver		"nvidia"
```
Try changing that to vesa and see what happens. It might get you back to the desktop at least.
```
Driver		"vesa"
```Don't change the Identifier, just the driver.

---

### Post by 23meg on 2005-12-02
Doing a reinstall of the nvidia drivers should fix the problem.

---

### Post by kb_ganesh on 2005-12-02
that was real fast!! and it worked like a charm too!!

thanks to xmastree!!

and 23 meg, i guess i will do that too... :)

---

### Post by xmastree on 2005-12-02
Great! :)
I had to do a similar thing recently, I transferred a hard disk from one PC to another completely different spec one. Intel 810 drivers don't work well with nvidia cards. :)

---

### Post by Chris Griste on 2007-06-30
I am really new to Ubuntu and Linux.  How do you change the driver to Vesa?

Chris

---

### Post by praxis22 on 2007-06-30
Do the following:

**sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak**

Search for a Line that says "Driver" and then a name, you can do this with the following command:

**grep -i driver /etc/X11/xorg.conf**

This will list several lines, some will say wacom one kbd another mouse, and the last will says something else, possibly "ati", "radeon", "nvidia", "fglrx", etc.

This is the line you have to change, you can do that as follows:

**sudo gedit /etc/X11/xorg.conf**

Save your file out. Then hit Ctrl - Alt - Backspace, and this will restart X

If you can't get X up at all let us know and we can get around that too.

---

### Post by xmastree on 2007-07-01
The above is fine if your X server is ok, since you need it in order to use gedit.

If you're stuck at a console, use **nano** rather than gedit.

---

### Post by Chris Griste on 2007-07-01
Thanks a lot, problem solved.

---

