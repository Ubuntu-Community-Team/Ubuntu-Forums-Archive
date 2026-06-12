---
title: "ProjectM for Jaunty x86-64"
date: 2009-04-25
forum: x86 64-bit Users
---

### Post by SqRt7744 on 2009-04-25
Hello I compiled the latest packages for ProjectM, the "Milkdrop" visualization port for Linux. It was a tad of a pain so I thought I'd post them here in case anybody else is interested. The packages in the repository are only the libvisual plugin, which isn't terribly useful- especially since Totem won't recognize it.

Anyway, if you install these packages (may also need some qt4 libs), you'll have an entry in the Apps->Sound & Video for ProjectM-Pulseaudio. Let me know if there are any additional dependencies...

Save them somewhere where there aren't any other debs and then install them with dpkg -i *.deb

happy visualizing


if you don't want my packages you can do this yourself:
1: download projectM-pulseaudio, libprojectM-qt, libprojectM from the homepage: [http://sourceforge.net/project/showfiles.php?group_id=104201](http://sourceforge.net/project/showfiles.php?group_id=104201)
2: extract libprojectM, move the other two into the directory created by tar and extract them as well.
3: sudo apt-get build-dep libprojectm2
4: sudo apt-get install libqt4-dev ftgl-dev checkinstall build-essential libpulse-dev
5: sudo ln -s /usr/include/FTGL/ftgl.h /usr/include/FTGL/FTGL.h  (yah this is kinda annoying but it won't compile otherwise)
6: ...now you have to do the rest in the CORRECT order.
    a) in the libprojectM directory: ccmake .  [don't forget the DOT], when menu appear 'c' to configure, change /usr/local to /usr, 'g' to      generate and exit. cmake . -DCMAKE_BUILD_TYPE=RELEASE, now make, then sudo checkinstall
    b) do the same for libprojectm-qt, and finally for projectm-pulseaudio
7: if you mess up on one of the packages, you can start over by deleting the backup* files that checkinstall created, make clean, rm CMakeCache.txt and starting over.

---

### Post by SqRt7744 on 2009-05-29
Ubuntu geek has now also posted a howto!

[http://www.ubuntugeek.com/ubuntu-howto-install-projectm-audio-visualizer.html](http://www.ubuntugeek.com/ubuntu-howto-install-projectm-audio-visualizer.html)

---

### Post by punkrockguy318 on 2009-06-17
Wow, how does this topic have no replies?

ProjectM (winamp/Milkdrop on win) is the first thing I install on all my computers.  Anyway, thanks so much for these packages they work pretty well

I get some crashes every now and then on this machine compared to my other machine where I have this installed from source, but it might have something to do with the shitty ATI driver.

Anyways, thanks so much you're the man

---

### Post by SqRt7744 on 2009-06-24
yeah I get the crashes too, not sure what's that about, haven't looked at the backtrace or anything yet. Hopefully they'll fix the bug in a new version...

---

### Post by SqRt7744 on 2009-06-24
ok i just compiled the new version which is hopefully more stable, but i can't figure out how to change the attachments to the new versions... anyone know if this is possible? I think I'm just not noticing some incredibly obvious button staring me in the face...

EDIT updated:

..and the button is 'go advanced'

---

### Post by Crimson_Fox on 2009-07-10
It's running like a million bucks on my system, thanks!

---

