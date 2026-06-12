---
title: "Script for WoW"
date: 2008-05-29
forum: Wine
---

### Post by Mauler5858 on 2008-05-29
I am extremely new to scripts, and i need to know how to create one to fit my need.

I need to be able to write a script to:

disable compiz fusion
launch world of warcraft
upon closing re-enable compiz if possible

Many thanks in advance.

---

### Post by Zorael on 2008-05-29
```
#!/bin/bash

metacity --replace &
wine *<path to wow executable>*      # or similar Cedega command, depending on what you use
compiz *<any extra compiz arguments you use>* --replace &
```

Extra compiz arguments would include [FONT="Courier New"]--ignore-desktop-hints[/FONT] for KDE users, [FONT="Courier New"]--loose-bindings[/FONT] if nvidia videocard, [FONT="Courier New"]--indirect-rendering[/FONT] if Intel/similar cards, etc.

Mind the ampersands (&); you want them after the metacity and compiz lines, but not after the wine line.


If you use fusion-icon, make it this instead.
```
#!/bin/bash

**killall fusion-icon**
metacity --replace &
wine *<path to wow executable>*      # or similar Cedega command, depending on what you use
**fusion-icon &**
```

---

### Post by Mauler5858 on 2008-05-29
So in my case it would be:
```

#!/bin/bash

metacity --replace &
wine /home/<username>/.wine/drive_c/Program Files/World of Warcraft/launcher.exe

compiz <any extra compiz arguments you use> --replace &


```

For the extra compiz arguements part.  Can you elaborate on that.  All i know about compiz is the options i set at the gui.

---

### Post by Zorael on 2008-05-29
You may want to encase the wow.exe path between quotes to make sure it handles the spaces correctly.

As for the compiz arguments, you usually needn't worry. If you're running [COLOR="DeepSkyBlue"]KDE[/COLOR], be sure to add [COLOR="DeepSkyBlue"]--ignore-desktop-hints[/COLOR] to avoid getting 16x16 desktops when you only want 4x1 for a cube. If you're using [COLOR="SeaGreen"]Nvidia[/COLOR], you can add [COLOR="SeaGreen"]--loose-binding[/COLOR] to get better performance but chance of tearing. If you're using an [COLOR="Orange"]Intel integrated chipset[/COLOR] (and perhaps of other similar makes), I think you should add [COLOR="Orange"]--indirect-rendering[/COLOR] to get proper performance.

On my Nvidia laptop, I used the following command until I started using fusion-icon and let it do it for me.
```
$ compiz [COLOR="DeepSkyBlue"]--ignore-desktop-hints[/COLOR] [COLOR="SeaGreen"]--loose-binding[/COLOR] --replace &
```

The only really necessary argument is --replace (and the ampersand). The others are optional.

---

### Post by Mauler5858 on 2008-05-29
```
 $ compiz  --loose-binding --replace &
```

Looks like it will be the way to go for me.  I have an Nvidia card, and i am using Gnome.  I will try it when i get home from work tonight.

---

### Post by Sammi on 2008-05-30
> **Mauler5858 said:**
> ```

#!/bin/bash

metacity --replace &
wine /home/<username>/.wine/drive_c/Program Files/World of Warcraft/launcher.exe

compiz <any extra compiz arguments you use> --replace &


```

Use this:
```
wine "C:\Program Files\World of Warcraft\launcher.exe"
```Instead of this:
```
 wine /home/<username>/.wine/drive_c/Program Files/World of Warcraft/launcher.exe
```As it makes Wine set the working directory correctly.

---

### Post by Mauler5858 on 2008-05-30
I made my script file with the following:

```

#!/bin/bash

metacity --replace &
wine wine "C:\Program Files\World of Warcraft\launcher.exe"     
compiz  --loose-binding --replace & 

```

Made it executable with:

```

chmod 0755 <scriptname>

```

And when i executed it, the screen flashed a second and nothing happened.  I checked and compiz wasnt disabled.  Anything i am missing?

---

### Post by Zorael on 2008-05-30
> **Mauler5858 said:**
> I made my script file with the following:

```

#!/bin/bash

metacity --replace &
**wine wine** "C:\Program Files\World of Warcraft\launcher.exe"     
compiz  --loose-binding --replace & 

```
One **wine** too many. :>
```
**wine** "C:\Program Files\World of Warcraft\launcher.exe"
```
The path (C:\Program Files, etc) needs to be the same as the path in wine's C: drive. For instance, I sure didn't install it there (though I imagine it may be the default location), opting for "C:\Games\WoW" instead.

Run '[FONT="Courier New"]wine explorer[/FONT]' to explore that C: drive. (Make sure to choose C: there up top.)

---

### Post by Mauler5858 on 2008-05-30
ah i see that now with the double wines lol.  And the path is correct.  I allowed it to 100% mimic the windows directory structure.  Thanks

---

