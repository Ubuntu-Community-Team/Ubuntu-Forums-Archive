---
title: "[SOLVED] Heroes of Might and Magic 5 -- texture problem"
date: 2008-01-02
forum: Wine
---

### Post by kade on 2008-01-02
Hey guys,

Following the brief [[COLOR="Orange"]howto from Wine App DB[/COLOR]]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=4905"), I installed HoMM5 with no problems.  
The game runs, however the textures are not displayed. The terminal prints: 
'fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support'   many times. 

I have scoured the web for days, and have been unable to find help.  
I also tried patching the game (which I did successfully), but the texture problem persisted.
Here are my specs:
- Wine 0.9.52 
- IBM Thinkpad T60 
- ATI x1400
- fglrx 8.37.6 driver

Wine Config:
- ALSA driver
- Windows Settings: 'Allow the window manager to control the windows' and 'Emulate a virtual desktop' are selected ; 'Vertex Shader support: none' ; 'Allow Pixel Shader' is unchecked.
- Libraries: I tried with the default Wine libs, plus the d3dx9_25.dll.  When that didn't work, I installed DX9c, but that didn't fix the problem either.
- Regedit: Added to 'HKEY_CURRENT_USER\Software\Wine\Direct3D', the string value 'VideoMemorySize' = 128

I've attached a screenshot of what I've described (the file is ~100kb).

---

### Post by kade on 2008-01-03
I have reduced the file size of the screenshot from 680kb to 100kb.

---

### Post by kade on 2008-01-03
Well, I finally figured out what my problem was.  

I noticed the first error that I receive, when I ran the game was:

Xlib:  extension "XFree86-DRI" missing on display ":1.0".

Which is caused by my xgl session.  Using a failsafe gnome session, the game ran fine (albeit a little slowly) with 'Allow Pixel Shader' UNCHECKED (if checked the game runs, and the menu displays, however the background graphics are black).

I'm going to run some more tests and I'll post my finding.

---

### Post by slim_s on 2010-07-29
Kade, my homm3 looks exactly the same as in the screenshot, you attached. How can I fix this problem?

---

