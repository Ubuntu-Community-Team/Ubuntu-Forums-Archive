---
title: "Wine - steam, scroll bar broken  (56K WARNING!)"
date: 2007-09-09
forum: Wine
---

### Post by BeastlyKings on 2007-09-09
When installing steam under wine, when I get to the window where you have to scroll down and accept the agreement to install wine I cannot scroll down. The scroll bar just jumps back up really fast, so fast that my cpu maxes out, and the code you see in the terminal goes really fast as well (must be connected to the prob?).

I have tried running in a virtual environment but no go, please help?

[IMG]http://i13.tinypic.com/4m2goaw.png[/IMG]

[IMG]http://i9.tinypic.com/5zep2iq.png[/IMG]

[IMG]http://i14.tinypic.com/4z1dwrs.png[/IMG]

[IMG]http://i13.tinypic.com/4kmkmds.png[/IMG]




Also, the reason I'm doing this is to install Half Life 2. Just FYI :)

---

### Post by cmat on 2007-09-09
"fixme" is a good indication of what's the problem. Try putting the cursor over it and using the arrow keys.

---

### Post by BeastlyKings on 2007-09-10
Tried, didn't work. I also tried some command I got from the wine IRC channel, it did something to ignore fixme or something like that. It didn't work either.

---

### Post by cogadh on 2007-09-10
The "fixme" messages are generally just developer notes and mean nothing to the normal user. 9 times out of 10, you can ignore everything with a "fixme" on the beginning of it, they are only there to remind the devs of what still needs to be worked on.

As for the problem you are having, the issue you describe was inherent to previous versions of Wine and the Gecko html engine. If you are not using the latest version of Wine, you should update to it (currently 0.9.44) and if you haven't installed the Gecko engine, you need to do that before Steam will work in Wine properly.

On a side note, rather than put massive images in your post, next time use the forum's attach function, that way the images will be attached to your post and only a thumbnail is presented to anyone reading the post.

---

### Post by BeastlyKings on 2007-09-11
I have 0.9.44, I have the gecko engine and I only used the big pics so I could reduce the load on the ubuntu servers. My bad...

---

### Post by BeastlyKings on 2007-09-22
I have used a friends computer to get past the "register" part and I can now play HL2.

---

