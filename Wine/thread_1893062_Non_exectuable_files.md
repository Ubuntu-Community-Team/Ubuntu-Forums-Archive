---
title: "Non exectuable files"
date: 2011-12-09
forum: Wine
---

### Post by Agent26 on 2011-12-09
Hi all,
I am now almost there with my linux systems, i've got Xubuntu 10.4.2 on my desktop as the main system and on my laptop i've got the Wubbi install withing windows. The more I use linux the more I want to earase windows for good.

I have 2 last probs that i want to sort out and then i'm fine to just play around seeing terminal in action.

Not that I really want to open many exe windows files but it would be handy in the odd occasion should needs be.

There is a technique for Ubuntu  but it's a bit different on Xubuntu as there is no small checkbox in the permissions when right clicking the exe's so i'm now stuck.

Would anyone be able to help and send me in the right direction please. I need to mark the exe's as executable.
Thankyou

---

### Post by BC59 on 2011-12-09
Follow the instructions from here:

[http://www.youtube.com/watch?v=9GTwpf81dWY](http://www.youtube.com/watch?v=9GTwpf81dWY)

---

### Post by Morbius1 on 2011-12-09
Wine itself does not care and cannot determine if a given file has a Linux executable bit set.

Open up thunar as root:
```
gksu thunar /usr/share/applications
```Right click on the Wine program loader and select Properties > Launcher.

In the Command window you will see this entry:
```
cautious-launcher %f wine start /unix
```Change it to this:
```
wine start /unix
```It's "cautious-launcher %f" that's the problem.

BTW, the same thing happens when you try to run a java jar file and the fix is the same with it's program loader.

---

### Post by Agent26 on 2011-12-09
Hi, thanks for the fast responce guys, Thats that problem sorted with no fuss atal.
Thankyou very much for the help, I shall mark this solved!

---

