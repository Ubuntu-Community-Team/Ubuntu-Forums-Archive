---
title: "Cannot add DLL override"
date: 2007-12-05
forum: Wine
---

### Post by 8daysaweek.co.uk on 2007-12-05
I have searched both the generally and in these forums and cannot find a solution to this :(

I have a program which works under WINE, but needs a DLL override for comctl32.  When I go into winecfg the Add, Edit and Remove buttons are greyed out, so that even though I can select the file from the drop down list, I can't "Add" it into WINE.

Any ideas?

---

### Post by cogadh on 2007-12-05
When you select it from the list, add ".dll" to the end of the file name, the buttons will magically become accessible. I think that just started to happen with 0.9.50, or at least that's when I first started to notice it.

---

### Post by 8daysaweek.co.uk on 2007-12-05
Ah, so simple!  Thanks for the pointer :)

---

