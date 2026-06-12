---
title: "Unable to stream asf in firefox32"
date: 2008-07-19
forum: x86 64-bit Users
---

### Post by Hoyland84 on 2008-07-19
I'm running Ubuntu 8.04.1 AMD64. Because of java and flash issues I am using Firefox32. Works great using java and streaming flash movies, such as YouTube, but I run in to trouble when trying to stream typical totem formats such as asf in Firefox. I don't know how I can get any plugin that can stream stuff like this to work in Firefox32.

Installing mplayer or helix doesn't work. At least not when installing it the standard way through apt-get or synaptics. I guess all those installations assume I'm using the standard Firefox 64.

---

### Post by Hoyland84 on 2008-07-19
Actually, using this site:
[http://fredrik.hubbe.net/plugger/test.html](http://fredrik.hubbe.net/plugger/test.html)
shows me that none of the formats can play in my browser.

I did use this HOWTO [http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537) and the automatic script to install firefox32, java and flash. mplayer does not seem to work with firefox after the installation

---

### Post by warp99 on 2008-07-20
To solve this problem I use a Firefox plugin called MediaPlayerConnectivity:

[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

This allows you to play embedded movies in any external player. You can also download the mozilla-mplayer plugins 32-bit .deb file, then extract the plugins and place them in you Firefox plugins directory. So just do the following:

Download the 32-bit deb file:

```
wget http://mirrors.kernel.org/ubuntu/pool/multiverse/m/mplayerplug-in/mozilla-mplayer_3.50-1ubuntu2_i386.deb
```

Extract the files from the package
```
dpkg -x mozilla-mplayer_3.50-1ubuntu2_i386.deb ~/some_tmp_folder
```

Then copy the plugins to your Firefox plugins directory:
```
sudo cp -r ~/some_tmp_folder/usr/lib/mozilla/plugins /path_to_firefox_folder/
```

and they work fine with the 32-bit browser on a 64-bit install. With both of these options installed you can switch between MediaPlayerConnectivity or the mplayer plugins very easily.

---

