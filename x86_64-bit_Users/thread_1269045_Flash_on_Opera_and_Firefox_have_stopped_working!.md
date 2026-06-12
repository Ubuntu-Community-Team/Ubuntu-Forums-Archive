---
title: "Flash on Opera and Firefox have stopped working!"
date: 2009-09-17
forum: x86 64-bit Users
---

### Post by kylejamestobin on 2009-09-17
Hey guys I'm a bit of a noob and I could use some help.

So I'm running firefox and opera and as of recently I've been getting some craziness.  I tried going to firefox 3.5 and when i removed 3.0 and re installed 3.5 all I get now is "server not found"  Opera still works fine for websurfing but it won't play any flash video.  If I go to hulu in Opera everything works except for videos.  I can still see the flash "slideshows" but when I try to start an actual episode all I get is sound and the gray to black motif of hulu continues across where the video should be playing.

I'm running Jaunty 64 bit and Opera 10.  I have a feeling I must have uninstalled something accidentally when I was installing firefox 3.5.

Any suggestions?

---

### Post by quixote on 2009-09-18
See if "flashplugin-installer" and "flashplugin-nonfree" are installed in synaptic (System > Administration > Synaptic).  If not, install them.  I don't know if hulu also maybe wants java.  If so, check that the following are installed too: java-common, sun-java6-bin, sun-java6-jre, sun-java6-plugin.  This may not solve the problem, but at a minimum you need the flashplugins to run flash content.

Have you rebooted since your new install of FF?  It's weird that you should be getting server not found.  Is that true of all sites?  Including eg [www.google.com?](www.google.com?)  It doesn't seem like that could be a FF problem, although if it wasn't, Opera should have the same problem.

---

### Post by HappyFeet on 2009-09-19
Remove whatever flash (or gnash) you have installed first.

Go [here]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz") and download the 64bit flash file. Right click and extract here. Then copy the resulting libflashplayer.so file. Then go to your home folder and do Ctrl-H. You will now see the hidden folders that start with a dot. Open the .mozilla folder and create a new folder called plugins. Paste the libflashplayer.so file there. Close out and restart firefox.

---

### Post by quixote on 2009-09-19
Good point!

---

