---
title: "Nokia sync program runs but needs file explorer?"
date: 2008-05-22
forum: Wine
---

### Post by tnc on 2008-05-22
Hello and thanks for looking.
I have a Nokia 6620 cell phone.  The software for the phone installed in wine and runs normally.  However, it seems to need a file browser to access the phone (based on little windows experience). 
Is there a file browser available for/in wine?
Can wine be set up to use the Ubuntu file browser?
Or if someone knows another way to get images, contacts, etc. off a Nokia 6620 I'm all ears!!  (Tried several programs but only got a connection with Gammu, not able to download)
Thanks.
Tim

---

### Post by pseudo-random on 2008-05-22
tried Gnokii?

---

### Post by tnc on 2008-05-22
Yep.  It comes up, says "connecting...." and then craps out.  I haven't pursued that one further.  It's worth more effort?
Thanks.
Tim

Edit: ran gonkii in terminal for out put:

tnc@tnc-desktop:~$ xgnokii
Couldn't read /home/tnc/.gnokiirc config file.
Couldn't read /home/tnc/.gnokiirc config file.

(xgnokii:14314): Gtk-WARNING **: horizontal scrolling not implemented

(xgnokii:14314): Gtk-WARNING **: horizontal scrolling not implemented
Lockfile /var/lock/LCK..ttyS0 is stale. Overriding it..
Telephone interface init failed: Command timed out.
Quitting.
Failed to open the phone. Quitting.

So, it would seem that gnokii is working fine but can't find the phone.  Ongoing theme.....

---

