---
title: "ati catalyst control"
date: 2008-09-08
forum: x86 64-bit Users
---

### Post by wu-stix on 2008-09-08
When ever I turn on my computer it goes to 1080p mode (1920x108).  The monitor I use is 1024x768 so I can't see all the screen.  I have to open ati catalyst and change this everytime I start up.  I have a tv connected to the hdmi output and that is 1080p and I use that but what I would like to know is how to make the 1024x768 the default display setting without losing the ability to set it to 1080P.

---

### Post by markbuntu on 2008-09-10
You can type 

aticonfig --help 

in a terminal. That will give you the options about setting up your screens. You can also try using the 

Applications/Other/Catalyst Control Center 

to set up your screens. If you do not have it, it is

amdcccle

in the repository.

---

### Post by wu-stix on 2008-09-12
I found out what it was in the ati catalyst if it is set to clone then it defaults to the tv resolution.  I just turn clone off my monitor is the default.

---

### Post by johnaaronrose on 2008-09-14
markbuntu,

I'm running Hardy. I don't see amdcccle in its repositories. Could you point me to the repository(s) it's in now.

---

### Post by markbuntu on 2008-09-14
I think you need to have the third party thing checked in Synaptic to  see the amdcccle. Also, you may already have it installed. It is ususally in Applications/Other. Or you can try to run it from a terminal, 

amdcccle.

---

### Post by johnaaronrose on 2008-09-15
Found it. I needed to install package fglrx-control. Then it appears in Applications - Other - ATI Catalyst Control Center

---

