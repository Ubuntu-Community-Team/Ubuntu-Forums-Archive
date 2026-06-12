---
title: "Trouble Compiling MythTV, Edgy, 64-bit"
date: 2006-12-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by brandon_r87 on 2006-12-07
Hi,

Here is what I've run
```
make[2]: ./configure --prefix=/usr --enable-xvmc --enable-opengl-vsync --enable-proc-op
t --dvb-path=/usr/src/linux-headers-2.6.17-10/ --enable-dvb
```

```
$ qmake mythtv.pro
$ make
```

And here's the error I get on make
```
/usr/bin/ld: cannot find -lqt-mt
collect2: ld returned 1 exit status
make[2]: *** [libmythavcodec-0.20.so.0.20.0] Error 1
make[2]: Leaving directory `/home/mythtv/mythtv-0.20/libs/libavcodec'
make[1]: *** [sub-libavcodec] Error 2
make[1]: Leaving directory `/home/mythtv/mythtv-0.20/libs'
make: *** [sub-libs] Error 2
```

I can post more, but I don't know what stuff is necessary and unnecessary aside from the obvious.

Thanks,
Brandon

---

### Post by RAOF on 2006-12-07
Is there any particular reason you're compiling mythtv?  From memory, 0.20 got into Edgy's universe, so you should be able to just install the **mythtv** package.

If there's some special reason you want to compile it, you're missing the QT3-libraries.  They're almost certainly in the **libqt3-mt-dev** package.

---

### Post by superm1 on 2006-12-08
Yes mythtv is in universe/multiverse.  Only reason you would need to compile is if you needed something that included newer 0.20-fixes or svn.

If you need a guide to get started explaining myth on ubuntu, see
[http://help.ubuntu.com/community/MythTV](http://help.ubuntu.com/community/MythTV)

---

### Post by eclisse on 2006-12-20
Hello!

I've also sent an email to superm1, sorry for the noise, but I've found that forums become a great reference for other users in the future.

If version 0.21 is still far from Ubuntu repositories (see the XvMC problem at the URL below) could you please point me to a good rsource on how to compile an Ubuntu package from MythTV sources ?

[http://svn.mythtv.org/trac/ticket/2412](http://svn.mythtv.org/trac/ticket/2412)

Thank you very much.

Best regards,
      Paolo

---

### Post by superm1 on 2006-12-20
> **eclisse said:**
> Hello!

I've also sent an email to superm1, sorry for the noise, but I've found that forums become a great reference for other users in the future.

If version 0.21 is still far from Ubuntu repositories (see the XvMC problem at the URL below) could you please point me to a good rsource on how to compile an Ubuntu package from MythTV sources ?

[http://svn.mythtv.org/trac/ticket/2412](http://svn.mythtv.org/trac/ticket/2412)

Thank you very much.

Best regards,
      Paolo
We are quite a ways off from building packages of current things in SVN.  Generally its better to track 0.20-fixes, so if the resolution to this makes it into 0.20-fixes, it should get into an Ubuntu package.  If you would like to build a package yourself however, I'll give you a quick overview whats involved.

1) Install devscripts, build-essential, & debhelper
2) apt-get source mythtv
3) apt-get build-dep mythtv
4) Download the mythtv svn sources
5) Copy the debian directory to svn sources
6) Remove patches from debian/patches/00list that won't cleanly apply
7) Increment the debian/changelog by adding a new entry similar to 0.20-6ubuntu0unofficial1.  The big important thing here is to make sure you change the ubuntu1 to be ubuntu0unofficial1.  This guarantees that you can still upgrade to an Ubuntu official build when new packages are released & you upgrade releases if you would like to.
8) Build the packages with dpkg-buildpackage
7) Install the packages, and open up synaptic/adept.  "Lock" the versions of all the packages.  Now when you upgrade releases, any locked packages won't be upgraded, but if you would like to, your able to unlock them and they will upgrade.

