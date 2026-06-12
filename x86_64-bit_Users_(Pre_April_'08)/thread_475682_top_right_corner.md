---
title: "top right corner"
date: 2007-06-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by karl_kashofer on 2007-06-16
Hi !

I am using KDE.

On my edgy eft 32 bit system when I have one window maximised and i move my mouse cursor in the top right screen corner and press the left mouse button it will close the window although the tip of the mouse cursor is not on the X button.

In my new feisty 64bit system this does not work, I have to position the mouse cursor right over the X which requires additional attention.

This is annoying, Anyone know why this is different ?

Thanks,
Karl

---

### Post by karl_kashofer on 2007-06-18
hmm, it seems the buttons are placed differently on my edgy system, the top X button is right on the right screen edge. 
Also if i move my mouse on the top screen edge the buttons get activated in edgy, while in feisty they do not.

Anyone ?

---

### Post by Ayuthia on 2007-06-19
I could be wrong, some of the themes in KDE can have the window frame and buttons adjusted under Window Decorations.  

If anything at all, the crew at [http://www.kubuntuforums.com](http://www.kubuntuforums.com) might be of assistance.

If you are still not able to get any help at either forum within the next 24 hours(I check both), I will pop in a kubuntu live CD and see if I can find it for you.

---

### Post by Ayuthia on 2007-06-19
I checked into this and found three things:

1)  I ran the kubuntu 7.04 live CD and was able to use the close button in the far top right corner when maximized.  You can change the width and height of the window by going to the control center->appearance->window decoration but the button will still work no matter how big the window frame is.

2)  Not all the window decorations allow the ability to close in the top right corner.

3)  I am currently using ubuntu 7.04 from Linux Magazine and it comes with KDE as an optional desktop manager.  However, when I am in KDE, it does not allow me to close the window in the far corner.  It looks like this is the case because it provides you the ability to resize the window when maximized.  To turn off the option to resize windows when maximized, you will need to go to the konsole/terminal and edit $HOME/.kde/share/config/kwinrc.  In this file, you will need to change MoveResizeMaximizedWindows from true to false.  You will need to restart KDE and the windows should allow you to close from the upper right hand corner.

---

### Post by karl_kashofer on 2007-06-19
Hey Ayuthia !

> **Ayuthia said:**
> 
[snip]
3)  I am currently using ubuntu 7.04 from Linux Magazine and it comes with KDE as an optional desktop manager.  However, when I am in KDE, it does not allow me to close the window in the far corner.  It looks like this is the case because it provides you the ability to resize the window when maximized.  To turn off the option to resize windows when maximized, you will need to go to the konsole/terminal and edit $HOME/.kde/share/config/kwinrc.  In this file, you will need to change MoveResizeMaximizedWindows from true to false.  You will need to restart KDE and the windows should allow you to close from the upper right hand corner.

This did the trick !
Thanks a lot for your help, this is why this community is so great !
Cheers,
Karl

---

