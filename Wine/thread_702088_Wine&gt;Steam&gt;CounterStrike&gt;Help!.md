---
title: "Wine&gt;Steam&gt;CounterStrike&gt;Help!"
date: 2008-02-19
forum: Wine
---

### Post by Flynn555 on 2008-02-19
whenever i try to play any steam game through wine...the game is extremely choppy and laggy.  even the steam (my games) window laggs when i drag it across the desktop...is this a common problem with running steam on wine? or is it a video card problem?

ive tried it with the window manager and the virtual desktop in wine.

---

### Post by xtek0 on 2008-02-19
Run it through win98 in wincfg

---

### Post by Flynn555 on 2008-02-20
ok i set it to run through win98 but now im getting a message that says...

please turn off compatibility mode...

1. right click steam exe.
2. go to properties
3. select compatibility tab
4. uncheck run in compatibility mode

cant find compatibly tab,
im guessing these are instructions for disabling compatibility mode in windows...

still laggy when i set it to run through ME, 2000, XP, 2003 and vista  :(  
i get compatiblity errors  when i run through anything < 98

---

### Post by aoanla on 2008-02-20
There are two issues here:

1) The Steam application being slow to refresh itself. 

This may be due to poorly supported GTK rendering (IIRC) on your graphics card. Is it a recent nVidia card?

2) Running apps in Windows 98 mode. 

This is more complicated than has been made out. You *don't* want to run Steam in Win98 mode; this is what's causing those compatibility mode errors. You want to find the hl2.exe in your Steam folder and set *that* to Win98 mode.

You may also find performance improves if you add -dxlevel 81 to the launch options for the games you play (this is in Properties for each game in Steam itself).

---

### Post by dmn_clown on 2008-02-20
> **Flynn555 said:**
> ok i set it to run through win98 but now im getting a message that says...

please turn off compatibility mode...

1. right click steam exe.
2. go to properties
3. select compatibility tab
4. uncheck run in compatibility mode

cant find compatibly tab,
im guessing these are instructions for disabling compatibility mode in windows...

still laggy when i set it to run through ME, 2000, XP, 2003 and vista  :(  
i get compatiblity errors  when i run through anything < 98

winecfg > add application > <browse to counterstrike:source directory> css.exe > windows 98

That is what he was talking about, steam will run in xp mode, counterstrike: source will then be run in windows 98 mode, also you should do what aoanla said and start the game with dxlevel 81 as dx 9.0 effects are not as smooth as they should be (though they look pretty sweet!)

---

### Post by Flynn555 on 2008-02-20
> **aoanla said:**
> There are two issues here:

1) The Steam application being slow to refresh itself. 

This may be due to poorly supported GTK rendering (IIRC) on your graphics card. Is it a recent nVidia card?

2) Running apps in Windows 98 mode. 

This is more complicated than has been made out. You *don't* want to run Steam in Win98 mode; this is what's causing those compatibility mode errors. You want to find the hl2.exe in your Steam folder and set *that* to Win98 mode.

You may also find performance improves if you add -dxlevel 81 to the launch options for the games you play (this is in Properties for each game in Steam itself).

i dont think its my gfx card...its 128meg i dont know the make it came with my comp (Dell)
but...steam/steam games worked fine when my comp was running windows.

---

### Post by aoanla on 2008-02-20
Yes, they may well have done. However! Wine is not Windows, and graphics card drivers can also be different between Linux and Windows.

I asked, because the newer nVidia cards, ironically, are worse at 2d rendering than older cards - and this is particularly obvious when applications in Linux use a particular display library called GTK. I /think/ Steam is rendered through GTK when Wine runs it, so...

---

### Post by Flynn555 on 2008-02-20
i followed your instructions...the game runs a little bit smother...

my two main problems are...
-the game flickers whenever i (right or left) click the mouse.
-the game crashes/freezes when the server experiences any kind of lag spyke (resulting
 in me having to restart)

edit. the game crashes/freezes alot (online and offline)

---

### Post by Flynn555 on 2008-02-20
i am running compiz could that have anything to do with it?

---

### Post by kiwiadam2 on 2008-02-20
> **aoanla said:**
> 
I asked, because the newer nVidia cards, ironically, are worse at 2d rendering than older cards - and this is particularly obvious when applications in Linux use a particular display library called GTK. I /think/ Steam is rendered through GTK when Wine runs it, so...

Not true - GTK does **not** use hardware acceleration. GTK is the library used for creating GUI interfaces with GNOME. OpenGL performance is what matters for hardware accelerated 2d & 3d under linux, and newer nVidia cards handle it very well - far better than older cards.

---

### Post by kiwiadam2 on 2008-02-20
Is it counter strike or counter strike source? they are different games, and Steam would suggest that this is source. if so try [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731)

---

### Post by aoanla on 2008-02-21
> **kiwiadam2 said:**
> Not true - GTK does **not** use hardware acceleration. GTK is the library used for creating GUI interfaces with GNOME. OpenGL performance is what matters for hardware accelerated 2d & 3d under linux, and newer nVidia cards handle it very well - far better than older cards.

In that case, perhaps you'd like to explain why the "official" nVidia linux forums contain this discussion about a long-standing issue with 2d rendering efficiency on 8x00 series nVidia cards?
(and when did I claim that GTK uses hardware acceleration? I meant that I thought Wine might use GTK to render 2d entities, like the Steam window - not that it would render 3d objects! Clearly that's outside of GTK's scope!)

[http://www.nvnews.net/vbulletin/showthread.php?t=87865](http://www.nvnews.net/vbulletin/showthread.php?t=87865)

Notice that the issue is claimed to be (on page 11 of the thread, if you want to skip to it) 
> The problem with GTK is that it does double-buffering in a very inefficient way:

For almost every component they create a pixmap (a drawable image), paint into it once, draw it and free it again. Just a single window-repaint of gftp leads to ~15mb pixmap (de)allocation every time.
Because allocation of pixmaps is expensive on some hardware, the nvidia driver allocates a pixmap in RAM (instead of the vdieo ram on the graphic card) and uses the CPU to render the GTK content.

Therefor the reason GTK beeing that slow is GTK's inefficient double-buffering forces the nvidia driver into software rendering. Complain at gtk-list and let them know you suffer from low performance - its really not a problem of the nvidia driver.


---

### Post by strongboww on 2008-02-21
hi,
i also have problems with steam,

install went great, tahoma installed

but when i doubleclick on e.g. cs the game starts but when the menu things are to come it crashes and throws me back on desktop with 640x480 res, normally it should be 1680x1050

---

### Post by Flynn555 on 2008-02-21
not source...its just counterstrike and counterstrike condition zero.

i also tried playing hl:1 and that completely crashed within the first 2 min.
and the textures didnt even show up just models

---

### Post by jacob01 on 2008-02-21
> **Flynn555 said:**
> i am running compiz could that have anything to do with it?

yea thats probably your problem    try to disable it

---

### Post by Flynn555 on 2008-02-22
how?

---

### Post by aoanla on 2008-02-23
> **Flynn555 said:**
> how?

Go to System->Appearance->Visual Effects  and set them to None.

---

### Post by Flynn555 on 2008-02-23
> **aoanla said:**
> Go to System->Appearance->Visual Effects  and set them to None.

oh duh...sry that was nooby of me. ;)

---

