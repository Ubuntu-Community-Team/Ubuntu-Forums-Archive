---
title: "Steam on wine."
date: 2008-08-25
forum: Wine
---

### Post by rentacop on 2008-08-25
Hey guys, I am having a problem running steam on wine.

I am running the latest wine from the respos. and i am on hardy. 86 x64. I have a nvidia geforce 9600gt with the latest drivers installed. 

When i try to install steam it loads fine with no errors at all. I can also log into steam with no issues. The problem i am having is that when i try to install a game using steam via interweb it just crashes. I thought maybe i could just go over to my windows half and copy my games over to my .wine/drive_c/Pgram/Steam / folder and when i launch steam again it shows my installed games but when i try to launch the game it just crashes again.

heres my output when i double click on a game from term.

```
err:shell:SHGetFileInfoW pidl is null!
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
Segmentation fault

```


Any help would be grateful!

---

### Post by rentacop on 2008-08-26
bump

---

### Post by hell_prince on 2008-08-26
Well Sorry I can't be much of a help since i'm a noob myself But erm... I'm Having this strange problem... Well the first time I installed Steam it wen't ok and I looged in... But then the second Time I couldn't make a successful login since... It says Theproblem is with my Internet connection or with steam... I think not... Any Help?

---

### Post by rentacop on 2008-08-26
I tried installing steam on crossover and the exact same thing happens. Steam runs fine, When i try to launch a game it just quits.

Is it possible that my gfx card driver isn't properly installed? ...

If so how do i check?

---

### Post by the[V]oid on 2008-08-26
> **rentacop said:**
> Is it possible that my gfx card driver isn't properly installed? ... If so how do i check?

1. run "glxgears" - does it work?
2. run "glxinfo | grep -i direct" - what does it say?

---

### Post by rentacop on 2008-08-26
> **'the[V]oid said:**
> 1. run "glxgears" - does it work?
2. run "glxinfo | grep -i direct" - what does it say?


glxgears - The gears show up fine, Animation also shows up fine. I get this error in term after closing the animation.
```
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 36 requests (36 known processed) with 0 events remaining.

```

glxinfo | grep -i direct -

```
glxinfo | grep -i direct
direct rendering: Yes

```

My guess its running ok.

---

### Post by rentacop on 2008-08-27
Turns out it didnt like the 173.14.09 gfx drivers i had installed. I noticed there was a 173.14.12 driver out. installed, removed wine, installed again, installed steam, good to go.


Thanks for the help.

---

