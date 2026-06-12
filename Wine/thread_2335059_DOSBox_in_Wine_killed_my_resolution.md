---
title: "DOSBox in Wine killed my resolution?"
date: 2016-08-25
forum: Wine
---

### Post by shakkol2 on 2016-08-25
Hello, everyone.

I know what you're thinking, and it's not that I was trying to install or play anything in DOSBox through Wine. I bought a game on GOG and tried to install it through PlayOnLinux so I can copy the files and play them in the native DOSBox. To be more specific, the game is Redguard, from Bethesda.

So the issue I have is that I installed the game, and upon launching it (to see why this game had DOSBox settings and whatnot, but a Windows launcher) DOSBox (in Wine) froze up, and upon force-closing it my screen resolution was screwed up. I am looking for any answer that doesn't lead to "reinstall Ubuntu" because I finally have a nice assortment of Windows games set up just right to play on here (since I removed Windows from my drive altogether). I'm able to type this up because I have myself set up for a multi-monitor, shared screen output, and for some reason it's only the primary screen (my monitor) that is having this issue. I took a screenshot and there's a highlighted area on the desktop that shows where my screen is crunched down to on my monitor. I've tried changing the resolution in the display settings and that didn't work.

Does anyone have any suggestions?

---

### Post by howefield on 2016-08-25
Thread moved to the "*Wine*" forum.

---

### Post by shakkol2 on 2016-08-25
I honestly don't believe this should have been moved to Wine. Wine may have caused the issue, but this is an issue that starts after I log in, before I even open Wine. Though the login screen knows its true resolution.

---

### Post by shakkol2 on 2016-08-25
Since this was, indeed, NOT a Wine issue, I did some digging around and changed my monitor's settings in /.config/monitors.xml. For future reference, if anyone ever gets this same issue, here's what you can do:

Open your terminal and type in
```
gedit ~/.config/monitors.xml
```

Look for the <width> and <height> tags and set your resolution accordingly. IE:
```
<width>1920</width>
<height>1080</height>
```

Then save the file, either restart or logout, then log back in. Ta-daa~ it's done.

---

