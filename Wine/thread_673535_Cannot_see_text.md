---
title: "Cannot see text"
date: 2008-01-20
forum: Wine
---

### Post by Tredici on 2008-01-20
Hello, I just recently installed wine and it worked perfectly until I went to install full tilt poker and other applications. Here is a screen shot of the problem. I cannot figure out what went wrong and why I cannot see any of the text in these boxes! If anyone has a solution please help me out.

---

### Post by pytheas22 on 2008-01-20
You may not have the proper fonts installed.  Can you copy the text there and paste it into a text editor and have it show up?  I had a situation like that once.  If that's the case, try installing more Windows fonts (into your wine environment, not Ubuntu itself) and see if it helps.

---

### Post by Tredici on 2008-01-20
It is not working, copying and pasting.

---

### Post by pytheas22 on 2008-01-20
Did you look up the application you're trying to use in the wine database on winehq.com?

---

### Post by Mikesco3 on 2008-11-07
I can't see text either. and not only wine there are a few other little apps, like the new network configuration tool that sits in the system tray, when I right click on it I can't see the text on the context menu

---

### Post by Mikesco3 on 2008-11-08
Somebody suggested this fix and it actually worked so, I recommend you try it out.
First disable compiz if you are running it (the following steps are for Ubuntu)
 [LIST]
[*]System -> Preferences -> Appearance -> Visual Effects -> None
[/LIST]
[LIST=1]
[*]Create a text file, say called "settings.txt" with the following content
```
[HKEY_CURRENT_USER\Software\Wine\X11 Driver]
"ClientSideWithRender"="N"
```
[*]open the terminal and run
```
regedit settings.txt
```
[/LIST]
that did the trick for me, that is if your text is not showing up at all or just plain garbled. The link with the original post is here 
[http://wiki.winehq.org/FAQ#head-dec980f6deabdb11b789c981bf49e10e70929eaf]("http://wiki.winehq.org/FAQ#head-dec980f6deabdb11b789c981bf49e10e70929eaf")

---

