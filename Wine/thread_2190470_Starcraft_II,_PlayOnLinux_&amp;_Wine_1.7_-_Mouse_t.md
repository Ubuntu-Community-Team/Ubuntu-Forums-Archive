---
title: "Starcraft II, PlayOnLinux &amp; Wine 1.7 - Mouse troubles"
date: 2013-11-27
forum: Wine
---

### Post by jcllings on 2013-11-27
So I've got Starcraft installed and it works pretty good but not yet good enough.  Starcraft is a game where the mouse comes in to play a lot.  What I am seeing is that during heavy engagement, i.e. lots of units maneuvering and attacking / defending it' becomes impossible to select units by click-drag or sometimes ctrl-click. That is the kind of thing that will make a player crazy. 

So... what tips has the community got for me? Machine is pretty spiffy so I seriously doubt its resources.  Has an nVidia card + SSD + Maxed memory, Core i7 above 4 ghz.

---

### Post by DanglingPointer on 2013-11-28
Have you tried a different mouse?  Different brand, make and type?  Borrow one from someone and give it a shot.  Or try a top of the range mouse like from Razer or similar.

---

### Post by jcllings on 2013-11-29
Hmmm... is there any precendent for issues with keyboard / mouse? My keyboard is a Logitech G510 Gaming / Macro keyboard which isn't very well supported. g15tools package has been broken for quite some time.  Mouse looks like a half way decent Logitech but it's not a gaming mouse. I suppose it's worth a try. I have others around but after bying this expensive keyboard and discovering I wasn't allowed to use it, from that point forward I decided I wouldn't buy any more of that stuff.

---

### Post by jcllings on 2013-11-29
You might be on to something the more I think about it. That machine was the server but I was using synergy, for example. I'll do some checking this weekend.

---

### Post by jcllings on 2013-11-30
OK so what I did was, I changed the mouse to a USB 3.0 port and killed the synergy daemon. This seems to have done the trick!

---

