---
title: "Video problems with ATI X1650"
date: 2008-02-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by guilly on 2008-02-21
HI guy's, Alright so I successfuly installed my 64bit edition of 6.06 Drapper (I think that's what it's called) I am running 2 19" Widescreens so the first thing I did was went and downloaded the drivers off of amd's website for my video card. Then I reconfigured XServer, everything seemed to have worked. However when i go into my ATI Control Center and enable Big Desktop everything is fine and dandy until i restart my p.c. Once I do that my screens go back to acting as a "clones". I guess I should mention that my "Big desktop" still works when i'm at the logon screen after I have restarted they only become "Clones" again once I log in.


Any help is appreciated, I've attached my xorg file aswell

Thanks

---

### Post by Yellow Pasque on 2008-02-21
I believe you need two monitor sections, with a "right of" or "left of" option in your secondary one. I think you also need a Virtual line in your Screen section for Big Desktop (e.g. Virtual 2880 900)
You might try automatically setting it up with something like:
```
sudo aticonfig --dtop=horizontal --overlay-on=1
```

---

### Post by guilly on 2008-02-21
ok great,

I'll take a look when I get home tonight. Which option would be the best  doing it thru xorg.conf or the automatic way like you suggested as a second option?

Thanks

---

### Post by Yellow Pasque on 2008-02-21
Try the automatic way and then look at the xorg.conf to see what it came up with. We'll go from there.

---

### Post by guilly on 2008-02-21
Well I tried the automatic way and this is what it gave me as output in the terminal. I don't quite understand what you mean when you talked about inserting virtual line and such in my xorg.conf. Also after running that command it seemed to have created a new xorg file and called it xorg.conf.fglrx-0 i tried using that one as my xorg wiht no luck.

> Warning: Failed to set hardware overlay to head 1 immediately.
Warning: Option 'DesktopSetup' doesn't affect running session.
Using xorg.conf
Saved back-up to xorg.conf.fglrx-0

any help would be awsome!!

---

### Post by Yellow Pasque on 2008-02-21
Ok, what does your xorg.conf look like now?

---

### Post by guilly on 2008-02-21
same as before haven't changed it. incase you want to see the new one that the command created here it is...

---

