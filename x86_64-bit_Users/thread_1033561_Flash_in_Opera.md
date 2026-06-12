---
title: "Flash in Opera"
date: 2009-01-07
forum: x86 64-bit Users
---

### Post by Ellaine on 2009-01-07
Did a fresh install monday of 8.04 64Bit. Installed Opera & Firefox. Installed sun java 64bit and three different downloads of flash. Both Firefox & Opera played flash videos. Hard drive died tuesday. Reloaded again on another hd & put in everything. Flash plays in Firefox but not Opera. Is there a simple way to get flash to work in Opera? If it works in firefox there must be a way to copy this from firefox into Opera?

I hope!

---

### Post by Arup on 2009-01-07
Best way to make it work is to remove with --purge the installed Flash and nsplugin, then download x64 Flash from Adobe site. Untar and do a sudo mv libflashpleyr.so /usr/lib/mozila/plugins

Opera picks it up from there and it works fine.

---

### Post by CJ56 on 2009-01-07
So you've got the libflashplayer.so from the Adobe website - ?

In which case, close Opera, copy libflashplayer.so from whichever folder it lives in, and paste it into usr/lib/opera/plugins 

Restart opera and it should work...

---

### Post by Ellaine on 2009-01-07
CJ56: I didn't get flash from Adobe, couldn't get the tar.gz to open and run from the desktop. What I have is usr/lib/moxilla/plugins is "flashplugin-alternative.so.
 I can copy this file but when I go to usr/lib/opera/plugins I can't paste into this folder. The "paste" command is grayed out. How to I get this into the opera folder?

---

### Post by CJ56 on 2009-01-07
Okay, well...

What I would attempt is to clear out all the old stuff first (as per Kilz' instructions in the sticky) -

Well worth doing, one line at a time, is

```
sudo apt-get -y purge nspluginwrapper
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo apt-get -y purge flashplugin-nonfree
sudo rm -rfd /usr/lib/nspluginwrapper
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so
```

This clears out all the gunge from previous installations and sets you up to -

Download the Flash 10 for 64-bit tar.gz from the Adobe website and close all browsers

Simplest thing after that is to extract the libflashplayer.so file (use right-click on the tar.gz and choose Extract Here) and copy the .so into .mozilla/plugins in your Home Folder. 

This should set up Firefox with Flash 10. Then copy libflashplayer.so into the usr/lib/opera/plugins folder and that should work for Opera. It did for me...

If there are problems getting into some folders, what I do (it's a bit flaky, but it works) is open the terminal and type

sudo nautilus

Which lets me muck around with the file system, but using the normal nautilus GUI

Hope this helps...

---

### Post by Ellaine on 2009-01-07
CJ56 THANKS; This worked perfect except I couldn't copy into opera/plugins thru normal terminal. Used nautilus and drag & drop to opera plugins folder. Worked perfect. Youtube flash videos play in both firefox & opera.   




THANKS a million!

---

### Post by CJ56 on 2009-01-07
Glad it worked!

---

