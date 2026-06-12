---
title: "problems, ubuntu -&gt; kubuntu"
date: 2005-11-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by dpdt1 on 2005-11-13
hi there,
 
before reading this, i just want to say i had ubuntu installed and none of these 2 were a problem. 
since i installed kubuntu-desktop (kdm default), i noticed these "minor" problems below :

1) sudo chmod/chown dont seem to work in kubuntu.

2)when i first installed ubuntu and added greek layout to the keyboard, i adjusted switch button to be "alt+shift" and that worked fine. then i installed kubuntu (i like kde more) and although i changed the layouts just like i did in gnome, the switch button doesnt work anymore. 
i can only switch by mouse-clicking on top of the flag in the tray. 
that's annoying when writing a big text using both languages.

i suspect it's a permissions thing but i dont know how to fix it. 
(i just quited windoze)

any suggestions much appreciated, 

Dimitris

---

### Post by ksenos on 2005-11-23
You might like to take a look to the /etc/X11/xorg.conf file. There should be a section describing the keyboard and should look something like this.

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us,el"
        Option          "XkbOptions"    "grp:alt_shift_toggle"
EndSection
```

Hope it helps ;)

---

### Post by Ribs on 2005-11-24
[QUOTE=dpdt1]1) sudo chmod/chown dont seem to work in kubuntu.[/QUOTE]
Could you expand on this? What error do you get? What commands have you tried?

---

### Post by jyhelle on 2005-11-27
[QUOTE=dpdt1]
1) sudo chmod/chown dont seem to work in kubuntu.
[/QUOTE]
by the number of times I have used these, they must be working perfectly here ;)
do they report something, or simply end without action ?

---

### Post by dpdt1 on 2005-11-27
ksenos, thanks for the help. i'll try it now. 

for the rest of you guys i'm sorry, but sudo chmod/chown plays well. consider that my mistake.

thanks everyone.

---

