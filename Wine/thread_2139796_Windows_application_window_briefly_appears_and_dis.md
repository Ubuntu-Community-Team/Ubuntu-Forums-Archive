---
title: "Windows application window briefly appears and disappears"
date: 2013-04-27
forum: Wine
---

### Post by Defrector on 2013-04-27
An apparently VB-based application which I'd been using for months suddenly stopped functioning properly a few hours ago. The window appears for a split second then disappears. The app keeps running somehow until I Ctrl+C in the terminal. I did not install anything new in the time it stopped running. I tried removing and re-installing wine,even installing an older version 1.5ppa->1.4, no change. Had read some things about libpng needing to be installed; it was already installed and it was reinstalled, no change.

Any ideas how to resurrect this app?

Here is the terminal output:
```
fixme:ole:OleLoadPictureEx (0x9dfda4,798,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32fa50), partially implemented.
fixme:ole:OleLoadPictureEx (0x9dfda4,162182,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32fa20), partially implemented.
fixme:ole:OleLoadPictureEx (0x9dfda4,196670,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32fa20), partially implemented.
fixme:ole:OleLoadPictureEx (0x9dfda4,1262,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32fa20), partially implemented.
fixme:ole:OLEPictureImpl_SaveAsFile (0x1f3ef8)->(0xf78128, 0, (nil)), hacked stub.
fixme:ole:OleLoadPictureEx (0x9e8de4,774,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f67c), partially implemented.
fixme:ole:OLEPictureImpl_SaveAsFile (0xf78f30)->(0xf80008, 0, (nil)), hacked stub.
err:menubuilder:convert_to_native_icon error 0x80004005 getting frame 7
err:menubuilder:convert_to_native_icon error 0x88982F04 committing encoder
^Cfixme:console:CONSOLE_DefaultHandler Terminating process 8 on event 0
```

---

### Post by Defrector on 2013-04-27
Update: Considering the possibility that the window was minimizing and falling out of view, I tried using a different window manager and it still was not on the window list. It looks like the window is failing to create. Sometime it shows up in my dock for a split second. Task manager shows it still running until I terminate it.

---

### Post by Defrector on 2013-04-28
Gave up and found an alternative app to do the job. Can't win em all...

---

