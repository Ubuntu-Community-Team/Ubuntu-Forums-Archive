---
title: "Mighty Mouse and Ubuntu 5.10 / Dapper Drake ?"
date: 2005-12-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by FredB on 2005-12-15
Simple question : do they work allright together ?

Thanks ;)

---

### Post by ssam on 2005-12-15
it should work fine as a mouse, but i doubt all the fancy stuff would work.

try it with the live cd

---

### Post by muchmusic on 2005-12-16
works great for scrolling (vertical only), left and right clicking and that's it.

side buttons seem to do some kind of paste function by default, but I can't test it right now.

---

### Post by ssam on 2005-12-16
it good to know all those bits work.

middle click is paste on X11 (select to copy), the higher numbered buttons are probably mapping back over the normal one (this happens on my logitech mx500). it may be possible to get the side buttons to map to high click numbers, and then some software can use them.

may have a look at
[https://wiki.ubuntu.com/ManyButtonsMouseHowto](https://wiki.ubuntu.com/ManyButtonsMouseHowto)
[https://wiki.ubuntu.com/mx1000mouse](https://wiki.ubuntu.com/mx1000mouse)

and report any findings

---

### Post by muchmusic on 2005-12-17
You are right ssam, it is just mapping paste to both the scroll button and the side 
"squeeze" buttons. I am able to get the buttons to do different things thanks to those links. I will write something up. Should I just post here? Makes sense I think.

---

### Post by ssam on 2005-12-17
its best if you post info in the wiki. you could either add a section to one of the existing pages or make a mighty mouse page.

then post a link to the wiki here, so we can have a look.

---

### Post by FredB on 2005-12-18
Thanks for your answer. I will have to wait until KDE 3.5 packages are built for powerpc ;)

---

### Post by numb555 on 2006-08-30
The mouse works great for me under Dapper. 

Just need to learn how to map the  "Squeeze Button" to activate Compiz Scale.

I've run the mouse in Xev, and all buttons are recognized, Squeeze being button 8.  Can anyone help on this??

---

### Post by ben s on 2006-09-01
Run gconf-editor, browse to /apps/compiz/plugins/scale/screen0/options and change initiate and terminate to the string "Button8".  At least, that's what worked for me in OpenSUSE.  I haven't tried it in Ubuntu.

---

