---
title: "karmic broke my flash"
date: 2009-11-02
forum: x86 64-bit Users
---

### Post by not a pipe on 2009-11-02
what the hell, karmic decides it's a good idea to reinstall nspluginwrapper (or whatever it is) while I had it specifically uninstalled. purging this, and reinstating the 64bit flash into the proper folder still causes firefox to crash on any page with flash. I also tried the script pinned at the top of the forum. Any help?

---

### Post by bigbroantonio on 2009-11-02
> **not a pipe said:**
> what the hell, karmic decides it's a good idea to reinstall nspluginwrapper (or whatever it is) while I had it specifically uninstalled. purging this, and reinstating the 64bit flash into the proper folder still causes firefox to crash on any page with flash. I also tried the script pinned at the top of the forum. Any help?

Try downloading x64 flash from:
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz)

Unpack and move libflashplayer.so to /usr/lib/mozilla/plugins/

---

### Post by not a pipe on 2009-11-02
> **bigbroantonio said:**
> Try downloading x64 flash from:
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz)

Unpack and move libflashplayer.so to /usr/lib/mozilla/plugins/

That's the first thing I did. Also I tried the script you had on here a minute ago with no luck. 
If I run firefox with a site that uses flash, it still crashes immediately. 
```
someone@computer:/usr/lib/mozilla/plugins$ firefox youtube.com
Segmentation fault (core dumped)
```
Have I done something wrong in installing flash, or could there be a problem with something else like my video driver?
edit: the plugin crashes chrome as well. "The following plug-in has crashed: /usr/lib/mozilla/plugins/libflashplayer.so"

---

### Post by bigbroantonio on 2009-11-02
I've been looking around, and came across this.  It should get rid of flash completely, and the install.

First, unpack flash to, say, your desktop, then run the following script (editing the necessary parts):

```
# deinstall all other Flashplayer
# which are installed?:
dpkg -l flashplugin-nonfree mozilla-plugin-gnash swfdec-mozilla
#
# delete installed:
sudo apt-get remove mozilla-plugin-gnash swfdec-mozilla flashplugin-nonfree
#
# create new folder for Flashplayer:
sudo mkdir /usr/lib/flashplugin-nonfree/
#
# copy the new Flashplayer in the just created folder. change the first
# term to the unpacked path.
# if you unpacked to your Desktop, replace YourDownloadPath with
# /home/YourLoginName/Desktop
sudo cp YourDownloadPath/libflashplayer.so /usr/lib/flashplugin-nonfree/
#
# give Firefox the Flashplayer as Plugin , by creating a symbolic Link
# to the path of the Flashplayers in Plugin-folder from Firefox:
sudo ln -s  /usr/lib/flashplugin-nonfree/libflashplayer.so /usr/lib/mozilla/plugins/libflashplayer.so

```

---

### Post by not a pipe on 2009-11-02
After restarting everything seems to be working fine. Guess I should have tried that before wasting your time =/, as it's a pretty normal thing to try (typical "something's broken" panic on my part, I guess). Thanks for your help.

---

### Post by bigbroantonio on 2009-11-02
> **not a pipe said:**
> After restarting everything seems to be working fine. Guess I should have tried that before wasting your time =/, as it's a pretty normal thing to try (typical "something's broken" panic on my part, I guess). Thanks for your help.

No time wasted at all!:D

---

