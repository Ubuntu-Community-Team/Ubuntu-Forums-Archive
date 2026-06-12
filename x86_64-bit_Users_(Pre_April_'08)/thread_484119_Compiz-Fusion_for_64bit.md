---
title: "Compiz-Fusion for 64bit"
date: 2007-06-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mauriciobc on 2007-06-25
I´ve posted this in the Desktop Effects & Customization but had no reply.
Are there any repositories out there with the new packages for the compiz-fusion?

Anyways,
thanx for the support people!
:p

---

### Post by Kobalt on 2007-06-25
Not yet, they are comming very soon : possibly this night or tomorrow (G.M.T).
You can coompile it though, if you really 'need' it :)

---

### Post by Mauriciobc on 2007-06-25
Thanx man! I´ve tried unsuccessfully so I guess I´ll just wait!
OMG! One more sleepless night! LOL
;)

---

### Post by jamesford on 2007-06-25
i cant wait either :)

---

### Post by Kobalt on 2007-06-26
A guide is available to install Compiz Fusion on (K)Ubuntu64 [here]("http://ubuntuforums.org/showthread.php?t=485284").

Enjoy ! :)

---

### Post by fracturedmorals on 2007-06-28
I have an ATI Radeon m200. 3d support is only through the fglrx driver and thusly I am limited to XGL.

My problem is this: Whenever I'm in XGL and I try to start compiz fusion, I get a "GLX_EXT_TEXTURE_FROM_PIXMAP missing" error.

Does anybody have a proposed solution?

My output from "glxinfo|grep texture" Tells me that I have the extension when I am running xorg, yet it tells me it's missing when I'm under XGL

I'd really like to get compiz fusion up and running on this system... I seem to be able to use beryl, and the built-in version of compiz, so what am I missing out on?

---

### Post by fracturedmorals on 2007-06-30
bump

---

### Post by sawjew on 2007-07-01
I have installed compiz-fusion from this repository [http://janvitus.interfree.it/ubuntu/]("http://janvitus.interfree.it/ubuntu/") and it seems to be working fine.

Use the experimental repository and it has somewhere near the latest compiz-fusion.

---

### Post by sambehera on 2007-07-02
i installed compiz-core and compiz-fusion from that repository in adept... now ... how do i get compiz fusion running?  "ccsm" opens up the settings manager but thats as far as i can get right now... no compiz fusion experience :(

---

### Post by sawjew on 2007-07-02
Use Alt-F2 to open the Start Programs window and type in ```
compiz --replace
```
If you want to start compiz automatically on startup add an entry to System>Preferences>Sessions under the Startup Programs tab with ```
compiz --replace
``` then next time you log in it should start automatically.

If you have problems with it hanging on login then follow the instructions in post #15 here [http://ubuntuforums.org/showthread.php?p=2946458#post2946458]("http://ubuntuforums.org/showthread.php?p=2946458#post2946458")

---

### Post by fonsocm on 2007-07-03
Treviño has made available a repository with compiz fusion for AMD64:

[http://3v1n0.tuxfamily.org/dists/feisty/eyecandy-amd64/](http://3v1n0.tuxfamily.org/dists/feisty/eyecandy-amd64/)

---

### Post by BobCFC on 2007-07-03
> **fonsocm said:**
> Treviño has made available a repository with compiz fusion for AMD64:

[http://3v1n0.tuxfamily.org/dists/feisty/eyecandy-amd64/](http://3v1n0.tuxfamily.org/dists/feisty/eyecandy-amd64/)


Thanks it works great, although I couldn't get the gpg key to authenticate.

---

### Post by fonsocm on 2007-07-05
In this adress: 

[http://3v1n0.tuxfamily.org/](http://3v1n0.tuxfamily.org/)

you have the instructions to add the key.

---

