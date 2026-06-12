---
title: "sudden WoW error - needs &quot;dual-tmu support&quot;"
date: 2007-09-02
forum: Wine
---

### Post by ministoat on 2007-09-02
i was running wow fine earlier this morning, but i went to run it now and get this error saying that my 3d card needs to support dual-tmu - i've googled a bit about it and i'd already set .wtf to run in opengl, have latest drivers etc..

what shall i do here? i don't exactly know how to go about reinstalling the nvidia drivers tbh

---

### Post by Nkari on 2007-09-03
I get the same error when attempting to run in Open GL mode with Nvidia 7600 video cards.

I'm as up to date as you can get with the video drivers that Envy installs.

Perhaps you where in D3D mode before when it was working, that is the mode it will default to unless you specify openGL. I do get a bit further in D3D.

---

### Post by ministoat on 2007-09-04
> **Nkari said:**
> I get the same error when attempting to run in Open GL mode with Nvidia 7600 video cards.

I'm as up to date as you can get with the video drivers that Envy installs.

Perhaps you where in D3D mode before when it was working, that is the mode it will default to unless you specify openGL. I do get a bit further in D3D.
solved - was in opengl to statr with - fixed by running with "d3d" in wtf file, then quit out and changed back to open gl. works fine :)

---

### Post by thieTe4l on 2008-03-15
> **ministoat said:**
> solved - was in opengl to statr with - fixed by running with "d3d" in wtf file, then quit out and changed back to open gl. works fine :)

7600 card, 2.6.24 kernel, actual drivers from hardy repository. worked fine then i got the very same message. the suggested fix didn't work for me unfortunately :-(

i got 169.12 drivers installed, 

#: glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

this is what the error causes imho, don't know what to do -.-

---

### Post by thieTe4l on 2008-03-15
reinstalling the driver suddenly solved it ... whatever

---

