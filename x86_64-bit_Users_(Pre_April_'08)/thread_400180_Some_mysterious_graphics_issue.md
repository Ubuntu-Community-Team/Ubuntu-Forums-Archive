---
title: "Some mysterious graphics issue"
date: 2007-04-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by morequarky on 2007-04-03
1. unsure what happened leading up to number 2.
2. motherboard died
3. too busy to change motherboard, months went by.
4. fixed motherboard, with same model/bios version
5. have not put in the old GForce2 MX200 graphics card, found in the trash, so using on board graphics, which is fine, cause I don't need any fancy graphics.(
6. XP64 PRO boots fine.
7. GRUB is installed and seems to work.
8. Booting Linux seems to start.  Seems to find the kernel and does get me to a prompt, but that is it.  unsure of the proper way to start 'x', but whatever it is, gnome throws some error and the whole screen complains about some graphics issue.

Gnome seems to try to start, but due to the graphics issues, it just doesn't work.

I don't know how to fix it.

Never had any graphics issues with the old motherboard(same motherboard as now.)

I am typing to you from XP pro64.  on the very computer I can't boot to Ubuntu.

Can some one direct me to the proper files to show you and fix the error?  Do I need to reinstall. :(  not again :(   I am sick of re-installing Ubuntu.  And the re-install is rarely my fault or Ubuntu's fault.

:D

---

### Post by renzokuken on 2007-04-03
let it boot to ubuntu and let it fail, then press Ctrl+Alt+F1 to get to a terminal screen.

since this sounds like a grafix problem you should check your xorg.conf, so log in and type

```
sudo nano /etc/X11/xorg.conf
```

have a look at the **Section   "Device"** part and see what driver it is using. could be using the wrong one. 

one option would be to change it to the "vesa" driver which is pretty failsafe.

so change your section from this (you can ignore whatever is in the identifier line, its not important)

```

Section   "Device"
        Identifier     "grafix card/chipset name"
        Driver         "nv"     [color=red]#this could be a whole host of things other than nv[/color]
End Section

```

to this

```

Section   "Device"
        Identifier     "grafix card/chipset name"
        Driver         "vesa"     [color=red]#change this line[/color]
End Section

```

save and exit the file by pressing Ctrl+X, Y then enter.

reboot using

```
reboot
```

and see what happens

---

### Post by morequarky on 2007-04-03
> **renzokuken said:**
> let it boot to ubuntu and let it fail, then press Ctrl+Alt+F1 to get to a terminal screen.

since this sounds like a grafix problem you should check your xorg.conf, so log in and type

```
sudo nano /etc/X11/xorg.conf
```

have a look at the **Section   "Device"** part and see what driver it is using. could be using the wrong one. 

one option would be to change it to the "vesa" driver which is pretty failsafe.

so change your section from this (you can ignore whatever is in the identifier line, its not important)

```

Section   "Device"
        Identifier     "grafix card/chipset name"
        Driver         "nv"     [color=red]#this could be a whole host of things other than nv[/color]
End Section

```

to this

```

Section   "Device"
        Identifier     "grafix card/chipset name"
        Driver         "vesa"     [color=red]#change this line[/color]
End Section

```

save and exit the file by pressing Ctrl+X, Y then enter.

reboot using

```
reboot
```

and see what happens

I'll Try THAT.

---

### Post by morequarky on 2007-04-04
Absolutely fantastic....it didn't even reboot.  It took the change so fast.  Thanks

---

### Post by renzokuken on 2007-04-04
no probs, glad it worked. the chances are your old install recognised your nvidia card and was using the "nv" driver.

even though you removed the nvidia card your xorg doesnt know this so it was still using "nv" so when it couldnt find it it didnt work. you have to tell it to use a different driver yourself, and vesa is most widely compatible and arguably stable driver there is

happy ubunting!

---

