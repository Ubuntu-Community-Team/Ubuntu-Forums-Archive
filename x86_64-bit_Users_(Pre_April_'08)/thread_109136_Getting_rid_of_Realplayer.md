---
title: "Getting rid of Realplayer"
date: 2005-12-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2005-12-27
I madee the mistake of trying to install Realplayer on my Ubuntu-64 Breezy computer. The installation appeared to go OK, but Realplayer has never worked. It laumches, then instantly disappears. 

I really don't want it around. Unfortunately, I did not install it via Synaptic, because it is not listed in Synaptic. I don't recall exactly how I installed it -- probably a download file and some instructions on the web. The only way I know how to install and uninstall stuff is via Synaptic.

The annoying thing is that it hijacked all kinds of associations. For example, if I go to [www.allclassical.org](www.allclassical.org) and click on the "listen" link, Realplayer pops up and immediately disappears. Therefore, I am unable to listen to this station (or any other web station.) 

I looked all over but can't find instructions for getting rid of it. Right now I need 1) to get rid of it and, 2) to make some other app (xmms?) take over playing sound from websites.

Any suggestions welcome!

---

### Post by amohanty on 2005-12-28
Try the following:

> sudo updatedb
locate real | tee ~/Desktop/real-files.txt

Then open up the file on your desktop called real-files.txt
and then using nautilus wipe out the sucker.

WARNING: this may return some files that are not realplayer related, so use your judgement and be careful.

HTH
AM

---

### Post by fabs0028 on 2005-12-28
Well it seams there is an install.log file in the folder where realplayer was installed.
It summarizes all the installation maybe you should look at it to get rid of realplayer

---

### Post by John Jason Jordan on 2005-12-28
[QUOTE=fabs0028]Well it seems there is an install.log file in the folder where realplayer was installed.
It summarizes all the installation maybe you should look at it to get rid of realplayer[/QUOTE]
Thanks, I found that file, but the list of files and locations is enormous. Evidently it scattered billions and billions of files all over my computer.

I forgot to mention another problem -- Firefox crashes every time I click on a link to play sound in a web site. I need to find out how this is supposed to work. Evidently there are different audio players, but Firefox must be calling RealPlayer which, in turn, crashes, and crashes Firefox along with it. I should add that the only audio player that works for me is xmms. I have installed Mplayer and several others, but they either crash or won't launch, or something else is broken that makes them not work.

I just now tried reinstalling RealPlayer, thinking that some of its files may be missing. The reinstallation went fine, but there is no change in the problem.

What I'd like to do is fix Firefox so that it does not try to call RealPlayer. I looked all over in Firefox for a setting, but can't find anything. I looked in Tools > Extensions, but I have none installed. In Tools > Themes all I have is the Firefox default. Under Preferences > Downloads > Plugins I have a long list of file types for which Firefox seems to have plugins, but I can't figure out what plugin is being called for the different file types, or how to change the plugin.

All I want to do is listen to radio stations that broadcast over the internet. I don't care what program I use, as long as it works. If I can't get rid of RealPlayer, fine, as long as I can remove links to it so it is not called as the default audio player.

---

### Post by amohanty on 2005-12-28
in the location bar type:

> about:Plugins

this only shows you what apps are registered to handle what files. To remove the real plugin look in (I think - not sure - not on my box) /usr/share/mozilla/plugins for a bunch of .so files. Remove the real so file. Restart ff.

HTH
AM

---

