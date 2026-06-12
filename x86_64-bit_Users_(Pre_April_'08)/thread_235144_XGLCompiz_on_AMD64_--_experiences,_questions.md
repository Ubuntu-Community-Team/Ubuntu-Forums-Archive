---
title: "XGL/Compiz on AMD64 -- experiences, questions"
date: 2006-08-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by spirilis on 2006-08-12
I just got XGL/Compiz half-working on my box.

HW:
AMD Athlon64 3000+, 2GB RAM
ATI Radeon 9800Pro 256MB


Using the latest ATI Radeon drivers (8.27.10).  Only quirk I've noticed with this driver is that it blanks my LCD monitor whenever X starts, the workaround is to use CTRL-ALT-KEYPAD+ followed by CTRL-ALT-KEYPAD- to regain the screen.

I have installed Xgl/Compiz from the following repository:
```
deb [http://ubuntu.systemadministrator.org](http://ubuntu.systemadministrator.org) dapper eyecandy
```

I tried the xgl.compiz.info one but there were unmet library dependencies (it was asking for a version of libsvg-cairo that was newer than the one contained in the repository!)

I loosely followed the tutorial here: [http://www.ubuntuforums.org/showthread.php?t=219336](http://www.ubuntuforums.org/showthread.php?t=219336) tweaking as necessary (such as leaving out the Radeon driver piece, using the latest fglrx instead) since it worked for me on my Dell Latitude D600 at work.  Only missing piece is gset-compiz -- I couldn't find that in the binary-x86_64 part of the repository.

Problems:
I cannot start Xgl if Xorg is running with the "Composite" feature enabled.  Xgl spits out this message:
```

X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  27
  Current serial number in output stream:  28

```

Without Composite enabled, I can start XGL and run compiz, and everything works except for some odd reason I have no window decorations--ie no titlebar, no resize handles, no minimize/maximize/close buttons.  The gnome-window-decorator process is running.  I assume that's related to Composite support?
Update- When I run Xorg and Xgl, I do have the window decorations--the window decorations only disappear once I run Compiz.

Otherwise, I can Alt-Tab between windows, do the Expose look with the mouse cursor in the upper right corner, and switch between the 3D virtual desktops nice and smoothly.  I guess I can deal without the window decorations for now.  I do like the fading effects on menus.

Questions-
1. What does "Composite" do?  I'm talking about this:
```
#Section "Extensions"
#       Option "Composite" "Enable"
#EndSection
```
(obviously commented out at the moment)

2. Is there a better repository I should be using for my xserver-xgl, compiz-* packages for x86_64?

---

