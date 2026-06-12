---
title: "wine help needed"
date: 2009-06-15
forum: x86 64-bit Users
---

### Post by asvestomix on 2009-06-15
Hello,
well i install wine stepbystep as i fount here [http://www.winehq.org/download/deb]("http://www.winehq.org/download/deb")
but now i want to run a game  "warcraft 3" 
i have the dics in an ntfs partition as iso but i dont know what to do to install the game
i am using ubuntu 64 the latest version

---

### Post by pixel :-) on 2009-06-16
you have to mount the .iso

try this [http://www.acetoneteam.org/](http://www.acetoneteam.org/)

then

menu > wine > configure wine

if you can find it in a terminal

winecfg

in tab "drives"

add the folder where you mounted the iso

in show advanced select type as CDROM

click OK

follow other instructions at

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=897](http://appdb.winehq.org/objectManager.php?sClass=application&iId=897)

---

### Post by asvestomix on 2009-06-16
Thnx you i will try it to morrow i am to busy today

---

### Post by asvestomix on 2009-06-17
i mount the disc but where i can find the virtual cdrom from wine?

---

### Post by asvestomix on 2009-06-17
ok i set it up but it is unable to join in batlenet
also how i can play full size? it runs wndowed and i cant see the whole screen

---

### Post by markharding557 on 2009-06-17
gmountiso is agood simple app for mounting iso

---

### Post by asvestomix on 2009-06-17
nice app

---

### Post by Stunts on 2009-06-18
> **asvestomix said:**
> ok i set it up but it is unable to join in batlenet
also how i can play full size? it runs wndowed and i cant see the whole screen

In order to play warcraft 3 in fullscreen you should disable you desktop effects (assuming you have disabled the option to enable a virtual desktop on the wine configuration).
To do that just press Alt+F2 and type ```
metacity --replace
``` without the quotes. This will disable compiz and replace it with gnome's regular window manager, metacity.

As for battle.net I assume you are experiencion a bug from the lates warcraft patch with the new battle.net banners.
In order to make it work using ArchLinux 64 I had to install a package called lib32-libgnutls. I'm not sure there is a similar one for ubuntu. Try searching for gnutls in synaptics.

Good luck!

---

