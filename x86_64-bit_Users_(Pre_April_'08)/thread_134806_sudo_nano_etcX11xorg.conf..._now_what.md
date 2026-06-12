---
title: "sudo nano /etc/X11/xorg.conf... now what?"
date: 2006-02-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by imacQ on 2006-02-22
i went into X11 file and disabled the dri to speed things up, and used the " sudo /etc/init.d/gdm restart" command to restart gnome. now i have a black terminal screen which asks me to login. okay  fine, i login and get the $ prompt. how do i get back to gnome, or restart computer entirely. when i type in "exit" it logs me out and then asks me to login in. :confused:  i know it's simple; i just don't know what it is. please help. thanks.

---

### Post by spencer on 2006-02-22
Hi,

I believe "startx" is what you type. I hope that works.

-spencer

---

### Post by 5-HT on 2006-02-22
Not sure if there is now an issue with your xorg.conf, but to see if you can get X and gnome back, what about trying (instead of the gdm restart):

```
sudo /etc/init.d/gdm stop 
sudo /etc/init.d/gdm start 
```

and switch to vitrual terminal 7 (where X usually displays) by: ctrl+Alt+F7.

If that doesn't work, what about 
```
 startx 
```

Finally, if it just doesn't seem to start, then to reboot:
```
 sudo shutdown -r now 
```

If it X won't load on reboot, looks like something may be amiss with your xorg.conf.

HTH

---

### Post by imacQ on 2006-02-22
well, tried the stop and start gnome commands. all looked good for a moment, but whoops after loging i get to brown screen; have cursor and nothing else?

okay now restarted with restart button and all came up as it should. yes there is an increase in speed.

---

