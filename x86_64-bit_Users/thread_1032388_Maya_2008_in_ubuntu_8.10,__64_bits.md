---
title: "Maya 2008 in ubuntu 8.10,  64 bits"
date: 2009-01-06
forum: x86 64-bit Users
---

### Post by bangee on 2009-01-06
I've been searching about this and i havn't found anything about it:

I've successfully installed Maya 2008 in my ubuntu (it's my first time) and my sourprise becames when i run the program... the active screen appears like [[COLOR="Blue"]this[/COLOR]]("http://img145.imageshack.us/img145/2082/pantallazodh1.png")

When i move through that active view, i can see everithing clean, without any problem, but... when i click to a menu, [[COLOR="Blue"]the problem appears again[/COLOR]]("http://img142.imageshack.us/img142/2149/pantallazo1oy4.png")... >.<

I've got an Ati X800 Xl and, with synaptic, i've installed the ati catalyst through the fglrx-amdcccle library.

I wish somebody could help me, i'm a new ubuntu user and i would like to start working ubuntu instead windows

Thx so much for everything ^^

---

### Post by bangee on 2009-01-07
Nobody? T.T

---

### Post by endymon on 2009-01-07
Hi,
this could easily be more of a Maya issue than Ubuntu.

Have you played with the viewport settings ? Have you disabled hardware shaders / lights, etc ? Are you viewing Mental Ray shaders ? etc

Does it get screwed up if you're only showing wireframe ?

I know for a fact that certain ATI cards have issues with advanced lightning enabled in the viewport.

---

### Post by bangee on 2009-01-07
excuse my noobs questions but.. 
[LIST]
[*]how can i play it with the viewport settings?
[*]where do i can disable hardware lights? and how to do for viewing mental ray shaders?
[/LIST]
through the option display->object display-> i've selected ignore hardware shader but.. the problem still continues T.T

when i push "4" buttom for seeing wireframe mode, the problem still remains here, i have disabled every visual effect from my desktop (throught system, preferences, Appearance, visual effects) and... nothing >.<

thank you very much!!!

---

### Post by bangee on 2009-01-08
:o

---

### Post by bangee on 2009-01-12
Please, somebody T.T

---

### Post by Kilz on 2009-01-12
Just one question. Do you have desktop effects enabled?

---

### Post by briandu on 2009-01-12
Bangee,

maybe u need to tell us about your hardware config, s/w versions etc. in your post.

The treatment of Nvisia vs ATi is different.

Can u do that?

---

### Post by bangee on 2009-01-12
Kilz i've got all desktop effects disabled

Briandu later i'll make another post telling all my ati catalyst config for my Ati X800xl, now i gotta go

what do you mean with "s/w versions etc"?

Thanks for everything!

---

### Post by skullmunky on 2009-01-13
Kilz is correct, you have to have the desktop effects DISABLED.  Turn all of them off.  The way that they use opengl acceleration on the graphics card conflicts with Maya, which causes that exact problem.  Symptoms include noise like that in different viewports or the timeline, icons in the shelf not drawing right, material samples in hypershade or material attribute tab not drawing right, freezes when you use the hotbox menus, and other nastiness.

If you read the Autodesk info for linux, or do a little searching for "ubuntu + maya" or "linux + maya" you'll also find instructions on disabling the Composite extension.  (that's the thing which allows the desktop effects).  Often, just disabling the desktop effects will do the trick.

---

### Post by Arijan on 2009-03-22
The composite extension has to be off - I searched for the possible solution - no luck. It simply has to be off - so if U want to use Maya U can forget about the eye candy Linux. The same thing is with Nuke on Linux which also requires composite off. 
The other things which annoyed me are: the behavior of cursor (becomes a big X every time I click the right button), sometimes Maya freezes when using the hotbox and the interface is ugly (more like the old Irix thing). So i finally found the solution for those things - here's the link, I hope U won't have those problems any more:

[http://ilbozo.wordpress.com/2008/04/28/6/](http://ilbozo.wordpress.com/2008/04/28/6/)

Cheers

---

### Post by peterguirguis on 2009-05-29
have you found a solution to this proplem???
if not...
start maya using this command

XLIB_SKIP_ARGB_VISUALS=1 maya

and hopefully it'll do the job.

---

