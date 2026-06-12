---
title: "Wine - keyboard input not working on virtual desktop"
date: 2008-06-28
forum: Wine
---

### Post by javbuntu on 2008-06-28
Wine: 0.9.59  (from Ubuntu's repository)
Linux: Ubuntu 8.0.4
Keyboard:  HP , PS/2 . I never had to install any special driver on Windows or Linux. It is recognized automatically always except by Wine Virtual Desktop.



My keyboard doesn't work within the Wine Virtual Desktop but it works on other Linux consoles/apps.  I have been going through the forums and trying different workarounds,  but nothing works for me yet... any ideas?


If I don't configure the Virtual Desktop, my keyboard works fine with the Wine applications.

---

### Post by yevgeni on 2008-11-18
I have to second that. When using virtual desktop and trying to type... no dice.

---

### Post by jyaan on 2008-11-21
I have had this problem for quite some time as well, and haven't seen any solutions anywhere. Keyboard input works fine without virtual desktop enabled. Once enabled, the title bars do not seem to focus (stays grey, noticed it turned blue when I tried clicking "About WINE", but input is still not working) no matter where I click, and even when there is a text input box with flashing cursor in it. 

I am generally able to enter a single character, and then I can't enter anything else. If it is in a game, the single key I entered appears to be held down (maybe a key up event is failing??), so a character would continue moving forward if I pressed the up arrow key. I use dvorak keyboard layout with a simple qwerty usb keyboard (Logitech Classic), and I change to Qwerty layout for certain games with setxkbmap. I have compiz enabled, but disabling it didn't seem to change anything.

Considering that enabling a virtual desktop is one of the ways to make many apps work with WINE, this is a rather large handicap to not be able to use it at all.

---

### Post by jyaan on 2008-11-21
Good news -- I believe I have found a solution. Hopefully you are all using SCIM, and this is why the input does not work. The workaround for this is to simply set the XMODIFIERS variable to '' when launching WINE.

```
XMODIFIERS='' wine myapp.exe
```

For .desktop application launcher files, you should edit them as follows, using the 'Properties' menu by right clicking and editing the 'Command' section: 

```
env XMODIFIERS='' WINEPREFIX="/home/jyaan/.wine" wine "C:\DeusEx\System\DeusEx.exe"
```

I hope this works for you guys. Good luck.

---

### Post by louskrad on 2009-01-17
> **jyaan said:**
> Good news -- I believe I have found a solution. Hopefully you are all using SCIM, and this is why the input does not work. The workaround for this is to simply set the XMODIFIERS variable to '' when launching WINE.

```
XMODIFIERS='' wine myapp.exe
```

For .desktop application launcher files, you should edit them as follows, using the 'Properties' menu by right clicking and editing the 'Command' section: 

```
env XMODIFIERS='' WINEPREFIX="/home/jyaan/.wine" wine "C:\DeusEx\System\DeusEx.exe"
```

I hope this works for you guys. Good luck.

Thanks jyaan, I was having the same problem and browsing the forums saw your solution. It works perfectly.

---

### Post by sumwonyuno on 2009-01-23
Thank you very much, I've been looking for an answer for this problem for months.

---

### Post by lamborghiniwang on 2009-03-12
> **jyaan said:**
> Good news -- I believe I have found a solution. Hopefully you are all using SCIM, and this is why the input does not work. The workaround for this is to simply set the XMODIFIERS variable to '' when launching WINE.

```
XMODIFIERS='' wine myapp.exe
```

For .desktop application launcher files, you should edit them as follows, using the 'Properties' menu by right clicking and editing the 'Command' section: 

```
env XMODIFIERS='' WINEPREFIX="/home/jyaan/.wine" wine "C:\DeusEx\System\DeusEx.exe"
```

I hope this works for you guys. Good luck.

Thanks for posting this work around. It works fine for me, except that it means I can no longer input Chinese/Japanese character in Wine. Unfortunately I am playing Koei's Romance of the three kingdom series, and without the Chinese/Japanese input, I am stuck at a certain point.

Any one knows a better solution?

---

### Post by zamajama on 2009-06-22
WINE can be such a pain sometimes. :x 

I also tried it with double quotes and no space in between them like this: 

```
env XMODIFIERS="" WINEPREFIX="/home/theuser/.wine" wine "C:\Program Files\Raven\SOF\sof.exe" +set console 1
```

(yes that is good 'ole Soldier of Fortune in the code) - I also modified  my Rosetta Stone desktop icon accordingly.

**[COLOR="Green"]Thanks for finding the solution jyaan!![/COLOR]**

---

### Post by Jiawen on 2010-01-17
I've tried the XMODIFIERS='' trick with Wine. While it works with notepad (I can enter text freely there, though SCIM doesn't work so I can't input Chinese), it doesn't work with other apps. With everything else, I'm able to do a single keypress, then Wine doesn't take any more input from the keyboard. Has anyone found a more permanent solution?

Ubuntu 8.04 | Wine 1.0.0-1ubuntu4~hardy

---

