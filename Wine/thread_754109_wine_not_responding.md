---
title: "wine not responding"
date: 2008-04-13
forum: Wine
---

### Post by windows-killer on 2008-04-13
when I click on an icon to open something, nothing happens.
any ideas? Am using the latest version of wine

---

### Post by chewearn on 2008-04-14
Check the file associations.

Right-click on file > Properties > Open With

---

### Post by windows-killer on 2008-04-15
thanks for the reply.
I already did that and no luck.

---

### Post by cogadh on 2008-04-15
Wine is not really meant to be used by just double-clicking on an .exe, it is meant to be used from the terminal or using the shortcuts that Wine puts in the applications menu when you install something. From the Wine FAQ:
> ***When I double-click on a .exe file in my File Manager, nothing happens.***

Note: If you can, start applications by clicking on the application's icon in the Applications / Wine menu or desktop instead. Double-clicking .exe's is typically only needed for applications that aren't installed yet, e.g. to run the setup.exe on a cd-rom game, or a downloaded installer.

If double-clicking doesn't work, you might need to right-click the file and choose "Run with Wine". It depends on your file manager. If that also doesn't work, contact whoever built your wine packages and complain.

You can work around this problem by using the commandline instead of your File Manager. To do this, open a terminal window, navigate to the folder where your application is, and run it by typing wine (program).exe. Running wine in this fashion will also let you see Wine's debugging log. This may not be the friendliest way to use Wine, but at the moment it is the most effective, and it's how wine developers usually do it.

---

