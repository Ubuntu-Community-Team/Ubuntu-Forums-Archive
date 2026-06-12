---
title: "Warcraft III wont boot"
date: 2008-10-07
forum: Wine
---

### Post by chaosdesigner on 2008-10-07
I'm aware that there are alot of tutorials about how to run Warcraft on wine and I have looked at alot of them but I just can't seem to find an answer. I'm running a amd64 Ubuntu Hardy System and I have wine on version 1.1.5. So in most of the tutorials it pretty much looked like that warcraft should pretty much run "out of the box" but I can't really aprove this. My instalation worked perfect but everytime I try to start wc3 I get a black screen and on the bottom a disturbed white box. I can leave that screen with the help of Ctrl and Alt.

I have already treid opening it with opengl but the result had no difference at all. So what else can I try?

Thank you for your help

Edit: This might be the problem:

```
err:quartz:DSoundRender_create Cannot create Direct Sound object
```

---

### Post by chaosdesigner on 2008-10-07
Ok so the situation has changed, i can now start warcraft 3, doesnt matter if I boot it from my windows partition or from my wine drive, both wirks, but both also have their problems. The problem is that now wc3 has extrem flickers... this is the output:
```

fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:ole:CoCreateInstance apartment not initialised
libGL error: drmMap of framebuffer failed (Cannot allocate memory)
libGL error: reverting to (slow) indirect rendering
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33f3b0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f658,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f690,0x00000000), stub!

```

Any Ideas on how to fix this?

---

### Post by PandaGoat on 2008-10-07
You need to rename the Warcraft III/Movies folder or delete it.  

Also if you get low fps run it with -opengl at the very end of the command.

---

### Post by chaosdesigner on 2008-10-08
right deleting the movies folder helped boot wc3, but like I said now it flickers extremly .. I already start it with -opengl too. Any more Ideas on how to solve this?

---

### Post by firedrow on 2008-10-08
> **chaosdesigner said:**
> right deleting the movies folder helped boot wc3, but like I said now it flickers extremly .. I already start it with -opengl too. Any more Ideas on how to solve this?

Have you tried opening it in a Wine desktop?  Most of the time people use Wine without the desktop, but occasionally the desktop will take care of it.  Now when I had WC3 working with Wine I didn't need the desktop, but I was also not using any Compiz or window effects.  You might try turning them completely off to see if that helps.

Also, go to Wine's AppDB and check which version of Wine runs WC3 the best.  Or you can get PlayOnLinux (Wine wrapper) which will setup WC3 with it's own version of Wine so it's running with the best compatibility.

---

### Post by chaosdesigner on 2008-10-08
I tried it with the desktop and the wierd thing is first time it worked, after that it didnt do me the favor anymore and then it didnt make a differnce. What I'm going to try is to disable compiz and if that doesn't work I will, just as you said, try a different version of wine. I'll have to try it later, since I'm at work now but I will keep you guys posted.

---

### Post by chaosdesigner on 2008-10-08
After I disabled compiz everything worked pretty well (its still a little laggy but I gues thats ok).


Thank your very much

---

