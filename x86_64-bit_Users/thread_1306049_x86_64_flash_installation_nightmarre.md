---
title: "x86_64 flash installation nightmarre"
date: 2009-10-30
forum: x86 64-bit Users
---

### Post by hoboy on 2009-10-30
This is my opreating system.
Linux ubuntu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux
I want to install flash to play some radios, and youtube. but I have really I have used long long time on it now.
I have am trying this link [http://ubuntuforums.org/showthread.php?t=1259102](http://ubuntuforums.org/showthread.php?t=1259102)
but it is not working, the radios I could play before upgrading from 9.04 to 10.9 are not working.

---

### Post by e-nygma on 2009-11-04
If you have already installed any flash on your system, follow these steps to remove it from your system.

sudo apt-get remove --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash 
sudo apt-get remove --purge swfdec-mozilla libflashsupport nspluginwrapper iceape-flashplugin 
sudo apt-get remove --purge iceweasel-flashplugin mozilla-flashplugin firefox-flashplugin 
sudo apt-get remove --purge xulrunner-flashplugin midbrowser-flashplugin xulrunner-addons-flashplugin
sudo rm -f /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/firefox/plugins/npwrapper.libflashplayer.so
sudo rm -f /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so
sudo rm -f ~/.mozilla/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/firefox-addons/plugins/npwrapper.libflashplayer.so
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -f /usr/lib/mozilla/plugins/*flash*

then download the 64bit flash player from Adobe's website:

[http://labs.adobe.com/downloads/flashplayer10.html]("http://labs.adobe.com/downloads/flashplayer10.html")

extract the file to your desktop, open up a terminal and write in the following command to copy it to the oppropriate location and then your done.

sudo cp /home/your_user_name/Desktop/libflashplayer.so /usr/lib64/mozilla/plugins

Have fun.

---

