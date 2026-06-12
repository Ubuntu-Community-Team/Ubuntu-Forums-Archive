---
title: "&quot;Failed to start X server&quot; - HELP!"
date: 2006-04-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by RWW on 2006-04-30
Well I successfully tiptoed my way into shrinking my HSF partition and installed version 5.10 from UBUNTU onto my eMac with 4 Gigs of space.  I get the dual boot question, and can boot into Mac, or start the process into Linux (getting the psychodelic Rorshack "UBUNTU" splash screen as things load up) - but it fails to get me into the graphical user interface. I get a message that tells me "Failed to start X Server".  I can go on to two screens past that, but it's all Greek to me.  ](*,) Can anyone help this newbie walk through this, please oh please - and I will be oh so greatful.  Thanks in advance!

---

### Post by aimislame15 on 2006-04-30
What do the "two screens" say?

---

### Post by RWW on 2006-04-30
The first one is X server output.

The second one is detailed X server output.

I found some related messages by PC users that leads me to believe it's the ATI driver for the monitor.  I've followed the hints to do:
nano /etc/X11/xorg.conf

and replace the line that says-

> driver: "ati"

with;

> driver: "vesa"

but when I exit and try to save, it tells me that it is unable to save, that I don't have correct permissions.  ](*,)

---

### Post by Yimmy on 2006-05-01
Try this instead:
```
sudo nano /etc/X11/xorg.conf
```

It'll ask you for your password.

---

### Post by iammatt on 2006-05-02
I have a similar problum, With the live CD of 5.10 and with 6.06 on my emac, neather gets me to a graphical interface. With 6.06 is complains of the x server not working but tells me it's not configured propelery. would I just type in sudo nano /etc/X11/xorg.conf in the screen it puts me to?

---

### Post by aimislame15 on 2006-05-03
type "sudo su" once youre logged in at the normal black/white console. Then enter your pass, you are now root. now change the file with vi and whatnot. then, exit and reboot. you might need to do a chmod for file permissions

---

### Post by linear on 2006-05-03
It might be easier to try **sudo dpkg-reconfigure xserver-xorg** first, especially if you're not sure what to put into xorg.conf.

---

