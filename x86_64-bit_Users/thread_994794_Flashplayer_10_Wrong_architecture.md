---
title: "Flashplayer 10 Wrong architecture"
date: 2008-11-27
forum: x86 64-bit Users
---

### Post by atleastitsnotcrack on 2008-11-27
As if there isn't enough threads on the topic of what I would regard as the second evil empire, adobe, microsoft being the first, I'd have to go add another one!

Right so anyways to the point

Go to adobe get flash, the typical user way via the deb file for x86 (so the site leads you to believe) and open as one would with GDebi package installer the ERROR: Wrong architecture 'i386' is reported for status.

So after searching around found this script credited to  Romeo-Adrian Cioaba [email]romeo.cioaba@spotonearth.com[/email] which goes

echo "Stopping any Firefox that might be running"
sudo killall -9 firefox

echo "Removing any other flash plugin previously installed:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

echo "Installing ia32-libs and nspluginwrapper"
sudo apt-get install ia32-libs nspluginwrapper

echo "Getting libs"
sudo getlibs -p libcurl3
sudo getlibs -p libnss3-1d
sudo getlibs -p libnspr4-0d

echo "Installing Flash Player 10"
cd ~
wget  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)
tar zxvf install_flash_player_10_linux.tar.gz
sudo cp install_flash_player_10_linux/libflashplayer.so /usr/lib/mozilla/plugins/echo "Stopping any Firefox that might be running"
sudo killall -9 firefox

echo "Removing any other flash plugin previously installed:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

echo "Installing ia32-libs and nspluginwrapper"
sudo apt-get install ia32-libs nspluginwrapper

echo "Getting libs"
sudo getlibs -p libcurl3
sudo getlibs -p libnss3-1d
sudo getlibs -p libnspr4-0d

echo "Installing Flash Player 10"
cd ~
wget  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)
tar zxvf install_flash_player_10_linux.tar.gz
sudo cp install_flash_player_10_linux/libflashplayer.so /usr/lib/mozilla/plugins/
rm -rf ~/install_flash_player_10_linux/
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

echo "Linking the libraries so Firefox can find it."
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/

echo "Done :-)"
rm -rf ~/install_flash_player_10_linux/
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

echo "Linking the libraries so Firefox can find it."
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/

echo "Done :-)"

Should work right?
NO!

nspluginwrapper reports the file libflashplayer.so is not a valid NPAPI plugin

I read somewhere in forums that a version higher then 0.9.91.5 of nspluginwrapper is needed (V1.14 to the best of my memory) however I cannot get a higher version anywhere and the script updates it anyway.

Have I gone down the wrong path? I think so wanting to install flash in the first place was where I went wrong.

New to linux so I have little knowledge which is dangerous but no fool so go easy on me

---

### Post by viciouslime on 2008-11-27
The 64 bit alpha is VERY stable, I haven't had a single issue with it yet. I would just use that and save yourself a LOT of trouble with nspluginwrapper.

[http://labs.adobe.com/downloads/flashplayer10.html]("http://labs.adobe.com/downloads/flashplayer10.html")

---

### Post by atleastitsnotcrack on 2008-11-27
Thanks, I'll give it a go!

---

### Post by atleastitsnotcrack on 2008-11-27
Curses still using wrong sound card - I'll crack that one another day I think too busy.

So does version 10 not use the ALSA sound driver either anyone?

---

### Post by sonicb00m on 2008-11-27
works ok for me with alsa

---

### Post by jespdj on 2008-11-27
So, are you just trying to install Flash 10 on your 64-bit system?

You're making it much more difficult than necessary. Just install the package **flashplugin-nonfree**. This will install the 32-bit version of Flash 10 along with nspluginwrapper (necessary to make the 32-bit plugin work on 64-bit Firefox).

Don't try downloading it from Adobe and installing it yourself if you don't have any special reason to do that.

---

### Post by sonicb00m on 2008-11-30
> **jespdj said:**
> So, are you just trying to install Flash 10 on your 64-bit system?

You're making it much more difficult than necessary. Just install the package **flashplugin-nonfree**. This will install the 32-bit version of Flash 10 along with nspluginwrapper (necessary to make the 32-bit plugin work on 64-bit Firefox).

Don't try downloading it from Adobe and installing it yourself if you don't have any special reason to do that.


I think his problem is almost the opposite, almost looks like he is trying to install the 64 bit native with the ndiswrapper.

I would remove all that stuff you've done and manually install the 64 bit native which is working very well and completely stable for me (with the small amount of flash stuff I use - kids games and youtube).

---

### Post by cariboo on 2008-12-01
I have to say the 64bit plugin finally works the way you would expect it and it was easy to install, just download, untar and copy to /usr/lib/mozilla/plugins.

I'm using it both in Intrepid and Jaunty and haven't had a crash yet. I've watched more flash videos in the last week then I have in the last year. :)

edit: synaptic even said that nspluginwrapper was no longer needed.

Jim

---

### Post by jespdj on 2008-12-01
> **sonicb00m said:**
> I think his problem is almost the opposite, almost looks like he is trying to install the 64 bit native with the ndiswrapper.
You mean **nspluginwrapper**, which is a wrapper to make the 32-bit Flash plugin work on 64-bit Firefox (which you obviously don't need if you're using the 64-bit native Flash plugin).

ndiswrapper is something totally different, it's a wrapper to make Windows drivers for wireless networking cards work on Linux.

---

### Post by VastOne on 2008-12-03
Ditto...

Several installs of 64bit machines and all are functioning perfectly with the new alpha plugin.  The time for each video to load is at a minimum 50% faster and all machines are playing up to 5 at any one time. Whatever way you can get it to work, do it.  I followed Cariboo907's method, getting it very easily done.  I made a mistake on one machine by grabbing the wrong file from adobe, but that was easily corrected but looking at help > about:? > about:plugins in Firefox, or simply Alt P in FF

VastOne

> **cariboo907 said:**
> I have to say the 64bit plugin finally works the way you would expect it and it was easy to install, just download, untar and copy to /usr/lib/mozilla/plugins.

I'm using it both in Intrepid and Jaunty and haven't had a crash yet. I've watched more flash videos in the last week then I have in the last year. :)

edit: synaptic even said that nspluginwrapper was no longer needed.

Jim

---

### Post by chongzi35 on 2008-12-03
High temperature **[cast steel valves](http://www.valvesupplier.net/cast-steel-gate-valves.htm)** are designed and manufactured to provide reliable shutoff and smooth operation under a high temperature environment. The specified bolt torque is maintained during valve assembly, using specialized torque limiting equipment, to prevent valves from leaking between the valve body and bonnet and providing reliable long term operation once the [cast steel valve]("http://www.valvesupplier.net/cast-steel-gate-valves.htm") is put into service.

---

### Post by sonicb00m on 2008-12-08
> **jespdj said:**
> You mean **nspluginwrapper**, which is a wrapper to make the 32-bit Flash plugin work on 64-bit Firefox (which you obviously don't need if you're using the 64-bit native Flash plugin).

ndiswrapper is something totally different, it's a wrapper to make Windows drivers for wireless networking cards work on Linux.

yes that is what i mean :p

---