I'm not going to go into too much more detail here, because building does have lots of oddities, idiosyncrasies, annoyances, etc.  Also, this will install a lot of build-time dependencies in your current working environment.  Normally, I use pbuilder instead to guarantee that these will build and install anywhere.  Thats a whole separate thing to explain.  So the short version is, the packages that you build using this method you really shouldn't redistribute for that exact reason.

---

### Post by eclisse on 2006-12-20
Thank you very much !

I'll give it a try during christmas holidays...

Best regards,
       Paolo

---

### Post by eclisse on 2007-01-01
Hello, Mario !

Great directions, I was able to compile my own .deb packages while I wait for the official release from you. Ah, btw, that really solved my Via EPIA Mpeg acceleration problem.

Now I've got a slight problem and maybe you can help me.

All plugins compile and install correctly save for mytharchive.
The compilation goes apparently well, and the installation too, but then I don't see the mytharchive menus when I open the frontend.

But I get some strange messages of missing files (see .deb compilation log attached). Maybe you can tell me what I've missed in my compilation ?

Thank you very much, and a Happy New Year !

Best regards,
     Paolo

---

### Post by superm1 on 2007-01-01
> **eclisse said:**
> Hello, Mario !

Great directions, I was able to compile my own .deb packages while I wait for the official release from you. Ah, btw, that really solved my Via EPIA Mpeg acceleration problem.

Now I've got a slight problem and maybe you can help me.

All plugins compile and install correctly save for mytharchive.
The compilation goes apparently well, and the installation too, but then I don't see the mytharchive menus when I open the frontend.

But I get some strange messages of missing files (see .deb compilation log attached). Maybe you can tell me what I've missed in my compilation ?

Thank you very much, and a Happy New Year !

Best regards,
     Paolo
Paolo,
Hi, glad to hear that your compilation went smoothly.  Do you by chance know what patchesets particularly got your via mpeg acceleration going better?  We're not going to move up to a direct SVN checkout for stability reasons, but if you know which SVN patches do this, i'll be glad to add those exact patches into the official ubuntu packages.

For the plugins, did you follow a similar procedure to build, or are you using the plugins from official packages?

---

### Post by eclisse on 2007-01-02
Hi, Mario.

From what I read from ticket 2412 looks like changeset 11327 (see quote below)

> 11/09/06 08:32:42 changed by anonymous  ¶

Thanks DannyCan?!

I just patched 0.20-fixes (checked out this afternoon) with changeset 11327 from trunk. It almost applies cleanly. 'patch' complains about one hunk, because the change has already been made, so it can be ignored.

With it, my XvMC processor utilization drops back to 0.19 levels.


Sorry, I'm not very familiar with SVN and the terms involved. I hope this information is useful to track down the right patch...

As for the mythplugins, I've downloaded the source from your repository, then copied debian folder into the SVN version, cleaned out patches that didn't apply, changed version in changelog and then recompiled using fakeroot. What makes me suspicious is that there are errors of missing files in the output, but no blocking error...

Thank you for your time !

Best regards,
      Paolo


best regards

---

### Post by gyro on 2007-01-17
Hello I am trying to compile mythtv and have found this thread very useful.  However I have one question.  When you say copy the debian directorys what do you mean?  I have searched but cannot seem to find the directories you are talking about.

thanks-

brian

---

### Post by superm1 on 2007-01-17
> **gyro said:**
> Hello I am trying to compile mythtv and have found this thread very useful.  However I have one question.  When you say copy the debian directorys what do you mean?  I have searched but cannot seem to find the directories you are talking about.

thanks-

brian
When you apt-get source mythtv, this is in the extracted directory.

---

### Post by sirdilznik on 2007-12-11
Great guide.  Thank you very much.  I used the ```
./configure --prefix=/usr
make
sudo checkinstall
``` method to build the package.  Otherwise I followed the guide to the letter.  Everything built and installed correctly.  There are occasional graphical glitches with the menus but nothing major and easily circumvented.  Everything seems to be running pretty well so far.  I installed SVN for the playback fixes but got an unexpected bonus as the scan function was now able to detect a couple of OTA ATSC channels that I didn't get before.

Thanks again for the excellent guide.

---

