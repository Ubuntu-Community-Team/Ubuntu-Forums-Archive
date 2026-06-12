---
title: "Wine encoding problem"
date: 2008-01-01
forum: Wine
---

### Post by Nikitas350 on 2008-01-01
I have installed wine to try to install a greek dictionary. Everything went fine and the only problem was that the greek characters are not appeared properly. How can i fix this? Thanksss

---

### Post by Nikitas350 on 2008-01-02
help......

---

### Post by happyhamster on 2008-01-02
In case you haven't already, try installing msttcorefonts:

sudo apt-get install msttcorefonts


If it doesn't work, could you give some more information: which program is it exactly? Which wine version are you using?

---

### Post by Nikitas350 on 2008-01-03
Thanks i will try it as soon as i arrive home.

---

### Post by Nikitas350 on 2008-01-03
Well the package msttcorefonts was already installed.The program is called gword and you can find it at [http://rapidshare.com/files/80979731/Gword.zip](http://rapidshare.com/files/80979731/Gword.zip) .You can test it.... Thanks...
edit: i have wine-0.9.46 installed

---

### Post by Nikitas350 on 2008-01-03
I have a problem and with an other application. Here is the screenshot and and the output of the wine

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
fixme:pager:PAGER_Create [0x30060] Drag and Drop style is not implemented yet.
fixme:pager:PAGER_Create [0x30068] Drag and Drop style is not implemented yet.
fixme:shdocvw:PersistStreamInit_InitNew (0x1503f8)
fixme:shdocvw:WebBrowser_QueryInterface (0x1503f8)->({376bd3aa-3845-101b-84ed-08002b2ec713} 0xe962c0) interface not supported
fixme:shdocvw:OleControl_OnAmbientPropertyChange Unknown dispID -1
fixme:bidi:mirror stub: mirroring of characters not yet implemented

Thanks

---

### Post by Nikitas350 on 2008-01-07
Helppppp

---

### Post by happyhamster on 2008-01-07
Gword should have its own font  (a .fon file). Copy that one to windows' font map, or into wine's font map. (In nautilus, select View-->Show hidden files, then navigate to .wine etc,etc).
You can also try to run it using different (older) windows versions (using winecfg).

---

### Post by jonian_g on 2008-05-01
In case that someone else has this problem try this:

Download tahoma fonts from [here]("http://fonts.appliedlanguage.com/fonts/tahoma.ttf") and put the file in /home/user/.wine/drive_c/windows/Fonts.

This should work with other languages too because it is a common problem according to this:

"There is important regression in Ubuntu Hardy (8.04) wine packages - lots of non ISO-8859-1 glyphs (Cyrillic, Lithuanian, etc. letters) are missing in built-in Tahoma font.
This causes displaying "::::::" instead of these letters in lots of applications, which uses Tahoma font (almost all installers uses this font)."

---

### Post by mistseeker on 2009-01-08
Thanks, this helped me!

---

### Post by cgia on 2009-03-11
Worked fine indeed!

---

### Post by christos.athanasiadis on 2009-09-19
It worked for me also with 'Navicat 8 for MySQL'.
Great advice! :)

---

### Post by pyrforos on 2009-11-02
worked for me too!Nice job!

---

