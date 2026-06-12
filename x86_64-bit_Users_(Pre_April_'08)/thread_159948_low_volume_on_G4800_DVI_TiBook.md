---
title: "low volume on G4/800 DVI TiBook"
date: 2006-04-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by davidmaxwaterman on 2006-04-13
Hi,

I've recently moved from OS X to Ubuntu on my Powerbook Titanium.

I've noticed that the sound output is 'bad'. The system occasionally makes 'noises' - loud blips and things, for example when I launch an application. These sound aweful - are they supposed to sound so distorted?

In any case, sound from other applications - realplayer, vlc and pretty much anything else - is really quiet. I can just hear the sound if I put my ear close to the computer.

Does anyone have any idea what the problem could be?

Max.

---

### Post by slux on 2006-04-14
Check out your mixer settings, there might be a "gain" or similar slider that is set low. The GNOME mixer might not show you the slider at first, look for the option in the mixer menu to select which sliders are shown (sorry, can't recall what it's called right now). As for the sounds, yeah they're supposedly (bongo) drums or something. :P

---

### Post by davidmaxwaterman on 2006-04-14
Yeah! This worked! Thanks!

To make it a little more straightforward for any further readers, I've added some comments below.

[QUOTE=slux]Check out your mixer settings,[/QUOTE]

It is 'Volume Control' on the 'Applications/Sound & Video' menu.

[QUOTE=slux]there might be a "gain" or similar slider that is set low. The GNOME mixer might not show you the slider at first, look for the option in the mixer menu to select which sliders are shown (sorry, can't recall what it's called right now).[/QUOTE]

Indeed, the sliders in question are called 'DRC Range' and are not shown by default. In the 'Edit/Preferences', there are two check boxes, one called 'DRC' and another called 'DRC Range' - (predictably) it's the box next to the latter you want to 'check'. I'm not sure what 'DRC' means, nor the difference between 'DRC' and 'DRC Range'. I checked everything, but it seemed like 'DRC' didn't make any difference to anything.

[QUOTE=slux]As for the sounds, yeah they're supposedly (bongo) drums or something. :P[/QUOTE]

Hrm. It sounds pretty aweful, IMO.

My music, though, sounds good now :D

Max.

---

