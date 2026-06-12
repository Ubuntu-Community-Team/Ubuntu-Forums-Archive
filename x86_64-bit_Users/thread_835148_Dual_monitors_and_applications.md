---
title: "Dual monitors and applications"
date: 2008-06-20
forum: x86 64-bit Users
---

### Post by pietervdv on 2008-06-20
Hi!  I'm using Hardy 8.04 with dual monitors and an nVidia card, (Twinview).My question is this... Is there anyway I can adjust my settings to allow me to open Firefox to open on Monitor Two?  Is there anyway to specify the monitor that a program or application will open on?  Any idea where I could get more information on this topic?  Thanks.

---

### Post by xinix on 2008-06-21
Add DISPLAY=:0.1 before your command to launch an app to make it launch on the second monitor.

eg:  ```
DISPLAY=:0.1 firefox
```

At least thats how it works with monitors setup as separate screens.

---

### Post by pietervdv on 2008-06-21
Thanks Xinix this sounds promising.  My next question is where do I find the file in which to change the default opening sequence.

---

### Post by secondstage on 2008-06-21
I don't know where the defualt command file for that is ,but you can go to the top, or bottom bar and make a custom launcher. It won't be in the Applications applet, but at least you have an easy way to launch it.

---

### Post by xinix on 2008-06-21
Right click on the application menu icon and choose 'edit menu'.  You could simply edit the original entry so that the app always opens on the second monitor, or you could duplicate the app entry and set it to open on the second monitor ( this way you can choose which one to launch it on).

---

### Post by markp1989 on 2008-06-21
when i try to run firefox in my second screen, it dont work.

I have two 17" Lcd, using Nvidia Twin View 

when i try starting firefox in the other monitor i get this message 
```
mark@mark-desktop:~$ DISPLAY=:0.1 firefox
Gtk-Message: Failed to load module "libgnomenu": libgnomenu.so: cannot open shared object file: No such file or directory
Error: cannot open display: :0.1
mark@mark-desktop:~$ 

```

---

### Post by xinix on 2008-06-23
Ahh twinview,  not sure how it's done that way. The thing about twinview is that it tricks X into thinking that there is only one screen for the system and spreads it across both monitors.  I imagine that it might be possible to force the app to open on the second monitor by making it open in at an absolute position on your screen (just a guess though).
Your other option would be to set up your monitors as separate xscreens where you would have independent desktops.  Thats how I have mine set up since the second monitor is a tv and I rarely run an app other than mythtv.
With separate screens you can drag files from one screen to the other but not windows (this is in KDE, Gnome may differ).

---

### Post by markbuntu on 2008-06-23
I did it by using the hide buttons on the panel. When I hide it from the first monitor it shows on the second. If I open an app from the panel when it is there, it opens in the second monitor. I kinda found that out by accident.

I don't know if this will work for you, I am using ATI and Big Desktop.

---

### Post by reets on 2008-08-29
I have similar problem with this. I am using nVidia card set as seperate X screen and Xinerama enabled. Using DISPLAY=:0 works just fine. Any ideas on this?


reets@reets-desktop:~$ DISPLAY=:0.1 gedit
cannot open display: 
Run 'gedit --help' to see a full list of available command line options.
reets@reets-desktop:~$ DISPLAY=:1 gedit
cannot open display: 
Run 'gedit --help' to see a full list of available command line options.
reets@reets-desktop:~$

---

### Post by cmavr8 on 2008-09-14
> **markbuntu said:**
> I did it by using the hide buttons on the panel. When I hide it from the first monitor it shows on the second. If I open an app from the panel when it is there, it opens in the second monitor. I kinda found that out by accident.

I don't know if this will work for you, I am using ATI and Big Desktop.

Hi, could you please explain what the hide buttons are? I can't seem to find them..

---

### Post by markbuntu on 2008-09-14
You need to turn on the hide buttons by right clicking on the panel and the choosing properties. They will appear on the ends of the panel.

---

### Post by cmavr8 on 2008-09-15
Thanks!
(doesn't work that good for me, though.. )

EDIT: I have another problem, fullscreen flash videos (in firefox) play in the wrong monitor.

Firefox is on the right screen, maximized, and I'm watching a video. When I try to stretch it to fullscreen it will almost be fullscreen on the left monitor...

---

### Post by fooey on 2008-10-17
you know... i swear. there isn't anything i can't ever find on these forums. it's flippin awesome :)

---

### Post by soul_ache on 2009-01-11
> **xinix said:**
> Add DISPLAY=:0.1 before your command to launch an app to make it launch on the second monitor.

eg:  ```
DISPLAY=:0.1 firefox
```

At least thats how it works with monitors setup as separate screens.

Thank you for this advice! Very helpfull

---

