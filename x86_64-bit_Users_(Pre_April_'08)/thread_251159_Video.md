---
title: "Video"
date: 2006-09-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sipheren on 2006-09-05
When I go to watch a video in player such as MPlayer, the video loads but before it plays the screen goes blank,and I have to log back in, its like the xserver gets reset.

I have the ati drivers installed, and as far as I can tell they are working.
This is my first ubuntu using x64 and Ati.

Any help would be good.

Cheers

Sipheren

---

### Post by FluffyElmo on 2006-09-05
Try running it from a terminal window, on my system the command is *gmplayer*, and see if there are error messages that might help.

My guess is that the output type is set to something incompatible with your video driver. Try editing *.mplayer/gui.conf* in your home directory. The line *vo_driver* should be changed to something compatible, *vo_driver = "x11,"* and *vo_driver = "xv"* are common values. 

If you get it working you can experiment with the possible values by right clicking in the movie window, selecting *Preferences* and then going to the *Video* tab. If it should stop working after trying a value you can change gui.conf again.

---

### Post by Sipheren on 2006-09-06
when I type it in the terminal, it does the same thing when I load a video. the only thing in the .mplayer dir is a config file with nothing written in it??

when the screen goes blank it is like a cammand line thing, it says something about automic and X11, but its very quick so I dont get a chance to really see it.

---

### Post by kuja on 2006-09-06
I would check your /var/log/Xorg.0.log file to see if it contains any errors? Also, which video driver are you using?

---

### Post by Sipheren on 2006-09-06
I am using the ati drivers from the ati website, I installed them by following the 'howto' on here.

---

### Post by Perfex on 2006-09-18
I have the same exact problem, I will try to play a video and it will load the app, then black screen then login screen

using 8.28.8 ATi drivers - tutorial used to install them [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually)

I have attached my Xorg log if anyone can decifer it

---

### Post by juicemansam on 2006-09-19
Try *mplayer video.mpg 2>&1 > mplayer.log*. That way there's a log of what mplayer is doing up until the moment of the crash. Post those result, but beware that Mplayer adds return carriages and the output will probably need some editing, but not likely since it doesn't seem that it plays anything before the crash.

---

