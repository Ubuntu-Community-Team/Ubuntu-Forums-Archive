---
title: "Force a Wine Virtual Desktop Size?"
date: 2012-03-03
forum: Wine
---

### Post by etienne@Rofti on 2012-03-03
Hi there!

I recently downloaded an old game, Dune 2000, that I used to play when I was a kid off Abandonia.com and tried to play it in Wine. The mouse sometimes gets tricky when scrolling around the map, so the workaround that I employ is to run it in a virtual desktop, as suggested by heading 7.8 on the Wine FAQ's : [http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ)

However, the game runs at a resolution of 640x480, which is way too small for my modern screen. I would like to run it at 800x600 or 1024x768, but I am unable to force that size. It always resizes the virtual desktop to 640x480 as soon as the game loads.

Is there any way to work around this behaviour and/or force another desktop size? The game offers no screen size option.

Thanks!

---

### Post by Toz on 2012-03-03
I had a look at this a while back and based on this [_link_]("http://tfischernet.wordpress.com/2009/02/14/enlarge-fullscreen-programs-in-wine/"), came pretty close.

1. Install necessary components:
```
sudo apt-get install xserver-xephyr x11vnc xtightvncviewer
```

2. Start a nested X session:
```
Xephyr :5 -ac -screen 640x480 &
```

3. Start the wine app in the nested x session:
```
DISPLAY=:5 wine DUNE2000.EXE &
```
...then minimize the Xephyr window (better performance if there aren't 2 seperate screen redraws happening).

4. Start the X11vnc server and attach it to the correct display:
```
x11vnc -nocursor -localhost -scale 2:nb -display :5 &
```
...(note the scaling parameter - scale to twice its size)

5. Connect using a vncviewer:
```
xtightvncviewer -compresslevel 0 -nojpeg localhost
```

Viola! The only issue I had was somewhat sluggish performance as compared to a regular wine run.

---

### Post by etienne@Rofti on 2012-03-05
Thank you so much, Toz.

I'm struggling a little bit, being a bit of a n00b. But I figure with some trial and error I'll eventually get there.

Hopefully one day there is a simple fix in WineCFG.

---

