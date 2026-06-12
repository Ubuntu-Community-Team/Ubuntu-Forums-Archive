---
title: "Perfect World Sirens of War working"
date: 2012-11-28
forum: Wine
---

### Post by vanquishedangel on 2012-11-28
Perfect World Sirens of war is working quite well
64bit may require ia32-libs and ia32libs-multiarch to be installed, also game seems to run smoother when I changed the direct draw renderer to gdi under configure in playonlinux

[COLOR="Red"]**1. Install playonlinux from here (http://www.playonlinux.com/en/download.html)**[/COLOR]

wget http://www.playonlinux.com/script_files/PlayOnLinux/4.1.8/PlayOnLinux_4.1.8.deb


[COLOR="Red"]**2. Download perfect world, you need to torrent it. The web installer contains a file sharing program that doesn't work in wine.(6-7 gigs)**[/COLOR]

wget http://pwi.perfectworld.com/download/torrent


[COLOR="Red"]**3. Download the language packs for Chinese (helps game run smoother)**[/COLOR]

wget http://download.microsoft.com/download/officexpstandard/ie_zht/1/w98nt42kme/en-us/ie_zht.exe

wget http://download.microsoft.com/download/officexpstandard/ie_zhc/1/w98nt42kme/en-us/ie_zhc.exe


[COLOR="Red"]**4. Install Perfectworld**[/COLOR]

Open playonlinux and click ***"install"***, then select ***"games"*** and check the box for ***"testing"***. Find the perfect world script and install it, when prompted for the perfect world installer navigate to your download folder and open the PWI_v676_Installer folder and select ***"install.exe"***. (verify everything that it gives you an option to) Do not launch game however.


[COLOR="Red"]**5. Install the language packs and required libraries**[/COLOR]

With the playonlinux window open click install and select ***"Install a non-listed program"*** then click ***"Next"*** then select ***"Edit or Update an Existing Application"*** then check the box ***"Show Virtual Drives"*** and select ***"perfectworld"*** then click ***"Next"*** and check the box ***"Install Some Libraries"*** click ***"Next"*** choose ***"32 bits windows installation"*** then ***"Next"*** Check the boxes for these files:

POL_Install_vcrun2005

POL_Install_vcrun2008

POL_Install_directx9

POL_Install_VideoDriver

and when asked, navigate to where you downloaded the language packs and install the language pack, repeat for the second language pack without installing the libraries.


[COLOR="Red"]**6. Make a menu entry for perfect world**[/COLOR]

With playonlinux open select ***"configure"*** then select ***"Make a new shortcut from this virtual drive"*** and select ***"elementclient.exe"*** and name it what you wish, this is how you will start Perfectworld.


[COLOR="Red"]**7. Build dependencies that wine may need**[/COLOR]

sudo apt-get build-dep wine


I haven't got the updater to work but you should be able to manually update it. To start PerfectWorld you will need to run it fron the menu entry you created in step 6, the others will not work due to the updater not working. Also any other version of directx installed will cause issues, all the libraries I listed are needed, and you should use playonlinux because it uses the best version of wine and the script installs other libraries needed.

---

### Post by ppjdee on 2013-02-26
does the game run well for you?

---

### Post by vanquishedangel on 2013-03-09
It did when I played, about 14-40 fps but my system is old, and low end graphics but it was certainly playable also my internet was bad (2G lol) but yes for my system and internet it was great. They may have updated since then so it may be different.

---

