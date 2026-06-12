---
title: "games crashing"
date: 2008-08-29
forum: Wine
---

### Post by Codemastadink on 2008-08-29
Plz read all. I have tried things and updated with results

So i have installed a few games using Wine. Starcraft and WarCraft3. Starcraft launches fine, but when i start WC3 the screen goes black, like its loading, but nothing ever happens. It doesn't lock up the computer, i can still use different workspaces, but that one workspace is just black.

Anyone had this problem before? or would know how to fix it?

EDIT:The sound works, and i know the game is running, but it is just not displayed.

EDIT: I looked on winehq.com and it said that effects programs like compiz may mess with it. Would there be a way to turn compiz on and off? but keep the same settings? so when i play i can keep it off, but when i surf the web and do whatever else i can turn it back on?

EDIT: turned off Compiz, that is not the problem. I put the game in a window instead of full screen. Now it plays the opening cinematics, but when i click or hit esc to get past that part, it then freezes.

---

### Post by Codemastadink on 2008-08-29
Can anyone help?

---

### Post by sidewinder46 on 2008-08-29
Try to load using```

wine <program> -opengl

```
if this doesnt help try, [here]("http://ubuntuforums.org/showthread.php?t=45407")

---

### Post by Codemastadink on 2008-08-29
Anyone?

---

### Post by Tzimisce on 2008-08-29
Urk I trolled before I posted, sorry. 

You could set Compiz to a profile that leaves the desktop without any effects while you run the game if you believe it is Compiz related. Also in my experience with Wine it is just unreliable. Finally, reading appdb myself it caught my eye that Warcraft 3 apparently played better on older versions of wine.

---

### Post by Codemastadink on 2008-08-29
> **Tzimisce said:**
> Urk I trolled before I posted, sorry. 

You could set Compiz to a profile that leaves the desktop without any effects while you run the game if you believe it is Compiz related. Also in my experience with Wine it is just unreliable. Finally, reading appdb myself it caught my eye that Warcraft 3 apparently played better on older versions of wine.

how would i create the 2 profiles?

---

### Post by Codemastadink on 2008-08-29
bump

---

### Post by aoanla on 2008-08-30
If you're just using the default compiz, then setting Desktop Effects to None turns off compiz.

Otherwise, in a terminal:

metacity --replace &

should remove compiz, and

compiz --replace &

should bring it back again (probably with the same settings it had).

I should note that this only took one forum search to find.

---

### Post by Codemastadink on 2008-08-30
> **aoanla said:**
> If you're just using the default compiz, then setting Desktop Effects to None turns off compiz.

Otherwise, in a terminal:

metacity --replace &

should remove compiz, and

compiz --replace &

should bring it back again (probably with the same settings it had).

I should note that this only took one forum search to find.

Well, i did that, but it didnt help any :/

---

