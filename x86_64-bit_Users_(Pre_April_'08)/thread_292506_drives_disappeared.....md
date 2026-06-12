---
title: "drives disappeared...."
date: 2006-11-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by weird_c00kie on 2006-11-03
my sound went out again a short while ago and i was trying to fix it once again using the guide here:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

while going through the "Getting the ALSA drivers from a *fresh* kernel" bit, i entered
> sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
and it seemed to be going fine, until all of a sudden X quit and it took me to a full-screen terminal
when i rebooted the system and logged back in, i noticed that all my desktop items were gone and that i couldn't access my drives anymore.
i can't even open the terminal!
for some reason though, it still lets me open my browser and retains all its bookmarks....

i tried booting into Gnome Failsafe and that didn't really help. the drives were still gone
if i go to Disk manager, i can see them there, and it says they're mounted, but it won't let me browse them


does anyone have any ideas? i mean... i was planning on doing another clean install as soon as i finished uni, but i didn't think it'd all fall apart on me before i got to back up my data :(


when i go to the Places menu, my home directory, My Computer and Filesystem aren't there. if i try clicking on one of my other drives, it comes up with an error message saying 

> Could not open location 'file:///media/SharedFAT'
Details: There is no default action associated with this location.

if i try opening the terminal from the shortcut i put on my toolbar, it comes up with another error message saying
> Could not launch application
Details: Failed to execute child process "gnome-terminal" (No such file or directory)

after that, i noticed the terminal isn't even in the Accessories menu anymore.


can anyone help in any way?:-?

---

### Post by weird_c00kie on 2006-11-04
the issue gets weirder...
i just noticed that i actually can still access the drives through other applications. like, if i type **file://localhost/** into my browser, i can still see everything and access it, but i still can't get to it from the Places menu.

if no one replies with a solution i guess my only option will be to boot off the LiveCD, back my data up and format once again

---

### Post by weird_c00kie on 2006-11-04
any takers? yes? no? maybe? no?

---

### Post by weird_c00kie on 2006-11-04
i experienced a moment, just now, when intelligence and common sense descended upon me.

i checked the system monitor and realized that Nautiuls isn't actually running.
i guess now i just need to work out how to start it up again....


any ideas from anyone?

---

### Post by weird_c00kie on 2006-11-05
continuing my monologue in here, i managed to get my terminal back by reinstalling it through synaptic (after reading this thread: [https://launchpad.net/distros/ubuntu/+ticket/1956](https://launchpad.net/distros/ubuntu/+ticket/1956))

i was hoping that reloading nautilus would be as easy as entering "nautilus" into the terminal, but it's not :p

---

### Post by weird_c00kie on 2006-11-05
*dances around* 
WOOHOO! 
finally worked out what was wrong....

for some reason nautilus was uninstalled!
so i reinstalled it using synaptic and it's all back now :D

i still have no sound, but at least i'll have a chance to back all my stuff up now before reformatting and reinstalling :)

---

### Post by kuja on 2006-11-05
In that case, Nautilus probably depended on one of the packages you removed, always pay close attention to what things get removed when you remove packages.

---

### Post by weird_c00kie on 2006-11-05
kuja, nautilus was indeed one of the MANY things which depended on linux-sound-base
unfortunately, because i was removing them through the terminal, i didn't realise that. afterwards when i did it through synaptic, i noticed that these packages were also being removed:
> alsa-base, alsa-utils, compiz-gnome, gdm, gnome-applets, gnome-control-center, gnome-panel, gnome-session, gnome-terminal, nautilus AND ubuntu-deskto

when i tried removing linux-sound-base through synaptic or the gnome terminal though, it would always screw up before finishing... probably because the terminal itself and nautilus were being removed.
so i booted into ternimal mode and did the
> sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
thing, then used
> sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop gnome-terminal nautilus
to get it all back :D

so, nautilus is back, my terminal is back AND my sound is back :D


a good lesson learnt about dependencies hehe :)

---

