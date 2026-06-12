---
title: "WOW wine hotkey problem"
date: 2008-03-21
forum: Wine
---

### Post by Findarato on 2008-03-21
Hello,

I have just managed to get wow working on wine (pretty easy after all) but there seems to be one bug which I can't solve. I am a druid and use the alt+f1-f4 keys to shapeshit, but at the moment, the ubuntu hotkeys are still associated with them.
Example: when I hit alt+f3 I get the desktop applet instead of shapeshifting into catform.

Any ideas / solutions?

Thank you very much for your time,

---

### Post by Findarato on 2008-03-22
anyone please?

---

### Post by Findarato on 2008-03-22
none here have a solution for this problem?

To be more accurate, I am running Ubuntu 7.10 and Wine 0.9.57

When I hit alt+f1, f2, f3 or f4, I get the "ubuntu shortcut" (which is the desktop applet for alt+f3) instead of the "wow shortcut" (which is shapeshifting)

---

### Post by MemoryDump on 2008-03-22
you are probably using compiz.. try disabling it before you start WoW. I often get that problem. Do a search for compiz-switch... it's a nice little app that toggles it for you.

---

### Post by Findarato on 2008-03-22
doesn't seem to fix it, when I hit alt+f3 I still get the desktop applet instead of shifting in catform.

---

### Post by Findarato on 2008-03-22
would be really nice if someone could give me a tip, as it's the only thing keeping me from playin now :(

---

### Post by MrShurr on 2008-03-23
You could just change the ubuntu keyboard shortcuts altogether:

System>Preferences>Keyboard Shortcuts

Along the right it lists the key combinations. Just highlight the ones you need to change (ALT + F1, for example) and change it. I suggest simply changing the ALTs to SHIFTs or CTRLs. :D

Hope that helps you. =]

David

---

### Post by Findarato on 2008-03-23
this helps for both alt+f1 and alt+f2, but alt+f3 (which launches the deskbar applet) isn't listed there :(

---

### Post by Findarato on 2008-03-25
ok, I managed to find a weird and hopefully temporary solution to the problem. I switch off compiz and use "killall -9 deskbar-applet" which simply kills it, so the f3 shortcut is free... :)

---

### Post by Repale on 2008-05-01
Start gconf-editor in terminal, then go to apps -> deskbar, change the keybinding from <Alt>F3 to something else, quit the editor, and restart the machine.

---

