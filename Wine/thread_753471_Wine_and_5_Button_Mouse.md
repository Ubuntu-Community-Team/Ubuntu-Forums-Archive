---
title: "Wine and 5 Button Mouse"
date: 2008-04-12
forum: Wine
---

### Post by schtufbox on 2008-04-12
How do I get Wine to recognise the thumb buttons on my mouse?
They work fine in firefox etc just not picked up by any games in wine when I try setting them as a key etc in a game, like Tabula Rasa etc.

I'm sure they worked about 2 years ago in WoW, which is when I last used Linux (until recently, I'm now 100% linux as all 3 of my PC's are running Hardy :D ) 
Here's the mouse entry in my xorg.conf 
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "vmmouse"
    Option "Protocol" "ExplorerPS/2"
    Option "Emulate3Buttons" "false"
    Option "Buttons" "7"
    Option "ZAxisMapping" "4 5"
    Option "ButtonMapping" "1 2 3 6 7"
EndSection
```
any ideas? do I need to add something else?

---

### Post by sephiros9883 on 2008-04-13
I have the exact same problem. Try to add ```
option "CorePointer"
``` and it will work in wine...but will be broken in firefox....it's driving me mad! ](*,)

---

### Post by schtufbox on 2008-04-14
Nope, that made no difference to wine, the thumb buttons still do nothing :D  As a bonus that stopped them working in firefox too, si I had to remove that line

---

### Post by sephiros9883 on 2008-04-14
Now that&#347; pretty annoying.... he is my config:
```
Section "InputDevice"
Identifier "Configured Mouse"
Driver "vmmouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Buttons" "7"
Option "ButtonMapping" "1 2 3 6 7"
EndSection
```

This one works in Wine (.59) and Hardy Heron, but breaks FF.
comment CorePointer and it will be vice versa: won work in wine but will work in FF.

Im using a Logitech mx518.

I didn't upgrade to kernel 24-16 yet...

---

### Post by sephiros9883 on 2008-04-17
anything new on this front? I successfully managed to make firefox work with CorePointer enabled.....except it doesn work with wow.... I hate i have to choose between FF or WoW!!!!

my last try at xorg.conf (back forward working in FF, not in Wine):

```
Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "Buttons" "7"
Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 2 3 8 9"
EndSection 
```:

---

### Post by sadris on 2008-04-22
I am fairly certain that Wine doesn't support more than 3 buttons as if you run Ventrillo then go to setup and have it detect all button presses, it only grabs up to Mouse Button 3.

Has anyone experienced differently?

---

### Post by sephiros9883 on 2008-04-22
I made it work. the problem is that if i make it work in Wine, it breaks Firefox :P (8.04)

---

### Post by sadris on 2008-04-22
What I did was that I remapped mouse buttons 4 and 5 with IMWheel


~/.imwheelrc
```
"^World of Warcraft"
None,Thumb1,Alt_L|F11
None,Thumb2,Control_L|F11
```

In wow I have a macro placed in a button which has a keybinding of F11:

```
/cast [mod:alt,target=mouseover] Abolish Poison
/cast [mod:ctrl,target=mouseover] Remove Curse
```

It's not the same thing but it accomplishes it. However it would still be good to figure out how to get wine to support buttons 4/5.

---

