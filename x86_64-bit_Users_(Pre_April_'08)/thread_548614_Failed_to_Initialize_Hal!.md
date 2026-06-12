---
title: "Failed to Initialize Hal!"
date: 2007-09-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by lsweet on 2007-09-11
I'm a long-time Windows user and have been playing around with Ubuntu 32bit for sometime now.  Nothing fantastic, just the regular old stuff, getting used to the environment, etc.

As I consider myself an experienced computer user, my Linux experience is lacking, which is ultimately the reason I figured I'd give it a shot.  So I tried 32 bit 7.04 Feisty and have probably installed it going on ... ohhh... more times than I can count.  I'm a glutton for punishment, so don't ask.

Anyhoo -- during one of my re-install phases I figured I'd give 64 bit a shot since it would give me yet another 'new' environment while still allowing me to dabble a bit more.  I've tried 6.10, 7.04 and 7.10 tribe 5 -- all in 64 bit -- and all of them fail at allowing me to install as they would always boot to a black screen.  Through research, I learned of the alt cd's and text based installs.  I tried 7.04 and 6.10 through alt cd's and every time I do, I get 'Failed to initialize HAL!'.  Never did I see this with 32bit 7.04.

I'd really like to keep trying at the 64 bit versions.  I've read a lot of issues of other people getting this error and have compiled a list of their solutions so I could see if they're any help.

Presently -- I've got 6.10 installed, fresh, nothing more.  Just finished the install before I headed off to work today.  The only thing I've done to the install was made a copy of my xorg.conf, changed the NVIDIA driver to Vesa and launched GDM.

EDIT: It don't know if it really applies -- but I'm running an 8800 GTS which seems to have a hard time being installed on either 32 or 64 bit platforms.

Is it worth my while to keep plugging away at it, or should I bite the bullet and stick with 32?  I'd really rather that be my last recourse.

---

### Post by Cappy on 2007-09-11
When you boot up off the CD Hit F6 and add the word ```
nosplash
``` on the end.
If that doesn't work try adding ```
noapic nolapic nosplash
```
on the end instead.



8800 .. there are a bunch of threads on it. Not hard either thanks to a program called envy.

Here is the home page so you can read it first : [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

```

sudo apt-get --purge remove nvidia-glx* nvidia-settings linux-restricted-modules*
sudo apt-get install build-essential xserver-xorg-dev
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb
sudo dpkg -i envy*.deb
sudo envy -t
```

---

### Post by dabl on 2007-09-11
For [[COLOR="Lime"]**this user**[/COLOR]](http://ubuntuforums.org/showthread.php?t=23291) the HAL problem was caused by the CD ROM drive.  The fix is in the thread, if that's what the problem on your rig is.

The 8800 GTS card is supported by the -100.14.11 Nvidia driver (the newest), so you need to use that. I recommend the Envy script installer to set up the driver, which I BELIEVE is in the Feisty 64-bit repo. If not, it is available [[COLOR="Lime"]**here**[/COLOR]](http://albertomilone.com/nvidia_scripts1.html)

:)


OK, Cappy wins today's speed typing contest!  ;-)

---

### Post by lsweet on 2007-09-11
Oh; I've got the 8800 to install -- it just doesn't seem to be friendly regardless of the driver installed.

Sorry -- I wasn't clear when I wrote that.  I guess I was implying more that with some of the bugs I had read up on, if perhaps that card was perhaps causing the issue.  I'm still a little unclear as to what causes this error to help identify the resolution to the issue.

---

### Post by dabl on 2007-09-11
> **lsweet said:**
> 

 if perhaps that card was perhaps causing the issue.



That's not out of the realm of possibility -- if so, then getting the right driver installed might fix everything. :)

---

### Post by lsweet on 2007-09-11
I think last time I tried to run Envy -- it was missing some module that I couldn't find immediately in the repository -- off the top of my head, I can't think of what it may be.  This would have been an earlier install, not the present one.

EDIT:  Bah; I'm getting off topic ;)

---

### Post by dabl on 2007-09-11
> **lsweet said:**
> I think last time I tried to run Envy -- it was missing some module that I couldn't find immediately in the repository -- off the top of my head, I can't think of what it may be.  This would have been an earlier install, not the present one.

EDIT:  Bah; I'm getting off topic ;)

Envy used to give errors and make you install all of its dependent packages before it would install, but the newer version doesn't do that -- it pulls in its own dependencies for you.

You're only off topic if it turns out the HAL error is NOT referring to your video card!

:lolflag:

---

### Post by lsweet on 2007-09-11
Success!  ... for now.  Until I break it again.  I did two steps, so I really couldn't pin it on either one really.

1st - Updates all things Hal.
```

sudo apt-get install hal*

```

2nd - Apparently changes the boot order?:
```

sudo rm /etc/rc2.d/S20dbus

cd /etc/rc2.d/
ln -s ../init.d/dbus S12dbus

```

That seems to have done the trick.  Envy doesn't want to install now mind you, still giving me that module dependency issue.  I've used it a number of times before with no issue.  These last few attempts have been upsetting!!

---

