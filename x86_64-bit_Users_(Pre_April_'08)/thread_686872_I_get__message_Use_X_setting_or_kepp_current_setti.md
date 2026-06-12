---
title: "I get  message Use X setting or kepp current settings I would like that gone"
date: 2008-02-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Lukasz Tarkowski on 2008-02-03
Dear Support
I get a window message Use X settings and Keep Current gnome settings how can I disable that?
It happens after login

---

### Post by coram deo on 2008-02-03
I had the same message.  I went into System-Preferences-Keyboard    
Then locate your keyboard, or the closest match, under Layouts (Choose...)
That should stop the message!

---

### Post by Yellow Pasque on 2008-02-04
Open terminal and type:
```
gconf-editor
```
Pull down /desktop/gnome/peripherals/keyboard and click on the kbd folder. Right click on the keys and select 'Unset Key'. Check the overrideSettings box. Problem solved. Now Gnome will play nice with X regardless of what X chooses for a keyboard layout.

---

