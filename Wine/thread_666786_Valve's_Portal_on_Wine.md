---
title: "Valve's Portal on Wine"
date: 2008-01-13
forum: Wine
---

### Post by CptJackSparrow57 on 2008-01-13
I'm new to Linux, so I'm going to have to ask for very simple instructions.

But I'm trying to get Portal/Steam to run on Wine (I have no idea what version I have, I just downloaded it the other day, so I'm assuming the newest).

However, whenever I try to run it, it randomly closes without any sort of warning or error message.  Any thoughts?  Feel free to IM me at CptJackSparrow57 via AIM, I'd love the instant feedback and help.

---

### Post by CptJackSparrow57 on 2008-01-13
I get this error

> 
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1


---

### Post by eiskalt on 2008-01-13
i assume you got your wine through synaptic?  GO back there, uninstall it.  Then go here [http://www.winehq.org/?announce=latest](http://www.winehq.org/?announce=latest)

compile wine yourself,  I've used wine for a while now, and I have the best luck when I compile it myself.  I'm currently compiling the newest version of wine, then i'm going to try and load up some counterstrike through steam.... hope all will go well

also open a console then type

wine --version

winecfg

click on the sound/audio tab you cant use alsa in wine, it needs to be oss for steam games to work...

---

### Post by karth on 2008-01-14
It's also possible to install wine through synaptic from Wine project's own repository, and get the latest versoin packaged for Ubuntu, whichever version starting from 6.06

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

