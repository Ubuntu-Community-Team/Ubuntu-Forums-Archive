---
title: "can't login..."
date: 2006-05-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by davidmaxwaterman on 2006-05-17
Hi,

I can't seem to log in via X (Gnome), but I can log in using an crtl-alt-f1 terminal.

I can't figure out why X won't start. I haven't changed anything to do with that - the only thing I've been messing with is the network config. ...

I couldn't login in at a hotel while I was on a trip, but it worked fine when I brought it back home. I figured it was something to do with the network configuration, so I unconfigured all network devices, intending to only enable and configure devices I knew would work after I had logged in. It seemed to work, but now I can't log in again.

I get the sound as it starts up, but no series of icons as it gradually starts.
I tried the other options for logging in, including the failsafe one, but the same thing happens.

I also tried killing gdm from the terminal, and then running 'startx', but same (though I get the traditional X background). The messages stop after a series of :

"(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialise Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
"

then

Warning: font renderer for "pcf" already registered at priority 0
...and several similar lines

I had been messing with the X config trying to get the SVideo port to work, but it hadn't broken anything at the time, and it's worked since then too. I've tried to remove the relevant lines, but it doesn't fix it...

Can anyone help?

Max.

TiBook G4/800/DVI

---

### Post by linear on 2006-05-17
You could try **sudo dpkg-reconfigure xserver-xorg**, to start fresh.

---

### Post by aimislame15 on 2006-05-17
The problem is just logging in at all isnt it? Maybe try a recovery from the cd?

---

### Post by davidmaxwaterman on 2006-05-18
[QUOTE=linear]You could try **sudo dpkg-reconfigure xserver-xorg**, to start fresh.[/QUOTE]

OK. I've now tried that, but it didn't make any difference, which, I suppose, rules out the x server config.

Thinking about the most recent time it worked...it was when I was transferring files off a usb camera. It worked just fine. I think I just put it to sleep by closing it.

Any other ideas?

Max.

---

### Post by davidmaxwaterman on 2006-05-18
[QUOTE=aimislame15]The problem is just logging in at all isnt it? Maybe try a recovery from the cd?[/QUOTE]

Well, logging in via X. I can log in using the text console/terminal/whatever it's called, without any problems.

Max.

---

### Post by ssam on 2006-05-18
maybe wiki.ubuntu.com/UbuntuDateBug

---

### Post by davidmaxwaterman on 2006-05-18
[QUOTE=ssam]maybe wiki.ubuntu.com/UbuntuDateBug[/QUOTE]

Yup! That fixed it. Thanks!

Max.

---

