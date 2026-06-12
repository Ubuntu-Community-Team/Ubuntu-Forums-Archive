---
title: "[SOLVED] Can't change wine config"
date: 2008-01-21
forum: Wine
---

### Post by Greg Mueller on 2008-01-21
Under wine configuration

If you check the "Emulate a Virtual Desktop" at 640 x 480. I can't find a way to change it back. If I uncheck  "Emulate a Virtual Desktop" I can't scroll down to "Apply" (whatever) because the Wine Configuration box is taller that the
 Wine Desktop that it is in.

How can I change it back?

---

### Post by bodymind on 2008-01-21
you can remove the directory .wine on your home directory.... the file manager for default hides those files... just search on the menu how to show hidden files ;)

edit: i forgot to mention... when you remove this directory you will loose all the definitions of wine and the programs installed in wine ...

---

### Post by Greg Mueller on 2008-01-21
So there's no way to just uncheck "Emulate a Virtual Desktop" and hit <Ctrl> <something> and have it save it?

---

### Post by hikaricore on 2008-01-22
> wine explorer /desktop=1024x768 winecfg

You should be able to change any options this way.

^_^

This will only be a temorary fix, your main settiings will change when you change them.

---

### Post by Greg Mueller on 2008-01-22
<Uncheck box>
<Ctrl>+<Enter>

---

### Post by sethanath on 2008-09-09
Alt + Mouse Clicked works for me.

---

