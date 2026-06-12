---
title: "is there anything like this app?"
date: 2006-04-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by xinix on 2006-04-02
[http://chezjd.free.fr/Creation/logiciel.php?sign=Sprk&lang=2](http://chezjd.free.fr/Creation/logiciel.php?sign=Sprk&lang=2) (spark).

It lets you define what key combinations do what on your computer.  If I wanted to eject a usb thumbdirve by pressing Ctrl+Alt+Eject.  Spark could do it by setting the key combo to run a script that did that for me.  Any thing like this on the Linux side?

-r

---

### Post by Aphorism on 2006-04-02
System -> Preferences -> Keyboard Shortcuts

Built right in... :)

---

### Post by xinix on 2006-04-02
Keyboard Shortcuts is too limited in terms of what you can actually do.   It's more like a list of pre-defined functions/events that we can assign a key to launch.  You can't change the default media player.  At least not without a work around like renaming the rythembox binary and placing a script called "rhythembox"  in it's place.  I'm looking for something that lets you set whatever-key/combo you want to launch whatever app/script you want.  Say like pressing F12 and ejecting your mp3 player.

---

### Post by ssam on 2006-04-02
you should be able to asign keyboard short cuts to commands using gconf-editor (atl+F2 and put in its name to run it).

then go to apps -> metacity

between global_keybindings and keybinding_commands you should be able to do what you need.

i think there are lower level ways of doing it but i dont know what the program is called.

---

