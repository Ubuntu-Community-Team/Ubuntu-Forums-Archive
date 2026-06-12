---
title: "Ubuntu is really slow on my iMac"
date: 2005-11-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by shubox357 on 2005-11-22
I have a g3 iMac (600mhz, 256mgb RAM) and i just installed ubuntu, I got rid of OSX completely. The only problem is when I log in everything loads at sucha  slow rate and the mouse onyl moves only every once ina  while. Its not fast enough to do anything and I'm sad. Anyone know what i can do to speed it up a LOT? without having to buy more RAM....?

---

### Post by darknuala on 2005-11-22
The only fix I have had for a similar problem was to use a low resource window manager like fvwm or xfce or blackbox.  

That's helped a whole lot for me.

---

### Post by ssam on 2005-11-22
it should not be that slow.

if a lightweigth window manager (eg xfce, openbox, fluxbox) helps then that implies that more ram would help.

i'd suspect that maybe you have a problem with graphics drivers.

---

### Post by darknuala on 2005-11-23
I upgraded the ram to 192 mb and it has helped some.  The video driver on this is crappy.  Tuxracer is not only unplayable, but once you fire it up, its almost impossible to move the cursor to exit the program.  And with it being an imac with onboard video, i don't see it possible to alleviate the problem.

---

### Post by rquint on 2005-11-23
Try editing /etc/X11/xorg.conf to NOT load the dri module--just put a hash mark (#) at the start of the line reading load dri.  That may help.  You lose acceleration but you probably aren't going to run anything that needs speed on a G3.

---

### Post by linear on 2005-11-23
It looks like (at least with the LiveCD) disabling either dri or glx (or both!) will work. (Or, as someone suggested elsewhere, limiting the color depth to 15.)

Could someone explain what glx and dri do?

---

### Post by spade_shark on 2005-11-24
Shubox357, you have enough horse power and memory!  Ofcourse more ram can never hurt, but it is not the issue.  Perhapse video driver / glx modules issues.  Rquint, what was your fix if any on this thread ?  
[http://www.ubuntuforums.org/showthread.php?t=82866&highlight=ppc+slow+video]("http://www.ubuntuforums.org/showthread.php?t=82866&highlight=ppc+slow+video").

GLX provides the glue connecting OpenGL and the X Window System.  It is required by any OpenGL implementation using X.  DMI is direct rendering.  All for graphics acceleration / 3D.  Just video enhancements, if you will.  And nice enhancements too, when it works.  

Darknuala, what do you get from a "glxinfo" command?  I would assume ..."GLX missing"... and "direct render = no".  Tuxracer is all about these modules being loaded and working.  Try a "glxgears" command.  I am certain just a tweak of drivers /modules will get it moving.  Lets make sure your ATI drivers are correct before we jump into the glx and dmi modules.;)  Should be able to "turn off" glx and dmi and get normal login and menu response.

Appears to be a number of people with the same similar issues.  Anyone have success with the G3 models and Breezy?  I have a G4 using ATI rage 128 Pro 16mb with breezy and do not have sluggish response for general use.  I am planning on tuning the graphics very soon and will post my results.

---

### Post by shubox357 on 2005-11-24
i changed teh graphics card driver i think to r128 and changed the clock and now its awesome. thanks guys

---

