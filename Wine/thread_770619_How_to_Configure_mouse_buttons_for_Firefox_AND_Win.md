---
title: "How to: Configure mouse buttons for Firefox AND Wine in 8.04"
date: 2008-04-27
forum: Wine
---

### Post by sephiros9883 on 2008-04-27
**Affected:**
Ubuntu Hardy 8.04 final, Firefox3 beta 5, Wine 0.9.60

**Problem:**
Out the box, the thumb mouse buttons don't work in wine. When editing the xorg.conf file, you can make it work in wine but it breaks back and forward in Firefox.

**Assumptions:**
You have a 7 buttons mouse (right click, left click, middle click, scroll down, scroll up, back and forward).

**Solution:**
Edit your xorg.conf file
```
sudo gedit /etc/X11/xorg.conf
```
Replace the InputDevice section by the following lines:
```

Section "InputDevice"
       Identifier      "Configured Mouse"
       Driver          "mouse"
       Option          "Buttons"       "7"
       Option          "ZAxisMapping"  "4 5"
       Option          "ButtonMapping" "1 2 3 6 7"
EndSection

```
The configuration found [here]("http://ubuntuforums.org/showpost.php?p=4813211&postcount=3") has been reported to work

Save and _restart X server_(save all your current work and press ctrl + alt + bckspace)

log back in

Execute xev in a terminal:
```
$ xev
```
Make sure your back and forward buttons are binded to 6 and 7. you may have to play with the above xorg config.

Start Firefox

In the url bar, type:
```
about:config
```

Change those options for the indicated values:

```
mousewheel.horizscroll.withnokey.action = 2
mousewheel.horizscroll.withnokey.numlines = -1
mousewheel.horizscroll.withnokey.sysnumlines = false

```

That's it, Back and forward should work in firefox and wine should recognize those buttons as mouse 4 and mouse 5.

Let me know if it worked for you or if you needed to change the xorg.conf!

---

### Post by schtufbox on 2008-04-27
xev shows my side buttons as being button 8 and 9
I already had my xorg.conf as you have above and it works fine in firefox, just not in wine.
However, if I change the buttonmapping to "1 2 3 8 9" it still works in firefox, and still does not work in wine.
My mouse is a Logitech MX518
and the mouse section of my xorg.conf is as follows:
```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "vmmouse"
    Option "Device" "/dev/input/mice"
    Option "Protocol" "ExplorerPS/2"
    Option "Emulate3Buttons" "false"
    Option "Buttons" "7"
    Option "ZAxisMapping" "4 5"
    Option "ButtonMapping" "1 2 3 8 9"
EndSection
```

As I said, even with buttonmapping saying "1 2 3 6 7" I get exactly the same results.
Any ideas? this has been bugging me for a while :P

---

### Post by schtufbox on 2008-04-27
I fixed it. You sir, are great.
I remembered some other post about this, where someone could get it to work in wine OR firefox by enabling Option "CorePointer"
For me, it just made it not work in either...

However, I changed my xorg.conf to the below, did your about:config changes and now it works!
Thanks, this has been bugging me for ages :)

New xorg.conf
```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "vmmouse"
    Option "Device" "/dev/input/mice"
    Option "Protocol" "ExplorerPS/2"
    Option "CorePointer"
    Option "Emulate3Buttons" "false"
    Option "Buttons" "7"
    Option "ZAxisMapping" "4 5"
    Option "ButtonMapping" "1 2 3 6 7"
EndSection

```
basically it was adding the CorePointer  option and your firefox changes.
Thanks.

---

### Post by sephiros9883 on 2008-04-27
Actually trying your 1st xorg config broke my tweak too!
If you want a cleaner xorg.conf try this

```
Section "InputDevice"
       Identifier      "Configured Mouse"
       Driver          "mouse"
       Option          "Buttons"       "7"
       Option          "ZAxisMapping"  "4 5"
       Option          "ButtonMapping" "1 2 3 6 7"
EndSection
```

It should work. Let me know!

---

### Post by K_T on 2008-06-08
> **sephiros9883 said:**
> Actually trying your 1st xorg config broke my tweak too!
If you want a cleaner xorg.conf try this

```
Section "InputDevice"
       Identifier      "Configured Mouse"
       Driver          "mouse"
       Option          "Buttons"       "7"
       Option          "ZAxisMapping"  "4 5"
       Option          "ButtonMapping" "1 2 3 6 7"
EndSection
```

It should work. Let me know!
This modification made the backward and forward buttons of my mx518 to work with firefox (in Hardy). I did not have to edit the about:config. :guitar:

---

### Post by Gauge on 2008-06-14
> **sephiros9883 said:**
> Actually trying your 1st xorg config broke my tweak too!
If you want a cleaner xorg.conf try this

```
Section "InputDevice"
       Identifier      "Configured Mouse"
       Driver          "mouse"
       Option          "Buttons"       "7"
       Option          "ZAxisMapping"  "4 5"
       Option          "ButtonMapping" "1 2 3 6 7"
EndSection
```

It should work. Let me know!

This is exactly what I was looking for, thank you so much, you have no clue how long I looked for a simple working fix.

---

### Post by Garf on 2008-06-27
The problem that I have is that I had the buttons working as I needed them in firefox 2 (back and forward)... But in firefox 3 they don't work...

Here is the part of my xorg...

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Buttons"	"7"
	Option		"ButtonMapping"	"1 2 3 6 7"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"false"
EndSection
```

---

