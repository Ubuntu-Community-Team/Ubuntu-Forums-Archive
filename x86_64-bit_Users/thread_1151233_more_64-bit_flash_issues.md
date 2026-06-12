---
title: "more 64-bit flash issues"
date: 2009-05-06
forum: x86 64-bit Users
---

### Post by anextx on 2009-05-06
alright, sorry to have to start a new thread asking about this but its starting to piss me off.

i've been trying to follow the instructions here:
[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)
to get the flash player to work for streaming videos but am still unsuccessful.  flash will sometimes work, but when it does the video and sound are choppy and im starting to think i've installed conflicting packages or something.  most of the time there will just be a black box.

right now i have these installed (that i know of):
flashplugin-nonfree
flashplugin-installer
nspluginwrapper

i have also tried the solution listed here [http://ubuntuforums.org/showthread.php?t=1134734](http://ubuntuforums.org/showthread.php?t=1134734) , disabling the Iced Tea add-on although i don't see a "Flash 10.0" plugin listed at all.

i am running 64-bit 9.04, and am not very well versed with linux so any help you could give would be great.

thanks

---

### Post by anextx on 2009-05-06
also tried the solution given here:
[http://www.stchman.com/flash_firefox.html](http://www.stchman.com/flash_firefox.html)

still have the same problems after reboot

---

### Post by cariboo on 2009-05-06
Download the flash 64-bit alpha plugin [here]("http:///labs.adobe.com/downloads/flashplayer10.html") and extract it to where you can find it, then copy it to /usr/lib/mozilla/plugins. Then remove the one you installed from the repositories

---

### Post by anextx on 2009-05-06
alright, i have downloaded and extracted it to that location - still getting the same problems.  i have a number of folders in usr/lib that are related to flash:

adobe-flashplugin
firefox
firefox-3.0.10
firefox-addons
mozilla
mozilla-firefox

should libflashplayer.so only be in the mozilla/plugins folder? and should anything else be in there?
currently i have these in mozilla/plugins:

libflashplayer.so
libtotem-clone-plugin.so
libtotem-gmp-plugin.so
libtotem-mully-plugin.so
libtotem-narrowspace-plugin.so

---

