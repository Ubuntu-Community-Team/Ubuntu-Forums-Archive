---
title: "gnome-panel disappeared...."
date: 2006-11-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by weird_c00kie on 2006-11-20
i just had the weirdest thing today.

i restarted my ubuntu, and as i logged in, gnome-panel disappeared.
i tried removing it and reinstalling it through the terminal, but it still won't run on start-up

problem is, in order to run gnome-panel now i have to use the terminal, which means that soon as i close the terminal window, i lose the panels again.
for some reason it's also hiding most of the options under the admin menu. all i can see there now are: device manager, network tools, printing, system log and system monitor. i can't even get to synaptic.

if it helps, when i run gnome-panel from the terminal it runs, but i get this:

> (gnome-panel:18931): Gdk-WARNING **: locale not supported by Xlib

(gnome-panel:18931): Gdk-WARNING **: cannot set locale modifiers

(gnome-panel:18931): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
- using device default
- using device default

(gnome-panel:18931): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(gnome-panel:18931): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -5 and height 24



it's just weird because one moment it was working and the next it wasn't :(


anyone have any ideas?

---

### Post by weird_c00kie on 2006-11-20
that is so weird....

after numerous restarts, i finally managed to find gnome-terminal in one of the folders and ran gnome-panels through it. my panels came back, despite the aforementioned complaints about xlib, and when i relogged just now the panels came up like normal. i didn't have to run them through the terminal, they just loaded up automatically


weird....

---

### Post by the79bomb on 2007-02-05
I have the same problem but don't know where to find the gnome terminal icon.  I have searched for it already but the file system is a bit new and confusing to me and I could not find the executable.  I also don't know how to run the panels in terminal if I did find it.

Thanks, Tim

---

### Post by weird_c00kie on 2007-07-26
well, this was posted a long time ago, so hopefully you would've come up with a solution to your problem by now :D

i can't remember where i found the gnome-terminal... it was one of those once-in-a-lifetime moments of epiphany hehe
maybe someone else can provide its specific location :D

---

### Post by praxis22 on 2007-07-26
Oddly enough something like that happened to me to last time I booted up. I have two panels, and the bottom one malfunctioned. I deleted it and started again, built a new one. this time I had two "show desktop" applets running, so I just deleted the one I hadn't locked.

**EDIT:** gnome-terminal is found here:
/usr/bin/gnome-terminal

---

### Post by weird_c00kie on 2007-07-28
maybe it's just one of those weird things that like to happen from time to time just to make us spend an afternoon fixing them hehe

thanks for the terminal path! :D

---

### Post by alegir on 2008-04-29
Hello,

I recommend installing nautilus-openterminal for the future.

It gives you an "Open Terminal" option when you right-click on the desktop.

Also in any folder, it will open a terminal and cd to that directory (very useful).

---

