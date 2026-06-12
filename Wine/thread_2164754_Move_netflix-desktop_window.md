---
title: "Move netflix-desktop window"
date: 2013-08-01
forum: Wine
---

### Post by kons-na on 2013-08-01
Hi everyone. I successfully installed netflix-desktop on my Ubuntu 13.04 machine. 

Unfortunately I don't have any window decoration (status bar, window header etc.) which means I can't move the window. 
I have two monitors and the window always pops up on my secondary screen. I would like to move it or at least to change the position of the window prior to execution. 

Does anybody have an idea where I could do that?

---

### Post by CatKiller on 2013-08-01
Alt+click-and-drag will move the window.

---

### Post by kons-na on 2013-08-01
Works with every window except for this one. :(

---

### Post by kostkon on 2013-08-01
> **kons-na said:**
> Unfortunately I don't have any window decoration (status bar, window header etc.) which means I can't move the window.
If you mean that it is in full screen mode, then I think you can press CTRL+F4 to change it to window mode.

---

### Post by kons-na on 2013-08-01
No, it is not fullscreen. it has approximately the size of the display though. The only way to close the application is a big X during browsing. Otherwise the window just embeds a wine emulated firefox with the silverlight extension. 
I tried to look through the wine-browser configs, but can't find anything that would change this behaviour. It is basically a border less window

---

### Post by kostkon on 2013-08-01
> **kons-na said:**
> No, it is not fullscreen. it has approximately the size of the display though. The only way to close the application is a big X during browsing. Otherwise the window just embeds a wine emulated firefox with the silverlight extension. 
I tried to look through the wine-browser configs, but can't find anything that would change this behaviour. It is basically a border less window
Sorry I gave you the wrong key combo in my last post; try pressing F11 and post back whether it has made any difference.

---

### Post by kons-na on 2013-08-01
> **kostkon said:**
> Sorry I gave you the wrong key combo in my last post; try pressing F11 and post back whether it has made any difference.
No, still doesn't work

---

### Post by CatKiller on 2013-08-02
You can tell Wine whether it should let the window manager decorate the windows. You can either run winecfg from the prefix that you're running Netflix with, or add the decoration option to the command part of your Netflix launcher.

---

### Post by kons-na on 2013-08-02
The problem is that the script is not calling wine, but [wine-browser]("http://www.ubuntuupdates.org/package/ehoover_compholio_netflix/quantal/main/base/wine-browser-installer"), which only offers options to enable debuggin and to allow addons

---

### Post by slw210 on 2013-08-02
Post the steps you used to install Netflix.


I have followed these and have NO problems. [**NETFLIX ON UBUNTU**]("http://www.howtogeek.com/130372/how-to-watch-netflix-on-ubuntu-with-the-netflix-desktop-app/")

---

### Post by kons-na on 2013-08-02
I did. And the repos contain the same programs as far as I can see it. No idea why I seem to be the only one who experiences this :)

---

### Post by millerthegorilla on 2013-08-04
HI - I had the same issue and so I installed Arandr, and then de-activated the second screen.  You can also pause netflix and then click on the screen so that the browser is selected and then press F11 - this moves it down from full screen.  Then you can drag it to the other window.  It might take a few attempts to find out how to activate just the wine-browser before the F11 key works.

---

### Post by kons-na on 2013-08-04
Oh it finally worked. In the netflix menu i had to aim for the most upper end of the window and then F11 worked. Thank you.

---

