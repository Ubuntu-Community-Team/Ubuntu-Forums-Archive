---
title: "Keyboard not working in wine with warcraft 3"
date: 2007-09-16
forum: Wine
---

### Post by stoked1 on 2007-09-16
Dell 1501 and the keyboard works fine all other times, but when im trying to play warcraft 3 in wine it doesnt want to work.  However if i leave *emulate a virtual desktop* checked it works but will no go full screen and makes scrolling across the map with the mouse a problem.  So could someone please help me get the keyboard working with that option unchecked so i can play in full screen.  

Thanks

---

### Post by L0CU5T on 2011-03-28
Hi, there is a solution... Keep your wine settings, as you have them now (emulating desktop).

Open your terminal and go to warcraft 3 directory (using "cd" command).

once there, type:
"wine war3.exe -opengl"

And enjoy fullscreen warcraft 3 with keyboard working :-)

I hope, it was helpfull...

---

### Post by SavvasKatseas on 2011-11-15
Thanks L0CU5T, your solution worked just fine on my desktop running 11.10/64. I've changed the menu link too, replacing the default command with this one and I no longer need to use the terminal either :)

---

