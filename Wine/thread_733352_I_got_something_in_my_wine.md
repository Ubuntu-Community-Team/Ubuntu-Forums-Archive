---
title: "I got something in my wine"
date: 2008-03-23
forum: Wine
---

### Post by NeoFlexer on 2008-03-23
I just installed wine last night, and this morning I was playing around with the options and screwed it up :(

The view is to big for my screen and now I can't see anything... Can anybody help me?

[IMG]http://i290.photobucket.com/albums/ll243/CJSommie/Screenshot.png[/IMG]

---

### Post by happyhamster on 2008-03-23
Open Text Editor and create an empty text file. Copy & paste these 2 lines:

```

[HKEY_LOCAL_MACHINE\System\CurrentControlSet\Hardware Profiles\Current\Software\Fonts]
"LogPixels"=dword:00000060
```


- Save the file in your home folder as "fontrescue.reg"
- Open a terminal (Applications-->Accessories-->Terminal) and run the command:

regedit fontrescue.reg

- After that, run winecfg. The wine screen/font resolution under the Graphics tab should now be 96 again (default value). (The setting is in hexadecimals BTW 60hex = 96dec.)

Good luck.

---

### Post by NeoFlexer on 2008-03-23
All better, thanks :)

[IMG]http://i290.photobucket.com/albums/ll243/CJSommie/Screenshot-1.png[/IMG]

---

### Post by tabotto on 2008-05-11
you are absolutely an angel.

Where to learn more registry tricks ? Give water to the thirsty !! thanks

---

### Post by cogadh on 2008-05-12
[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)
A few of these might be useful.

---

### Post by vjcamarena on 2009-12-02
wow, thank you SO much!

---

