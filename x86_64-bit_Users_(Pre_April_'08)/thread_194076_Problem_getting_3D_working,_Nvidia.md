---
title: "Problem getting 3D working, Nvidia"
date: 2006-06-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by dlyons on 2006-06-10
I'm having a problem getting 3D to work. I've installed the nvidia drivers following a couple guides and I get the splash screen on bootup showing it has installed. However, when I try to run glxinfo or glxgears, I get:

dustin@felix:~$ glxinfo
name of display: :0.0
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  147 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  15
  Current serial number in output stream:  16

I fooled around and noticed that when I type 'startx' at the prompt to load X, glxinfo and glxgears works. However, when the computer boots by itself or I start X by '/etc/init.d/gdm start', that's when I get the problem.

Note I'm running XGL with Metacity, Compiz isn't running and I'm trying to solve the problem of why I'm not getting 3D.

Also, maybe someone can explain the difference between 'startx' and manually telling gdm to start... why one loads the chooser and the other doesn't.

---

### Post by dermotti on 2006-06-10
hmmm....thats a tough one......

this may not solve your problem, but its worth a shot.
sudo dpkg-reconfigure xserver-xorg and select nvidia as the driver.

---

### Post by dlyons on 2006-06-10
already tried that... does nothing

---

### Post by kuja on 2006-06-11
I'm pretty sure that's an XGL issue. OpenGL apps (or even glxinfo) won't run in it. There are a variety of ways to work around it as far as I saw, ranging from running multiple sessions, running the app as a nested session, or least preferred, living without. I'll see what I can dig up for you on it.

---

### Post by RAOF on 2006-06-12
Where did you get xgl from?  If you haven't added any of the 3rd party XGL repositories, you'll be getting it from universe.  That package is so old that an entire species of spider has evolved within it.  Plus, it never worked on AMD64, with errors similar to the ones you're getting.

---

