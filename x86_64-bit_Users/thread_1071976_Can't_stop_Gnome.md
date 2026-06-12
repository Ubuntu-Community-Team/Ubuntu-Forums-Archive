---
title: "Can't stop Gnome"
date: 2009-02-16
forum: x86 64-bit Users
---

### Post by ceedub7 on 2009-02-16
I was trying to turn off Gnome in order to install Nvidia drivers, but it won't turn off and give me a prompt.

"sudo /etc/init.d/gdm stop" gives the message "* Stopping GNOME Display Manager..." but nothing actually happens.

"sudo killall gdm" just gives me a garbled and unusable display.

I am sure I use Gnome. While I can just boot in safe mode and get a text prompt from there, I would like to find out what the problem is here.

Any suggestions?

---

### Post by perlluver on 2009-02-16
I assume that the restricted drivers didn't work for you?  System>Administration>Hardware Drivers.  If they are not there, you could try envy, they both make it easier to install Nvidia drivers.

---

### Post by dzark on 2009-02-16
So you Ctrl-Alt-F2 (or F whatever) out of the desktop into another text login screen (console)?

After logging in, try ```
sudo /etc/init.d/gdm stop
```

It will come up with "Stopping GNOME Display Manager..." afterwhich you'll be back at prompt. You can verify that it's not running my pressing Alt-F7 which is the console where desktop the normally runs

also try ```
ps -A | grep gdm
```
if that results in anything, then gdm is still running... 

Now run Nvidia installer.. 

And then start it with

```
sudo /etc/init.d/gdm start
```

---

### Post by ceedub7 on 2009-02-16
Thanks for the replies. I needed to hit Ctrl-Alt-f2 instead of trying to turn off gdm from a terminal window.

---

