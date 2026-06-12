---
title: "Upgrade to wine leaves it useless."
date: 2008-01-31
forum: Wine
---

### Post by jrharvey on 2008-01-31
Is anyone else having this proplem??? I updated wine with automatic update and now NONE of my apps work. I attempt to start them but nothing ever opens. No window ever pops up or anything. I was just wondering, what the deal was. Right now I am using firefox(windows), Sketchup, and Kerkythea(rendering program). All of these worked perfect b4 the update.

---

### Post by hikaricore on 2008-01-31
errmmm..... run them from a terminal and see what happens?

also have you tried downgrading WINE?

---

### Post by arvevans on 2008-01-31
I am seeing something similar.  After the last update any menu items that I had added myself now just flash the screen and are gone.  Since I have not changed any software for the past two weeks, it seems to indicate the last update may be related to this problem.  I'm still working on the situation and will post here again if I get it resolved.

Arv
_._

---

### Post by jrharvey on 2008-01-31
> **hikaricore said:**
> errmmm..... run them from a terminal and see what happens?

also have you tried downgrading WINE?

Im not sure how to run a program in the terminal from WINE. I am also not sure how to downgrade. I went to the website and the only download I saw was the latest version. I did try removing and reinstalling the newewst version. No Luck!!

---

### Post by happyhamster on 2008-01-31
After installing a newer wine version, try updating wine's configuration using the command:

wineprefixcreate

If everything went well, there should be a message "wine updated successfully" or such. Then try to run your apps again.

---

### Post by jrharvey on 2008-01-31
> **happyhamster said:**
> After installing a newer wine version, try updating wine's configuration using the command:

wineprefixcreate

If everything went well, there should be a message "wine updated successfully" or such. Then try to run your apps again.

I tried it and no luck.

---

### Post by happyhamster on 2008-02-01
In case you're still suffering from this: try to check the menu items manually. Right-click the menu bar, and choose 'Edit Menus'. In the left window pane select wine and keep looking until you find the exact launch-entry for your application. Right-click that entry and choose 'properties'.

Under 'Command' will be the line used to launch the application. It should look something like this:

env WINEPREFIX="home-folder-name-/.wine" wine "C:\Program Files\UBISOFT\Prince of Persia The Sands of Time\PrinceOfPersia.exe" 

Then check if it matches the correct path and application-exe. Open your file-manager (nautilus) and press ctrl-h to be able to see hidden files. There should be a hidden .wine folder in your home dir, containing all things wine-related.

Good luck.

---

### Post by jrharvey on 2008-02-01
This is what i get with sketchup

```
jrharvey@jrharvey-desktop:~$ env WINEPREFIX="/home/jrharvey/.wine" wine "C:\Program Files\Google\Google SketchUp 6\SketchUp.exe" 
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2007 WGL Attribute
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2028 WGL Attribute
fixme:wgl:X11DRV_wglGetPixelFormatAttribivARB unsupported 2007 WGL Attribute
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2007 WGL Attribute
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2028 WGL Attribute
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2007 WGL Attribute
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2028 WGL Attribute
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2007 WGL Attribute
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2028 WGL Attribute
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2007 WGL Attribute
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2028 WGL Attribute
X Error of failed request:  BadAccess (attempt to access private resource denied)
  Major opcode of failed request:  160 (Composite)
  Minor opcode of failed request:  1 ()
  Serial number of failed request:  44
  Current serial number in output stream:  48
jrharvey@jrharvey-desktop:~$ 
```

---

### Post by jrharvey on 2008-02-01
This is my rendering program that always worked fine.


jrharvey@jrharvey-desktop:~$ env WINEPREFIX="/media/sda1/Program Files/Kerkythea Rendering System/kerkythea.exe
> 
> 
> 
> 
> 
> 
> 
> 
> 
> 
>

---

### Post by jrharvey on 2008-02-04
bump

---

### Post by ArtInvent on 2008-02-12
I had the same problem with Wine and Sketchup and CorelDraw 11 recently. Serious regressions starting around Wine 0.9.53. Programs wouldn't even start. I recently compiled the latest release v0.9.55 because the release notes claim they've been working on regressions, and it is much better. This is still not in the official Wine repo yet but it generally is available a few days after the Wine release. It should be available for installation within the week I would guess.

You can always go back to something like 0.9.51 or whatever you remember working well. You would have to uninstall Wine and then download a .deb package of the version you want from the winehq site. Deb packages install quite easily and can be removed easily later. I actually went back to that version for a while but I still had a problem with Sketchup. This is aggravating because under Feisty and Wine 0.9.46, Sketchup worked pretty much perfectly. You could even search for and download models from the internet! For some reason Sketchup support has gotten worse moving to Gutsy and now it tends to crash and not shutdown correctly and some windows freeze the app, even with 0.9.55 Bummer. Hope the Wine guys are working on this.

---

### Post by jrharvey on 2008-02-15
I really hope so. I was really excited when i found out sketchup worked but now i am bummed out b/c it was a small taste and now NOTHING.

---

