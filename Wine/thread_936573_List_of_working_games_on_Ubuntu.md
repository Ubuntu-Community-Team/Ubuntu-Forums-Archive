---
title: "List of working games on Ubuntu?"
date: 2008-10-02
forum: Wine
---

### Post by askyourpc.com on 2008-10-02
Does anyone know a list of working games for Ubuntu? Is there a website that shows the compatibility status of popular windows games?

---

### Post by binbash on 2008-10-03
[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by au_vagabond on 2008-10-03
I can successfully play (ie. at a level equivalent to that of windows)

 - Spore
 - TF2
 - CSS *hi fives wine developers*
 - Portal
etc.

It takes a bit of fiddling sometimes, but these days it is really easy. If you want to play steam games (like me), i would suggest doing the following.

1. Copy everything from your steam folder (EXCEPT steamapps) to your wine c drive (eg. /home/user/.wine/program files/steam/). 
2. Make a symbolic link to steam apps (sudo ln -s "/home/user/.wine/program files/steam/steamapps" "/path/to/steam/steamapps")
3. Open steam from the folder in the wine directory.
viola.

Also make sure you install decent drivers (ie. using envy or the drivers avail. at the manufacturer's website).

Anyhoo, good luck. I realise I just rambled off on a tangent, but meh.

---

