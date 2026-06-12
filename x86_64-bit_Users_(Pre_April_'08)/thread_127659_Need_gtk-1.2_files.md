---
title: "Need gtk-1.2 files"
date: 2006-02-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-02-09
I installed Endeavour2 on my Ubuntu-64 Breezy laptop and I love it. Great file manager. But the fonts suck and when I select different fonts in the Preferences, none of them work. I have been told I need to install gtk-devel and gtk-lib-1.2. They are not listed in Synaptic, and I can't find them on the net. Does anyone know exactly what files I need, where I can find them, and how I can install them (I am a n00bie). Thanks!

---

### Post by JAwuku on 2006-02-09
try ```
sudo apt-get install libgtk1.2-dev libglib1.2-dev
```

or search for **libgtk1.2-dev** and **libglib1.2-dev** in synaptic

---

### Post by John Jason Jordan on 2006-02-09
[QUOTE=JAwuku]try ```
sudo apt-get install libgtk1.2-dev libglib1.2-dev
```

or search for **libgtk1.2-dev** and **libglib1.2-dev** in synaptic[/QUOTE]
Thanks! Having the right name makes it a lot easier to find something. :)

I did it with Synaptic where I found that libglib1.2-dev was already installed, so I just installed libgtk1.2-dev. Unfortunately, that did not solve the problem. It still won't change the font. So evidently the person who told that installing those two things would fix it was wrong.

:(

---

### Post by RAOF on 2006-02-09
You'd need to recompile Endevour to use your newly installed gtk build environment.

---

### Post by John Jason Jordan on 2006-02-09
[QUOTE=RAOF]You'd need to recompile Endevour to use your newly installed gtk build environment.[/QUOTE]
I've never compiled anything before. Is there a wiki or something where I can find out how to do that?

---

### Post by RAOF on 2006-02-09
[QUOTE=John Jason Jordan]I've never compiled anything before. Is there a wiki or something where I can find out how to do that?[/QUOTE]
Oh, how did you install Endevour in the first place?  I assumed that because you were recommended the gtk-devel package you had been compiling from source - that's the only reason you'd need a -dev package.

---

### Post by John Jason Jordan on 2006-02-09
[QUOTE=RAOF]Oh, how did you install Endevour in the first place?  I assumed that because you were recommended the gtk-devel package you had been compiling from source - that's the only reason you'd need a -dev package.[/QUOTE]
It was listed in Synaptic. Click, click, click, click -- you're done!  :)

---

