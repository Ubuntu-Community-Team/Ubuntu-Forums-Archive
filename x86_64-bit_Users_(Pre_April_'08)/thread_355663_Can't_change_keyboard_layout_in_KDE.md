---
title: "Can't change keyboard layout in KDE"
date: 2007-02-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by mikerobinson on 2007-02-07
I like to switch between Spanish and English keyboard layouts to get all those accent characters, but when I go to System Settings > Regional and Language > Keyboard Layout the list of keyboard layouts is blank, however in Gnome I can switch to Spanish. How can I switch to a Spanish keyboard in KDE?

I'm running x86_64 Edgy 6.10 kubuntu on 64-bit AMD processor if it makes any difference.

---

### Post by tedrogers on 2007-02-08
No idea....i have a similar issue....but check here for a possible solution if someone provides one.

[http://ubuntuforums.org/showthread.php?t=309424&highlight=kubuntu+regional+settings](http://ubuntuforums.org/showthread.php?t=309424&highlight=kubuntu+regional+settings)

---

### Post by MasterOfMuppets on 2007-02-11
I'm one step ahead of you guy, but only one step... I can switch from English to Hebrew using alt+ctrl+k (default in KDE) but not from Heb to Eng.
I tried turning sticky switching on, but it resets itself every time! O_O

---

### Post by pingvin on 2007-03-04
Just found what I think would fix your problem - only now I can't find the thread again to make a link to it!
Oh well, here is the advice I found which seems to be working for me:
Copy the contents of /etc/X11/xkb
to /usr/share/X11/xkb
then logout out and back in, and go to kcontrol to choose layouts. Only thing that doesn't work is the keyboard shortcut to change between layouts, but I'll live. There's a cool little country flag for each layout in the system tray and it can remember layouts for individual apps or windows.
If anyone does find the original thread, please thank whoever wrote it, because they have saved me hours!

Mike

---

### Post by izi on 2007-03-20
See a possible solution at

[http://www.linuxquestions.org/questions/showthread.php?p=2677109#post2677109](http://www.linuxquestions.org/questions/showthread.php?p=2677109#post2677109)

I'm copying for your convenience:

(quote)
Hi there !

I think I've managed to find a solution that doesn't require global changes, scripts or installations (works in Kubuntu 6.10):

1. In the Regional & Language Add the needed layout, disable xkb options

2. Close any language / keyboard settings windows

3. Edit the file ~/.kde/share/config/kdeglobals
Look for the line:
Switch to Next Keyboard Layout=Alt+Ctrl+K
And change to:
Switch to Next Keyboard Layout=Alt+Shift_L;Alt+Shift_R
This will enable layout changes for both alt+shift (left and right) like in windows. You cal eliminte one if you'd like.

4. Open "Keyboard & Mouse", choose "Keyboard shortcuts", and make sure the correct shortcuts appear (they should).

5. Either restart KDE or just change some random keyboard shortcut (and change back) - Just as long as the "apply" button goes active.
6. Press "apply"

Cheers

NOTE: I've only discovered it today and haven't checked for long term effects / damage... I'd appreciate some feedback

(end quote)

---

### Post by izi on 2007-03-20
And a possible script from 

[http://www.linuxquestions.org/questions/showthread.php?p=2677514#post2677514](http://www.linuxquestions.org/questions/showthread.php?p=2677514#post2677514)

> 
```

cp ~/.kde/share/config/kdeglobals ~/.kde/share/config/kdeglobals.old
sed -e 's/Alt+Ctrl+K/Alt+Shift_L;Alt+Shift_R/g' ~/.kde/share/config/kdeglobals.old > ~/.kde/share/config/kdeglobals 
```

NOTE! If you've already changed the keyboard shortcut from ALT+Ctrl+K don't forget to change it in the script...

You may have to re-"apply" your keyboard shortcuts as I've writtem before: Change some random keyboard shortcut (and change back) - Just as long as the "apply" button goes active. Press "apply".

What you achieve is a GNOME-like functionality - ALT+Shift changes language (and the indicator)

Cheers :D


---

### Post by Keymone on 2007-03-24
i solved problem simply turning off switching keyboard layouts in Settings / Regional & Accessibility / Keyboard Layout and editing /etc/X11/xorg.conf

there in "Generic Keyboard" or whatever you use specify layouts and switch method

here is my block:

    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us,ua(winkeys)"
    Option         "XkbOptions" "grp:ctrl_shift_toggle"
    Option         "XkbVariant" "base"

i changed only last 3 lines

---

### Post by favio on 2007-03-31
This solution really works:
I just have replaced "en" for "es", then i save changes (using a text editor) and now it works fine. I can use the "ñ" without problems!!

File: /etc/X11/xkb/xkbcomp 

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"es"
EndSection

spanish comments:
La solución que había propuesto alguien de por ahí funcionó. Ahora la ñ funciona.
Sin importar que en la configuración del sistema diga que no hay ningun keyboard layout.
Quiero aclarar que por ahí encontré alguien que proponia reconfigurar el xorg server o algo así, pero yo lo hize y no me iniciaba la parte visual del kubuntu!! Me iniciaba desde consola. Por suerte antes de meter mano había hecho un backup del archivo que arriba mencioné.
Asi que recomiendo que también lo hagan.
Una última cosa: cuando vayan a editar el archivo (por ejemplo con el kate), les va a decir que es un archivo binario y que bla bla, pero en realidad es un archivo de texto (como van a notar), así que recomiendo ignorar el mensaje.

Saludos,
Favio

---

### Post by favio on 2007-03-31
Im Favio again. I post the previous message. I had an error in line:  "File: /etc/X11/xkb/xkbcomp ".
The file to modify is "/etc/X11/xorg.conf  "

----Original Message-----
This solution really works:
 I just have replaced "en" for "es", then i save changes (using a text editor) and now it works fine. I can use the "ñ" without problems!!
 
 File: /etc/X11/xorg.conf (corrected ;)
 
 Section "InputDevice"
 Identifier "Generic Keyboard"
 Driver "kbd"
 Option "CoreKeyboard"
 Option "XkbRules" "xorg"
 Option "XkbModel" "pc104"
 Option "XkbLayout" "es"
 EndSection
 
 spanish comments:
 La solución que había propuesto alguien de por ahí funcionó. Ahora la ñ funciona.
 Sin importar que en la configuración del sistema diga que no hay ningun keyboard layout.
 Quiero aclarar que por ahí encontré alguien que proponia reconfigurar el xorg server o algo así, pero yo lo hize y no me iniciaba la parte visual del kubuntu!! Me iniciaba desde consola. Por suerte antes de meter mano había hecho un backup del archivo que arriba mencioné.
 Asi que recomiendo que también lo hagan.
 Una última cosa: cuando vayan a editar el archivo (por ejemplo con el kate), les puede decir que es un archivo binario (a pesar de que es un archivo .conf) y que bla bla, pero en realidad es un archivo de texto (como van a notar), así que recomiendo ignorar el mensaje.
 
 Saludos,
 Favio

---

### Post by nawingolf on 2007-04-07
> **MasterOfMuppets said:**
> I'm one step ahead of you guy, but only one step... I can switch from English to Hebrew using alt+ctrl+k (default in KDE) but not from Heb to Eng.
I tried turning sticky switching on, but it resets itself every time! O_O

   If you haven't figure this out already, try reading the manual on "The Kxkb Handbook" chapter 4 (trouble shooting).
   It basically tell you that if you use layout of another language like Hebrew, Thai, or other languages that has a different layout.  Using shortcut with the letter 'K' won't work.  because the 'K' key does not mean k in other languages. (althought it is in latin , that's why it's a default)
    So basically you just need to change from Ctrl+Alt+K to Ctrl+Alt+Space or other common key like Shift or Tab.

Good luck, and POWER TO THE PEOPLE (not Bill Gate). LOL

---

### Post by mrli on 2007-04-21
Had the exact same problem, editing xorg.conf did't helped, but following izi's suggestion DID !
Thank you very much, doing very fine with three different layouts !

---

