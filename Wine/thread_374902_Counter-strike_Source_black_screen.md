---
title: "Counter-strike Source black screen?"
date: 2007-03-03
forum: Wine
---

### Post by nolongerlivecd on 2007-03-03
Hi all, I just installed Counter-strike Source, but I get a black screen when I attempt to start up Counter-strike Source. The splash screen loads up fine, but after that, where I am supposed to see the menu, I get the black screen.

Here's the results when running in terminal:

[http://paste.ubuntu-nl.org/8349/](http://paste.ubuntu-nl.org/8349/)

Can anybody help me make any sense out of it?

---

### Post by bastiegast on 2007-03-03
Known issue with wine 0.9.31. 0.9.32 fixes this, it was released yesterday and the ubuntu package can hit the repo's any moment. If you can't wait, downgrade to 0.9.29. (Uninstall wine then download a deb from [here]("http://wine.budgetdedicated.com/archive/index.html"))

---

### Post by nolongerlivecd on 2007-03-03
> **bastiegast said:**
> Known issue with wine 0.9.31. 0.9.32 fixes this, it was released yesterday and the ubuntu package can hit the repo's any moment. If you can't wait, downgrade to 0.9.29. (Uninstall wine then download a deb from [here]("http://wine.budgetdedicated.com/archive/index.html"))

Oh, ok. Thank you. I'll wait for the update and see how things work out.

---

### Post by nolongerlivecd on 2007-03-04
I'm still getting a black screen even after the update.

*EDIT* Works if I downshift to dxlevel 70

---

### Post by Jarn on 2007-03-04
I get this problem, too. Wine version 0.9.32. With dxlevel 70 and dxlevel 80.

EDIT: Ah, mine was from having UseGLSL enabled in Wine's registry. When I disabled that, CS:S works.

---

### Post by nolongerlivecd on 2007-03-04
I get:

Material "debug/debuglightmap":
   No render states in shader "LightmappedGeneric_DX8"
Material "debug/debuglightmapzbuffer":
   No render states in shader "LightmappedGeneric_DX8"

When I try without GLSL and try "mat_dxlevel 90". It still displays a blackscreen, and I have to change it to dxlevel 70 again before I can view the above output within the console.

With GLSL, there is no text output, just the blank screen.

---

### Post by Pugwash on 2007-03-04
I'm having the exact same problem. So running Css in dx7 solves the problem?

Edit - Yes, it works fine for me in dx7 :)

---

### Post by nolongerlivecd on 2007-03-05
Running it in DX7 solves the problem, but my graphics card is a native DX9, and I heard that running it on DX9 would be faster...

---

### Post by w116tjb on 2007-07-25
How do you downgrade your dxlevel?

---

### Post by ARTO^UK on 2007-07-25
-dxlevel 70 on the on launch line.

---

### Post by w116tjb on 2007-07-25
Following these directions, I got Source to work, but now my keyboard stops working in game. The mouse works fine. I was able to CTRL+ALT+BACKSPACE to restart X. Any ideas?

---

### Post by n1ght28 on 2008-04-08
> **ARTO^UK said:**
> -dxlevel 70 on the on launch line.

can ou elaberate please, i'm a newbie, which command line and where,

---

### Post by nolongerlivecd on 2008-04-25
> **n1ght28 said:**
> can ou elaberate please, i'm a newbie, which command line and where,

Right-click launcher, click on properties. Then click on "Launcher", and add the command at the end of the "Command" text box.

---

### Post by Spekke on 2008-10-16
this has being usefull to me, I had same error, changing the dxlevel to 70 worked, 
but now I wonder, 
when I play the game everything is more in "pixels" and the game runs with some low fps (I think it's not lag) anyone who knows if you can change that? 
(I could run it smoothly when I used windows xp)

thanks

edit: it's not lag, I play the game at +- 22 fps

---

