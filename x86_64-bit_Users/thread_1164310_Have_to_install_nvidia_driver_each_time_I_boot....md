---
title: "Have to install nvidia driver each time I boot...?"
date: 2009-05-19
forum: x86 64-bit Users
---

### Post by noblerabbit on 2009-05-19
Well I gave up on the wireless problems in jaunty (and ibex) and went back to hardy, where my wireless works fine.

However I am having X problems. I go through the proper steps to install the driver for my card. i get the pkg from nvidia site, then stop X with
```

sudo /etc/init.d/gdm stop

```then chmod +x to the pkg, and run it with
```

sudo sh NVIDIA...etc etc

```Installation goes fine, i say no to the 32bit OPENGL stuff because i have x64 obviously.

Upon restarting gdm everything seems fine (the first good sign is the annoying GPU fan finally stops) then i get the NVIDIA screen, and a correct resolution login screen.

Everything would appear it is as it should be, but as soon as i try to restart it cant load X (Ubuntu is running in low graphics mode... cannot determine screen video card etc, dont rememebr exactly what it says).

So I am having to do the above steps again, overwriting the previous driver and the xorg.conf file. I had a look at the file but I cant make much of it.

Does anyone know why this could be happening? I mean i load X fine the first time, so why should it be any different when i reboot?..

---

### Post by dabl on 2009-05-19
Are you using the "...pkg2" package, for 64-bit arch?

YES, you _do_ want the 32-bit Open GL libraries, too.

This "how-to" is slightly dated, in the driver version, but still accurate on the procedure:

[http://kubuntuforums.net/forums/index.php?topic=3100807.msg164892#msg164892](http://kubuntuforums.net/forums/index.php?topic=3100807.msg164892#msg164892)

Substitute gdm for kdm, and you should be good to go with Ubuntu.

---

### Post by noblerabbit on 2009-05-19
hmm..

i tried WITH the 32bit stuff as well, and gdm wouldnt even load immediately after installing the driver.

it was only when i said no to the 32bit that i was able to load gdm after installing, but as i said, not after rebooting again.


i will have a look at the guide, thanks for the quick reply :)

---

### Post by dabl on 2009-05-19
Make sure you do the ```
sudo /etc/init.d/gdm stop
``` part of it -- that could be your issue.

---

### Post by noblerabbit on 2009-05-19
AHA!! :D:D:D

you, sir, are a genius!


that did it! im guessing what made the difference was the pkg2 in the tmp directory instead of the desktop?

well at any rate, it worked after rebooting, so thanks so much for your help! ):P

---

### Post by dabl on 2009-05-20
> **noblerabbit said:**
> AHA!! :D:D:D

you, sir, are a genius!



:cool:

I love it when a plan comes together ....  :)

---

