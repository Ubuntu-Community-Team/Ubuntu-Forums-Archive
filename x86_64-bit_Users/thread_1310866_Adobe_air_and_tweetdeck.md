---
title: "Adobe air and tweetdeck"
date: 2009-11-02
forum: x86 64-bit Users
---

### Post by barbz127 on 2009-11-02
Hi all,

I have managed to get adobe air installed and after doing a

"sudo cp /usr/lib/libadobecertstore.so /usr/lib32" 

The installer and uninstaller will open.

I have tried installing tweetdeck from their site and from a .air file but everytime I get an error "Sorry, adobe air has a problem running on this computer" when I hit ok on this box it reappears until I hit the exit button up the top.

Has anyone had tweetdeck working?

Im running 9.10 64bit.

Cheers
Paul

---

### Post by timgood on 2009-11-02
If you are using an AMD processor you may have problems getting Adobe Air to work properly. I understand that Adobe are looking into the problem. Many AMD processor owners have reported problems.

---

### Post by barbz127 on 2009-11-02
Im running an intel processor.

Paul

---

### Post by barbz127 on 2009-11-03
tested this and got it working on a VM - does it work for anyone else?

[http://technologycrowd.com/2009/10/22/install-tweetdeck-on-64-bit-ubuntu-linux-desktop-2/](http://technologycrowd.com/2009/10/22/install-tweetdeck-on-64-bit-ubuntu-linux-desktop-2/)

cheers
Paul

---

### Post by barbz127 on 2009-11-03
Can confirm the above instructions work - well have on 2 out of 2 for me so far!

cheers
Paul

---

### Post by e.m.fields on 2009-11-18
@barbz127
I have similar problem: "Sorry, adobe air has a problem running on this computer". 

Ubuntu 9.04
64-bit AMD processor
Adobe AIR 64-bit deb

Looking forward to learning the solution - I am pretty sure that this can be gotten around with the 32-bit versions using "getlibs" workaround (uses 32-bit applications on 64-bit machines) but I really prefer not to do so, as I don't really trust this not to mess something else up.  =P

---

### Post by e.m.fields on 2009-11-18
UPDATE:
This thread [http://ubuntuforums.org/showthread.php?p=8342411#post8342411]("http://ubuntuforums.org/showthread.php?p=8342411#post8342411") seems to indicate that Adobe AIR 2.0 beta is working well on AMD 64-bit machines. 

Now to see if we can get tweetdeck working on AMD64.

---

