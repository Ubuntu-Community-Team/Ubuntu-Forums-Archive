---
title: "Can I give a wine run program access to the clipboard? It's for a Game."
date: 2007-08-02
forum: Wine
---

### Post by Drezliok on 2007-08-02
I am playing Utopia from this website. [http://games.swirve.com/utopia/](http://games.swirve.com/utopia/)

I use a helper program from another site called UtopiaAngel, it watches the windows clipboard for text copied from the game and loads it into it's self and formats it.

The program runs but doesn't have access to Xfce's "clipboard".

Anyone here know how to do that?

---

### Post by tkrisz on 2007-12-31
I have the same problem.

---

### Post by Drezliok on 2008-01-01
I swiched to Gnome. Can this be done in gnome too?

---

### Post by RC Howe on 2008-01-01
I can copy/paste text from gedit to wine's notepad and vis versa just fine (Wine 0.9.46). Perhaps the game uses a custom pasteboard type, or wine is not properly sending the observer the message.

The [Wine App Database]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=531") says it's usable, but that > one must turn on/off the "Monitor Clipboard" option to read the clipboard. Try turning on/off the monitor clipboard option.

---

### Post by tkrisz on 2008-01-03
I've searched for a solution, too, and found that as well. It is not helping for me.
Btw, I can copy to notepad, too, by Ctrl+C Ctrl+V (not by the middle mouse button. Offtopic question: is there a way to costumize the behaviour of the middlebutton pasting in Ubuntu?).
(Ubuntu 7.04, Gnome, 32-bit)

I've found this: make a file ~/.wine/config and put there
```

WINE REGISTRY Version 2
[Clipboard]
"ClearAllSelections" = "1"
"PersistentSelection" = "0"
"UsePrimary" = "1" 

```
But did not help either. Is there a config file of wine somewhere that i can try to edit? The search tool did not find any.

---

### Post by RC Howe on 2008-01-03
There may be a clipboard section in Wine's registry, try entering "wine regedit" in a console. Search for clipboard or for the program's name. Try entering your code there as registry keys.

---

