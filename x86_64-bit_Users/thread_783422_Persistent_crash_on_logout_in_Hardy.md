---
title: "Persistent crash on logout in Hardy"
date: 2008-05-05
forum: x86 64-bit Users
---

### Post by joehill on 2008-05-05
I have a real problem: I convinced a friend of mine to let me replace Windows on her machine with Ubuntu, but now every time you log out of this system, the whole system crashes.  That is, X stops, you see the startup text on TTY8 for a split second, then instead of starting a new X session the screen goes black and nothing works, although the fan keeps going.

I would say it's a problem with X, except nothing works, even over the network.  It's a new Dell with an Intel Core Duo and an Intel graphics card, very nice system that should easily run Ubuntu and ran Windows with no problem.

Any ideas on how to prevent this from happening?  I saw a couple threads here on the topic that have been closed but don't seem to have been resolved.

I'd be very grateful if anyone had suggestions!

Joe

---

### Post by pixel :-) on 2008-05-05
I have this to.CTRL+ALT+DEL still works,it does a clean shutdown,try avoiding hard shutdowns.

The solution is to change something in the xorg.conf file.Post your xorg.conf file, and wait for a xorg gurru to help.

---

### Post by joehill on 2008-05-06
Thanks for the reply.  Below is my xorg.conf.  I've tried dpkg-reconfigure several times but nothing changes.  If someone can help me get this solved I'll be very grateful!

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

---

### Post by ene_dene on 2008-05-26
I have the same problem on my laptop.

---

### Post by pixel :-) on 2008-05-26
If you have ati card,try this fix [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/118605/comments/32]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/118605/comments/32")

If this doesn't help.As interim solution try installing an other login manager.kdm(kde) or gdm(gnome) or xdm(xfce).

---

### Post by ene_dene on 2008-05-26
Unfortunately it doesn't work, I don't have KDE. Hardy is quite bugy compared to Gutsy, at least in mine case.

---

### Post by pixel :-) on 2008-05-26
So you have fglrx(ati card)?
By the bug report it strongly imply that you have to corect this line
> GDM_AUTH_FILE=/var/lib/gdm/$1.Xauth

check if "/var/lib/gdm" contains something

as an interim install kdm
sudo apt-get install kdm
and do the fix

you can try xdm,but it's really minimal

---

### Post by joehill on 2008-05-30
Thanks everyone for your comments.  Unfortunately, my friend has decided to put Windows back on this machine (but I'll probably put Ubuntu on another of her machines soon) so I won't be able to see how this problem gets resolved, but best of luck to everyone else having this problem.

---

### Post by Solomoriah on 2008-07-27
I'm experiencing the same bug.  Intel Core2 Quad, Intel DP35DPM mainboard, Diamond video with Radeon chip (I've mislaid the box so I can't tell you which, but it's one of the lower-priced units), running Ubuntu Hardy.

With fglrx installed, I can only get, at most, two users logged in using the switcher; and if either of them logs out, the screen might go black and the system become unresponsive, or alternately the login manager screen might appear but not work correctly (messed up keyboard focus and no mouse).

I uninstalled fglrx and got the standard xorg ati xserver working, and the problem is pretty much the same.  However, now I can get more than two users logged in via the switcher.

I enabled the hardy-proposed repo and installed the updated fglrx package, but the problem did not change.

---

### Post by Solomoriah on 2008-07-27
Here's an update:  I've logged in and out several times, without using the switch users functionality, and had no problem.  Still running the open source ATI driver and no Compiz.  I've tried all three user accounts on my system, but just one at a time, and things work fine.

HOWEVER... I then used "switch user" to log in all three users; when I tried to return to a logged-in user, I got the black screen.  I tried to ssh in from another computer but got no response.  Pressing and releasing the power button (and waiting several minutes) got me no response... I had to hold the power button to get it turned off.

In the past several days, I've tried about everything I can think of.  I've disabled the audio chip in CMOS setup, because someone said that might be the trouble; I've removed Compiz, with no effect.  I tried the "hardy-proposed" upgrade to the fglrx driver, and I've switched back to the open source ATI driver.  Nothing fixes this problem.

This bug:

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/86615](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/86615)

(originally for Feisty) seems to describe the problem I'm having.  My last test was to use the "ForceEnablePipeA" option described in the bug comments; it didn't help either.

---

### Post by Ken4000 on 2008-09-07
Hi i have the same problem. When I logout I get a black screen. My computer is a Dell Inspiron 8600 1.7GHz with a Ati Radeon 9600 Turbo Pro graphic card. I'm running Ubuntu 8.04 with Gnome.
I'm following this thread: [http://ubuntuforums.org/showthread.php?t=907307&highlight=logout+black+screen](http://ubuntuforums.org/showthread.php?t=907307&highlight=logout+black+screen)

Best regards
Kenneth

---

