---
title: "No text in eyeq wine"
date: 2007-12-09
forum: Wine
---

### Post by kcubeice on 2007-12-09
hi there every one i am a newbie to ubuntu and i heard about wine being able to install windows programs so i installed eyeq(speed reading program) but when it came to the actual text it is only showing blank screen but graphics otherwise including sound are working perfectly.I copied tahoma.ttf to ~/.wine/drive_c/windows/fonts i also copied the entire *.fon from /usr/share/wine/fonts/ to  ~/.wine/drive_c/windows/fonts but nothing is working 

i have attached a picture of how it looks(the blank screen should have text in it).

PLS HELP!!!

---

### Post by cogadh on 2007-12-09
The terminal output from Wine might help in determining what is happening. Please post that.

---

### Post by kcubeice on 2007-12-09
i did that and this is what i got

"err: x11drv:X11DRV_CreateWindow invalid window width 2080539920"
"err: x11drv:X11DRV_CreateWindow invalid window height 2124098348"

The text is doing some graphics like popping in one place then goes to another place.Do i need to install visual basic,directx or something like that?

---

### Post by cogadh on 2007-12-09
No, nothing in that error would tell me that you need to do that (besides, you technically can't install DX in Wine). Have you tried running the app in a Wine virtual desktop window?

---

