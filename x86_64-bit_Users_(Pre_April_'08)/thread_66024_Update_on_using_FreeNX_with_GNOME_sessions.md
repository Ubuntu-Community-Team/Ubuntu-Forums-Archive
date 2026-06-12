---
title: "Update on using FreeNX with GNOME sessions"
date: 2005-09-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by DancingSun on 2005-09-15
Well, I finally got myself to methodologically try out each NXClient settings to see which combination of settings will work.  And it sure paid off!

I'm writing this post via NXClient to my home computer right now!  Anyway, for those of you interested, here's how I got FreeNX to work:

I'm using the Windows NXClient, so some description might be off if you are using the client for other platforms.

In the configuration screen, under the "General" tab in the "Display" section, select "Use custom settings" for the image encoding, and click on the "Modify" button.

Under the Encoding section, select "Use plain X bitmaps".  So far this seems the be the source of the problem, and as long as this option is selected, you should be able to start a GNOME session with any other combination of settings.

As for those that are interested in the details of the encoding problem, looking at the "session" log file in the FreeNX server side (under /home/user/.nx/), I found an interesting error message output by the X server:
```
BadLength (poly request too large or internal Xlib length error)
```
Following that I got a bunch of "GC" errors dealing with codeops which sounds really low-level in terms of programming.

Searching through the web with the "BadLength" error, I finally found some relavant discussion that pointed to the X server not being "thread safe" and thus will cause these kind of problems.  The error seem to crop up in gtk applications that deal with color and images, and in some cases any gtk application (gnome included) that uses more than 8-bit color, which sheds some light on why the problem goes away when I tell NXClient to not use any compression methods.

Hope this helps.

Note: my GNOME desktop's "Human" theme colors and buttons are gone though, and some icons in the menu and gnome-panel do not display at all.  Oh well, at least the remote connection is really responsive now.

---

### Post by DancingSun on 2005-09-16
Does anyone know how can I get proper GNOME theme support when connecting via FreeNX?

What I have now is that the window border style seem to conform to the theme that I selected, but the colors, buttons, scrollbars, and other GUI widgets all seem to be stuck at the default or the traditional hard-edged 3D theme.  Icons are all messed up as well.  The trash can gets a big paper icon with an "X" in it, same with the show desktop icon.  All the folder and file icons use some generic file icon.

---

### Post by bugmenot on 2005-09-16
Try to run gnome-settings-daemon

---

### Post by DancingSun on 2005-09-16
[QUOTE=bugmenot]Try to run gnome-settings-daemon[/QUOTE]
Wow, that worked wonders! Except that I get 3 errors on XKB configuration activation.

What does gnome-settings-daemon do?  And why is it that I need to do this even when I am supposed to be logged into GNOME already?

---

### Post by makhand on 2006-01-25
[QUOTE=DancingSun]Wow, that worked wonders! Except that I get 3 errors on XKB configuration activation.[/QUOTE]

Three errors? I seems to get about 3000 errors when i run the gnome-settings-daemon from a terminal.

---

