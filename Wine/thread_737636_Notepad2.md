---
title: "Notepad2"
date: 2008-03-27
forum: Wine
---

### Post by Jookia on 2008-03-27
How would I go about opening a file using Notepad2 in ubuntu? I have the exe.

---

### Post by brownknight on 2008-03-27
> **Jookia said:**
> How would I go about opening a file using Notepad2 in ubuntu? I have the exe.

Have you looked at gedit or geany? They are the Notepad2 alternative for Linux. Gedit is install by default and located in > Applications > Accessories

To install geany, go to Synaptic Package Manager and install it or on the terminal:

sudo aptitude install geany:

---

### Post by Jookia on 2008-03-28
Well, I need to see the indented tabs and spaces, like SEE them, Notepad can show spaces as 50% alpha red dots and red arrows for indents

---

### Post by tubasoldier on 2008-03-28
I think kate may have this option... It would have to be enabled if it does. I know that it at least shows where lines have not had a return. And it can be configured to show line numbers.

---

### Post by happyhamster on 2008-03-28
Gedit also has that ability. Open gedit, choose Edit-->Preferences-->Plugins and choose Draw Spaces. You can also set the color.

---

### Post by SBFC on 2008-03-28
And Scite..and host of others.

---

### Post by Jookia on 2008-03-30
> **happyhamster said:**
> Gedit also has that ability. Open gedit, choose Edit-->Preferences-->Plugins and choose Draw Spaces. You can also set the color.

I don't see it there.

---

### Post by happyhamster on 2008-03-30
> **Jookia said:**
> I don't see it there.
Then make sure gedit-plugins is installed:

sudo apt-get install gedit-plugins

---

### Post by noughtypixy on 2009-03-10
> **Jookia said:**
> How would I go about opening a file using Notepad2 in ubuntu? I have the exe.

open the .exe file it will launch with wine then use file ... open
 this works
havent figured out how to add it to the applications menue or the right click open with menue yet tho

---

