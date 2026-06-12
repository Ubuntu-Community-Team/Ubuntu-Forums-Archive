---
title: "playOnlinux?  I just installed Office but I can't find it"
date: 2012-02-26
forum: Wine
---

### Post by Sxynerd on 2012-02-26
I just used PlayOnLinux to install a program but I can't find program I installed.  

This is my first time using Wine.

thanks

---

### Post by howefield on 2012-02-27
Thread moved to the "*Wine*" forum.

Don't use Wine much these days, but remember a log out and back in sometimes was needed for applications to show in the menu.

---

### Post by forrestcupp on 2012-02-28
If you're using Unity, you should be able to click the Dash button in the upper left, and start typing Word, Excel, or whatever, and it should show up.

Assuming PlayOnLinux uses the standard Wine setup, you can find your MS Office folder here:  ~/.wine/drive_c/Program Files/Microsoft Office

If you use the terminal to go to that directory, you'll need to put an escape '\' before the spaces like this
```
cd ~/.wine/drive_c/Program\ Files/Microsoft\ Office
```And just in case you're really new, the '~' means your user's /home folder. If you try to find it in your Nautilus file browser, you'll need to press Ctrl+H to show the hidden files and folders.

---

