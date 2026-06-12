---
title: "Will Wine run Photoshop 5.0?"
date: 2014-03-19
forum: Wine
---

### Post by riverguy99 on 2014-03-19
Will Wine run Photoshop 5.0?  I've been trying to get Wine configured on my 12.04 laptop and have been so far unsuccessful.  So the only reason I'm going through this is because I need to be able to run Photoshop 5.0.  Gimp is great but it's a real challenge to work CMYK graphics with it, and that's what I need PS for.

Anybody have any success with this? I've found lots of comments and posts on using CS2, but I have and need to be able to run good old (and I mean OLD) PS 5.0.

---

### Post by PotatoHead007 on 2014-03-20
Have you tried PlayonLinux? They can do PS4, maybe try using that install for PS5.
To install POL: 
```

wget -q "http://deb.playonlinux.com/public.gpg" -O - | sudo apt-key add -
sudo wget http://deb.playonlinux.com/playonlinux_maverick.list -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get install playonlinux

```
This will add the PlayOnLinux respiratory and get the newest version.

---

### Post by mastablasta on 2014-03-20
as you can see here CS5 has reported gold rating, but only with certain version/distro combo [https://appdb.winehq.org/objectManager.php?sClass=version&iId=20158](https://appdb.winehq.org/objectManager.php?sClass=version&iId=20158)

eventhough last rating is garbage.

playonlinux is just a GUI forntend for wine. but there are some scripts included to help install certian programs. i would hold my breath but you oculd try with the tested distro/wine version

if you mean version 5 (it has silver rating), while version 7 has platinum: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=17](http://appdb.winehq.org/objectManager.php?sClass=application&iId=17)

---

