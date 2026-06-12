---
title: "Jedi Outcast:GLW_StartOpenGL() - could not load OpenGL subsystem"
date: 2006-07-21
forum: Wine
---

### Post by hanzomon4 on 2006-07-21
[quot]I got it to install using loki but when I go to start it I get this error.
I have a nvidia Geforce 5500 fx and I'm using xgl/compiz[/quote]

It was an xgl issue the fix was to add (-xorgAc)to your gdm.conf-custom

like this  

```
[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -xorgAc  -accel glx:pbuffer -accel xv:fbo
flexible=true

```
this also you to run programs on the underlying xserver, (For ATI users that 0 should be a 1)

and then just run your game like this

for Nvidia ```
DSPLAY=:93 game
```
for ati     ```
DISPLAY=:0 game
```

Okay thats all

---

### Post by hanzomon4 on 2006-07-21
Fixed

---

### Post by chadk on 2006-07-22
Any idea how to get XQF to use the DISPLAY=:0 before launching ET?  If I try it, it tells me it can't find the command DISPLAY=:0

---

### Post by hanzomon4 on 2006-07-22
Do have xgl running, and if so did you add the -xorgAc to gdm.conf-custom.
What video card do you have? If you have an nvidia try DISPLAY=:93.
And also put "DISPLAY=:" first 
```
DISPLAY=:0 game
```
I installed xqf and I it worked with DISPLAY=:93 xqf, but From what I saw it looked like a regular app. I didn't it use so I'm not sure if it does anything else, but you should really only use the "DISPLAY=:" for runinng games

---

### Post by PriceChild on 2006-07-22
There is already a similar how to in the "HOWTo"s to allow you to run any app on a standard server using a "nonXgl" prefix e.g. "nonXgl ut2004"

---

### Post by chadk on 2006-07-22
yah and that nonXgl didn't work out for me very well but this post's fix worked great so...

---

### Post by hanzomon4 on 2006-07-22
> **PriceChild said:**
> There is already a similar how to in the "HOWTo"s to allow you to run any app on a standard server using a "nonXgl" prefix e.g. "nonXgl ut2004"

I didn't start this as a howto, I answered my own question.
I just edited my post to show how I fixed it, just in case someone else had a similar problem.

---

### Post by Angel456 on 2007-12-23
Plz help me out, i really want to play star wars jedi Outcast but becoz of this error i cant. i cant seem to figure out what to do. i am at a total lose here. plz help me somebody. plz send in an ez solution which i can understand easily n work out as i am not much of a computer freak. plz help me plzzz

---

### Post by coldReactive on 2009-09-16
Since Angel456 didn't get his/her answered, I'll ask for them:

What if you don't have a **gdm.conf-custom** file and what if you don't know how to use that DISPLAY= option or where to use it?

What then?

---

