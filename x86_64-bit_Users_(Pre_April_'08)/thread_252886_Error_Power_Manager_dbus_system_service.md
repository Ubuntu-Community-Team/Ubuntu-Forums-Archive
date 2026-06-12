---
title: "Error: Power Manager dbus system service"
date: 2006-09-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Bunro on 2006-09-07
I can not log in to my Ubuntu system in a normal way. login name/ password.
Only via recovery mode I can connect to my system.
When I start $startx.

I am getting the following error:

Power Manager
This program can not start until you start the dbus system service.
It is strongly recommended you reboot your computer after starting messagebus.

My question is how to solve this problem and how can I login normally in to my system.
And/or how can I do a reinstall from the command prompt for my complete system? 

Hopefully there is some one that can help me out!

Regards, Robert

The only “error” I can find is the following;
pico /var/log/Xorg.0.log
(WW) fglrx(0): Specified desktop setup not supported: 8

---

### Post by nachiketa.shukla on 2006-09-11
Hi All,

I am seeing excatly the same error on my 64-bit HP nx6125 laptop.

This renders the ubuntu install completely unusable and the machine just hangs after a certain time.

When I installed the base system this was not a problem. After that I went ahead the installed a bunch of software from the DVD and at the end of it all, I am facing this problem now.

I read varioud posts (some on the internet and some on these forums) and tried the following:

- Booted Ubuntu in recovery mode.
- At the root prompt did "/etc/init.d/dbus start".
- I see a bunch of error messages for the wireless network adapter showing up on screen.
- Waited for sometime since I did not realise what was going on.
- Pressed enter at some point and got the root prompt back.
- Typed "exit" and the system booted to the GUI.
- Logged in and did not see the error.
- Assumed that things were ok and was looking to fix my system startup so that the dbus service gets started normally.
- Then the system froze again and had to reboot and be back in windows.

Any help or suggestions is appreciated.

Ubuntu - 6.06 64-bit
Machine - HP nx6125 laptop.

Please let me know if additional details will help. I would be happy to provide them.

Thank you.

Regards,
-- Nachi

---

### Post by nachiketa.shukla on 2006-09-12
Hi,

I reinstalled Ubuntu 6.06 64-bit version on my laptop again and this issue went away.

I do not know what was going wrong but thought that this might help.

Thank you.

Regards,
-- Nachi

---

### Post by bdwetzel on 2006-10-16
Hey, 
I have the same problem, reinstall does not help.  Did you ever get that fixed?  If so, what did you do?

---

### Post by bdwetzel on 2006-10-16
I fixed it!:-D  didnt take too long eh?  If anyone else has this problem (same as me and bunro) try
```
sudo /etc/init.d/dbus start
```
worked for me..and i have no idea what i am doing.  So good luck.

---

### Post by RAOF on 2006-10-16
> **bdwetzel said:**
> I fixed it!:-D  didnt take too long eh?  If anyone else has this problem (same as me and bunro) try
```
sudo /etc/init.d/dbus start
```
worked for me..and i have no idea what i am doing.  So good luck.

What you're doing there is starting the DBUS messaging system.  Basically, it's a way for applications to talk to each other, and is heavily used by Gnome (for example by the theme manager, to tell the system when the theme has changed, etc).

I'm not sure why it's not running by default, though.  Have you modified the default system start-up services?

---

### Post by bdwetzel on 2006-10-17
Nope, like the first guy mentioned because of this login issue I have to boot in recovery mode...So no i have not changed anything
In fact when i rebooted(shut down..not log out) it had the dbus message again...so I am not sure how to tell it to run by default..let me know if you do.

---

### Post by M8M on 2006-10-21
I keep getting this same error AFTER I have logged in, then I have about 1 min to quickly do something before the whole system freezes up. I have attempted the suggestions above but they didn't work. Any other suggestions?

When I enter the command suggested above, the error disappears but it will still freeze up again.

---

### Post by Bunro on 2006-10-23
Thanks every body for your replay!


 After some days of fumbling around in the system I reinstalled Ubuntu. I think the problem was connected with the ATI driver that does not want to be installed correctly.
 With the new installation it went ok.
 

 Thanks again for the help!;)
 
Best Regards, Robert

---

