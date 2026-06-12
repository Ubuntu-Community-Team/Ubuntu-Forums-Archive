---
title: "what is X smokin'?"
date: 2006-03-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by DarBarf on 2006-03-04
so.. i'm having this problem.. (yes another one hehe). X seems to be really slow, and kde sometimes crashes when i'm not even really taxing it that much..
when i resize windows there's a trace of where the window used to be.. like in this picture:

[IMG]http://i8.photobucket.com/albums/a25/DarBar/snapshot2.jpg[/IMG]

i'm using ksmoothdock and gkrellm (obviously), on KDE version 3.4.3.

would upgrading kde solve this weird lagging problem.. when i was runnign kde 3.4.2 on mandriva i never had this problem... 

i'm also using a Gigabyte K8 Triton MOBO
                       AMD Sempron64 1.8GHz 3000+ proccessor
                       1024MB RAM
                        Nvidia GeForce4 DDR AGPvideo card
                        Antec TruePower2.0 430W Power Supply
if any of that helps :P

any suggestions would be greatly appreciated
;)

---

### Post by DarBarf on 2006-03-04
and you can see from the very low levels on GKrellm that my system was fairly idle when i changed the size of that Opera window...

it's probably something very simple, but i figure it never hurts to ask stupid questions.. because you know someone wants to ask the same one..
ha!

---

### Post by dresnu on 2006-03-04
Wow! Nice effect, you can suggest it to those xgl guys :cool: . I'm sorry, just joking :mrgreen: .

---

### Post by DarBarf on 2006-03-04
hehe :-P

---

### Post by nrwilk on 2006-03-04
Have you tried adding this line to your xorg.conf under the device section?

```
Option "RenderAccel" "True"
```

This helped me out a bunch with the slowness when dragging a bounding box around icons on the desktop, but it also helps with that chunky window-redraw wierdness.

---

### Post by DarBarf on 2006-03-04
i'll give it a shot.

---

### Post by nrwilk on 2006-03-04
I forgot to mention you'll need to restart the xserver after you save the file.

<ctrl><alt><backspace>

---

### Post by DarBarf on 2006-03-04
unfortunately, adding that line to xorg.conf, and restarting X didn't help..
well.. things are a little less choppy than before, so thanx for that.. i suppose it wasn't that choppy before, but it's a little faster it seems.

---

### Post by nrwilk on 2006-03-04
Too bad it didn't clear it all the way up.  Sorry about that!

I was hoping it would be a really easy fix like that.

Wish I could help further!

---

### Post by pelle.k on 2006-03-04
> Option "RenderAccel" "True" I'm pretty sure this option is nvidia specific...

if you're using ATI i think you should be using> Option "AccelMethod" "EXA"

Correct me if i'm wrong.
On the other hand, this is probably not going to work if you're not using ati firegl, or nvidia glx driver.

[edit]post the result of "glxgears -printfps"[/edit]

---

### Post by dresnu on 2006-03-04
I read somewhere else that the renderaccel option works only with nvidias, but I have an ati and I can see the difference too. 
About the accelmethod, if I'm not wrong it is enabled only in Xorg 7 so if you have a basic breezy installation this option is useless.

---

### Post by nrwilk on 2006-03-04
[QUOTE=pelle.k]I'm pretty sure this option is nvidia specific...[/QUOTE]
Jeez, you're right.  I totally forgot about that.  Sorry!

[QUOTE=pelle.k]post the result of "glxgears -printfps"[/QUOTE]
There's a good idea.  It will give us a bit more info.

---

### Post by DarBarf on 2006-03-04
```
darbar@ubuntu:~$ glxgears -printfps
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

```

i guess i'm not using the correct Nvidia driver?

---

### Post by nrwilk on 2006-03-04
That would be my guess too.

Try compiling it using the second method of this guide:
[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)

---

### Post by DarBarf on 2006-03-04
[QUOTE=nrwilk]That would be my guess too.

Try compiling it using the second method of this guide:
[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)[/QUOTE]


i'm gonna give that a shot tomorrow afternoon, and hopefully it works..
i checked out the list of cards that aren't supported anymore, and mine isn't in that list, so i should be in the clear.

i'll post in here what happens one way or another.

thanks peop's

---

### Post by nrwilk on 2006-03-04
Good luck!

That's the guide I always use.  I've had really nice results every time with it.

For some reason, I can't bring myself to use nvidia drivers from the repositories.  I dunno why...

---

### Post by DarBarf on 2006-03-11
well... i didn't end up messin' around with my nvidia driver... 
i plugged in another video card and monitor, and am running a multihead 
setting in xorg.conf..  having two monitors is pretty usefull, but bad if you have a short attention span :-P
then i upgraded to kde3.5.1
and the weird trippy (:-P) tracers on all the windows are gone :)
problem solved... somehow

thought i should follow up the thread with a solution.. sort of.

---

### Post by nrwilk on 2006-03-11
I'm glad you got it sorted! :D  \\:D/

---

