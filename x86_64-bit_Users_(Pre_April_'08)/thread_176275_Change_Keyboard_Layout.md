---
title: "Change Keyboard Layout"
date: 2006-05-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by dreadbiscuit on 2006-05-14
I need to be able to type some German and French characters and I'm having trouble. I've changing my keyboard layout to French, for example, but I'm running into problems because my USB Macintosh keyboard seems to lack some of the extra keys I need. 

Is there anyway to setup a custom layout? I would like to have the normal USA layout, and then a secondary layout that replaces the number keys across the top of my keyboard with the additional characters that I need.

In short, is there a simple way to program my keyboard so that when I press "1" I get a U-Umlaut instead?

---

### Post by ssam on 2006-05-14
i think the program xmodmap may be able to do what you want.

---

### Post by dreadbiscuit on 2006-05-14
Thanks. xmodmap seems to be the way to go. While trying to learn how to use it, I accidentally made my "v" key worthless. I was able to fix it, but I'm reluctant to mess with it further. If I make changes with xmodmap in Terminal, are these changes saved or do I have to make the changes in a config file somewhere?

---

### Post by pindar on 2006-05-15
You will have to save your changes to a file; this file will have to be loaded every time you start the X server (in Gnome, you will be asked the first time if you want the file to be loaded, after that, it's done automatically). The easiest way to get a working file, AFACS, is this: 

1. In terminal, run this command: 
xmodmap -pke > .Xmodmap
This will print the current layout, in proper format, to a file named ".Xmodmap." 

2. Open this file in an editor and see how the syntax works. Add keys and characters to your heart's content. Save file, place it in your ~ directory.

3. To test the configuration you created, run 
xmodmap .Xmodmap

If you're really clumsy, you could manage to make your keyboard unusable. But you can always delete the file and restart the Xserver.

HTH

---

