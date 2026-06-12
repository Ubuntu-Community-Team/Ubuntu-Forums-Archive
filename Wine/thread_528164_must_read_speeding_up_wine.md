---
title: "*must read* speeding up wine"
date: 2007-08-17
forum: Wine
---

### Post by unknownm on 2007-08-17
Well i'm not going to say this will work with any other game but I tried it on css

I downloaded the [DX10 files]("http://fallingleafsystems.com/site_media/preview.zip") off of that website and placed them inside [.wine/system32/Directx folder ]("http://ubuntuforums.org/attachment.php?attachmentid=40899&stc=1&d=1187373925"). Next thing I did was startup css and joined the same server that gave me avg 28fps and whata you know?! my fps just raised up. 

I love linux and wine alot so please try this people. There should be no harm

---

### Post by Mogurijin on 2007-08-17
This is interesting .Even thought I don't think any games can utilize dx10, but then again Guild Wars is supposed to work best set to Win98, so this might be something to try. However, I'm confused as to where exactly your putting these files? Did you make a new folder because all I have in .wine/drive_c/windows/system32 is a folder called drivers. Did you make a directx folder and put the contents of the preview folder into there loosely or did you make a dx10 folder?

---

### Post by unknownm on 2007-08-17
> **Mogurijin said:**
> This is interesting .Even thought I don't think any games can utilize dx10, but then again Guild Wars is supposed to work best set to Win98, so this might be something to try. However, I'm confused as to where exactly your putting these files? Did you make a new folder because all I have in .wine/drive_c/windows/system32 is a folder called drivers. Did you make a directx folder and put the contents of the preview folder into there loosely or did you make a dx10 folder?

nope there was already DX folder in there because I tried to install the DX9 setup :P that didn't work btw

---

### Post by sdowney717 on 2007-08-17
you really mean windows\system32\Directx inside of .wine directory drive_c

---

### Post by sdowney717 on 2007-08-17
I wonder if you have to try to install directx in wine, have it fail, then copy these files over to see any improvement

---

### Post by Mogurijin on 2007-08-17
Well [this page]("http://ubuntuforums.org/showthread.php?t=497332") specifically says not to install MS DirectX drivers under the "Installation Stuff" heading.

---

### Post by hikaricore on 2007-08-17
> **unknownm said:**
> nope there was already DX folder in there because I tried to install the DX9 setup :P that didn't work btw

[B]Installing DirectX under WINE is not recommended, useful, nor is it wise.
You'll more than likely overwrite WINE specific dll files that WINE needs to run.

If you need certain dll files for a game or application it is best to install them one by one, and manually.[/B]

---

### Post by cmat on 2007-08-17
I used WINE-doors and I got many Windows applications working. This was due to it downloading Windows native dlls and run times for C++ and Visual Basic. Programs work perfectly.

---

### Post by unknownm on 2007-08-17
> **cmat said:**
> I used WINE-doors and I got many Windows applications working. This was due to it downloading Windows native dlls and run times for C++ and Visual Basic. Programs work perfectly.

hmm I have no problem opening programs it's just css is super slow. I copyed those files inside that folder and it just became faster

---

### Post by unknownm on 2007-08-17
> **hikaricore said:**
> [B]Installing DirectX under WINE is not recommended, useful, nor is it wise.
You'll more than likely overwrite WINE specific dll files that WINE needs to run.

If you need certain dll files for a game or application it is best to install them one by one, and manually.[/B]
well the setup didn't. it some error and said to use error.log ><

---

### Post by disturbedite on 2007-08-17
this isn't brown-nosing, but i've read what hikaricore said and have to agree with him.

---

### Post by cogadh on 2007-08-17
From the Wine Official Wiki FAQ:
> **Does Wine support DirectX? Can I install Microsoft's DirectX under Wine?**

Wine itself provides a DirectX implementation that, although it has a few bugs left, should run fine. Wine supports DirectX 9.0c at this time. Plans for DirectX 10 are underway.

If you attempt to install Microsoft's DirectX, you'll run into some problems. You can install the runtime, but it will not run. The runtime needs access to the Windows drivers, and Wine cannot access them for obvious reasons. The only native Microsoft DLLs that could be useful anyway are the d3dx9_xx.dll type ones, and these require you to accept Microsoft's license. Regardless, don't try and do this.
[http://wiki.winehq.org/FAQ#head-fbaa851e07d7484640cc10b6d0c48abc741260b2](http://wiki.winehq.org/FAQ#head-fbaa851e07d7484640cc10b6d0c48abc741260b2)

In other words, don't try to install DirectX, it will be bad. As for Falling Leaf's "DirectX 10", I'd steer clear of it for the time being. No one is really sure what it actually does or if it is even really legal.

---

