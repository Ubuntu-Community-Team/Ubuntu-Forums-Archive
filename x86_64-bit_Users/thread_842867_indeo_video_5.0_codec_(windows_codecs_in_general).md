---
title: "indeo video 5.0 codec (windows codecs in general)"
date: 2008-06-27
forum: x86 64-bit Users
---

### Post by kung fu buntu on 2008-06-27
How do I solve this?

32bits users fix this by installing the win32codecs package, but I've tried to do the same and this doesn't work :(
I have my windows codecs in /usr/lib/codecs/

Can you play this:
[http://server.cs.ucf.edu/~vision/projects/triview/collision01.avi](http://server.cs.ucf.edu/~vision/projects/triview/collision01.avi)

There is a similar thread in [http://ubuntuforums.org/showthread.php?t=569402&highlight=indeo](http://ubuntuforums.org/showthread.php?t=569402&highlight=indeo) but it isn't 64 bits oriented so I'm guessing people in this forum may be more helpfull.

---

### Post by kung fu buntu on 2008-06-29
As with a lot other stuff in 64bit linux, I fixed the problem in my ia32 chroot :-/


I don't think this is a proper solution, so I will leave this thread un-solved.

---

### Post by pixel :-) on 2008-06-30
uninstall w64codecs if installed

sudo apt-get install ia32-libs
download and install this[http://rapidshare.com/files/126080080/mplayer32_1-2_all.deb.html]("http://rapidshare.com/files/126080080/mplayer32_1-2_all.deb.html")
sudo dpkg -i mplayer32_1-2_all.deb
install w32codecs

mplayer32 collision01.avi

a very old package that i had,i adapted it for hardy,this package has no dependencies what so ever,It does work for me,if it doesn't for you,post me back the output.You are suposed to use this only as a last resort.

---

### Post by kung fu buntu on 2008-06-30
Thanks for your comment but in the same way that IMO the chroot isn't the proper solution, I don't think yours is as well.
Now that I think about it... there probably isn't a proper solution for this one :s

Besides, I prefer SMPlayer... which is 10^10 times better than any other media player :P

---

### Post by pixel :-) on 2008-06-30
//Thanks for your comment but in the same way that IMO the chroot isn't //the proper solution, I don't think yours is as well.
Noncence,you just whant to whatch a movie,mplayer32 is the simplest solution,no chroot, no emulation,native speed. This is a proper solution,if you recompile a resent one.

//Besides, I prefer SMPlayer
Hey Smplayer is just a front end to mplayer,smplayer works with mplayer32 too,but you have to change the configurations.

A little hack.with "-ini-path" option, you can set up a smplayer32 lancher,that is simply smplayer with a different counfig file, that tels it to use mplayer32,and the drivers to use.So one click,and the video runs,in your fetish player.I don't think that you can chose mplayer executable from within the configs for individuall files.

Even beater,maybe,mencoder32, you can convert to what you want.
[http://www.stud.ntnu.no/~grannas/debs/mencoder32]("http://www.stud.ntnu.no/~grannas/debs/mencoder32")

keep in mind that mplayer32 is old,you don't want to use it all the time.

---

