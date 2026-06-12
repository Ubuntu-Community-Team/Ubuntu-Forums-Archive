---
title: "Wine X11 missing"
date: 2007-03-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by boss429 on 2007-03-10
I'm using Ubuntu 6.10 64 bit.
I compiled wine, but when I run it I get this:
```
boss429@ubuntu:/mnt/2k/Program Files/Adobe/Adobe Photoshop CS2$ wine photoshop.exe
fixme:actctx:QueryActCtxW 80000010 0x14ac42c (nil) 1 0x33fbcc 8 (nil)
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
```
I have an nVidia e-GeForce 7300 GS card.  I've installed the drivers off nvidia's web site.
I'm relatively new to Linux.

Thanks

---

### Post by Kilz on 2007-03-10
> **boss429 said:**
> I'm using Ubuntu 6.10 64 bit.
I compiled wine, but when I run it I get this:
```
boss429@ubuntu:/mnt/2k/Program Files/Adobe/Adobe Photoshop CS2$ wine photoshop.exe
fixme:actctx:QueryActCtxW 80000010 0x14ac42c (nil) 1 0x33fbcc 8 (nil)
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
```
I have an nVidia e-GeForce 7300 GS card.  I've installed the drivers off nvidia's web site.
I'm relatively new to Linux.

Thanks

You might want to check out the Wine Application Database page for information on running any windows application with wine. [Here is the photoshop page.]("http://appdb.winehq.org/appview.php?iVersionId=133")

---

### Post by boss429 on 2007-03-10
I don't think its photoshop related the same thing happens even when I run pinball.
```
boss429@ubuntu:/mnt/2k/Program Files/Windows NT/Pinball$ wine pinball.exe
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!

```

---

### Post by Masterj15 on 2007-03-29
I have the same problem. Think it is the way we built it that Is why I am going to try to unstall wine and get the debian package for it instead.:)

---

### Post by Kilz on 2007-03-29
> **Masterj15 said:**
> I have the same problem. Think it is the way we built it that Is why I am going to try to unstall wine and get the debian package for it instead.:)

Let us know how it went. By the way, does Debian have a 64bit wine package in its repo's?

---

### Post by Masterj15 on 2007-04-03
Ok, I know a little bit more than I did then. Download for ubuntu packages lilbgtk engine (Or something like that) that will get rid of the font thing. all I need to do is try to uninstall it so I can reinstall it angain. I don't know how to uninstall things that I installed from the terminal. I f this goes through I will make a tutorial on how to do this with pecific detals. When you download that libgtk-engine all that is going to be left is the x11. If you messed up like I did then you still can make some things work. I have quake3 running. all you have to do is download quake3 and put it in your home file install it in your home file and then copy and pasts the icon of the game without anything else and that should do it.:)

---

### Post by iansane on 2007-10-12
I just installed wine. The latest release from wine hq was 46. this was just 2 days ago. I get the same error and all I'm trying to do is run "winecfg" Nothing works at all because it can't make a window. I need a window so I can install a program so I know it's not because of a program. x11 driver is missing or wine can't find it because I get the same message as the original post. I don't know how you guys even got the first program installed. By the way, I recently upgraded to the gutsy release candidate and wine came from the gutsy repo. on my second try at reinstalling. The fiesty version in synaptic was 45 and it worked but didn't have the option to rightclick and open with wine. Any help would be apreciated.

I should say I get the same error message but without the stuff about adobe. Sorry, and thanks for any help :)

---

### Post by iansane on 2007-10-12
while waiting for a reply from someone, I have tried compiling source, deb package, and apt-get. All 3 ways install the same wine with the same problem. At least with the 45 version wine worked. I guess I'll have to go back to it.  That stinks cause the older version has less userfriendly options but oh well. I'll still check for replys if anyone can help. Thanks

---

### Post by Kilz on 2007-10-13
> **iansane said:**
> while waiting for a reply from someone, I have tried compiling source, deb package, and apt-get. All 3 ways install the same wine with the same problem. At least with the 45 version wine worked. I guess I'll have to go back to it.  That stinks cause the older version has less userfriendly options but oh well. I'll still check for replys if anyone can help. Thanks

Exactly what user friendly options are missing?

---

