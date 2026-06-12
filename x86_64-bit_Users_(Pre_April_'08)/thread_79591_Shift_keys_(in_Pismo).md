---
title: "Shift keys (in Pismo)"
date: 2005-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by thalavoy on 2005-10-20
Hello,

My application (a GTK2 immodule) requires simultaneous pressing of the two (left/right) shift keys. But, through 'xev', I can see, that both the physical left and right Shift kesy in my G3 (Pismo) powerbook, returns as 'Shift_L' (left shift).
After some trial and error, I found that 'fn' + Shift (left or right) now returns Shift_R.
Same is the case of Option/Alt keys. Only fn+ gives me the Right stuff.
Is there a way to get it corrected (pressing the right shift/alt should give Shift_R/Alt_R)?

Thanks
Siva

---

### Post by Cyhatch on 2005-12-02
Um, did you try using [FONT="Courier New"]xmodmap[/FONT]?

EDIT: Okay, bad joke, agreed.

---

### Post by Cyhatch on 2005-12-02
On second thought: Might it have something to do with the keyboard?

(CONTROL+F on "both shift" @ [this page]("http://www.pseudorandom.co.uk/2003/debian/tibook/").

Also, maybe paste your [FONT="Courier New"]/etc/X11/xorg.conf[/FONT] here? That won't help me help you, but might somebody else.)

---

