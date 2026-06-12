---
title: "WINE zoomed in"
date: 2008-04-26
forum: Wine
---

### Post by kulotzy on 2008-04-26
Just a simple problem... i was just experimenting with WINE and then all of a sudden, everything is zoomed in (config, fonts, everything) What happened? Is there fix? Please help, thanks.

---

### Post by schtufbox on 2008-04-26
in winecfg go to the graphics tab, right at the bottom there's a slider, on wine 0.9.60 it's called 'screen resolution' though it's actually a dpi slider, what's yours saying? the default is 96dpi (you can type it into the box instead of using the slider too)

---

### Post by kulotzy on 2008-04-26
> **schtufbox said:**
> in winecfg go to the graphics tab, right at the bottom there's a slider, on wine 0.9.60 it's called 'screen resolution' though it's actually a dpi slider, what's yours saying? the default is 96dpi (you can type it into the box instead of using the slider too)

Thanks for replying, however, i cant even see it anymore due to it being extremely zoomed in. Is there way to fix this? Changing the screen resolution doesnt work.

---

### Post by benjoji on 2008-04-26
I have the same problem with the DPI but how could i type it because i cant see the slider here's a pic:

[http://img32.picoodle.com/img/img32/4/4/26/f_Screenshotm_d12e99c.png](http://img32.picoodle.com/img/img32/4/4/26/f_Screenshotm_d12e99c.png)

---

### Post by kulotzy on 2008-04-26
> **benjoji said:**
> I have the same problem with the DPI but how could i type it because i cant see the slider here's a pic:

[http://img32.picoodle.com/img/img32/4/4/26/f_Screenshotm_d12e99c.png](http://img32.picoodle.com/img/img32/4/4/26/f_Screenshotm_d12e99c.png)

i can't even see that far down lol.

---

### Post by kulotzy on 2008-04-26
That sounds like a possible solution that schtufbox suggested... but if only i can see where to type/slide it.

---

### Post by benjoji on 2008-04-26
Just solved my prob you need to click the allow picture shader the press tab then <- key

---

### Post by kulotzy on 2008-04-26
Thanks.

But i seem to have a bigger problem that might require a clean install, so it wouldnt really matter i guess.

---

### Post by schtufbox on 2008-04-26
If you haven't got any windows apps installed yet, you can always delete the  .wine folder from your /home/insertusernamehere/  directory, then just run winecfg again to create a new one

---

### Post by kulotzy on 2008-04-26
> **schtufbox said:**
> If you haven't got any windows apps installed yet, you can always delete the  .wine folder from your /home/insertusernamehere/  directory, then just run winecfg again to create a new one

Thanks, i will definitely keep that in mind for future reference.

---

### Post by McLeod Brennaman on 2008-04-26
Before you wipe and reinstall, make sure it's not a compiz issue. Compiz does all kinds of weird things to me with modifier keys and desktop zooming, effects, etc. Pop open a terminal and:

sudo apt-get install compizconfig-settings-manager

And just go ahead and turn off anything that looks like it may have something to do with zooming. And disable any keybindings it has. Unless you use it often or actually have vision issues, it's just one more thing that can go wrong.

If you're still having that issue, then it probably is Wine that's messing things up. Even still, before you wipe everything, go into a terminal again:

winecfg

And go to the graphics tab. Emulate a virtual desktop. That confines Wine to whatever space you give it, and puts it back under metacity's full control instead of integrating it. Or should, at least. I've found this to be much more stable than desktop integration. Good luck, not sure if I helped at all.

---

