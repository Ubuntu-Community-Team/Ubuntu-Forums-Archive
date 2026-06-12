---
title: "opera not installing on AMD64"
date: 2006-06-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by desijays on 2006-06-13
I finally decided to quit windows once and for all. I've been on and off linux many times before. Each time switching back to windows because i had some problems with linux. But this time i'm convinced to sit myself through it all and solve any issues that may arise. 

I just installed Ubuntu 6.06 on my AMD 64 system this morning. I love it. Easy installations, everything was detected and even my internet was working. In the past i had run into network problems and couldn't access the internet. My uncle who was watching the installation was so amazed with ubuntu, he told me to write a copy for him as well right there. so he is probably installing it right now and facing the same problems i am  :sad: 

I love opera so very much. after installing ubuntu the first thing i looked for in the add/remove dialog and the synaptic manager was the opera package. Since i couldn't find it... I went directly to opera and downloaded the opera.deb package. But now when I try to install it, im getting an error saying Wrong architecture 'i386'. And the "install package" button is greyed out. i don't know what to do now.

Is there any way I can use opera on my AMD 64 system?.

Even the yahoo.deb package is not installing. It gives me the same error message.

I'm using the ubuntu meant for the 64bit AMD architecture. I thought that might be useful to let you know...

---

### Post by Hendrik van den Boogaard on 2006-06-13
Perhaps the same trick to install many i386 packages is to add '--force architecture' to the 'dpkg -i' command. Some more info about other programs that have problems with AMD64 are listed in 'my' thread: [http://ubuntuforums.org/showthread.php?t=191205](http://ubuntuforums.org/showthread.php?t=191205)

---

### Post by d0rift0 on 2006-06-13
The forcearchitecture option is the simple way of installing opera if you don't mind an ugly looking opera interface. If you do thenl a Chroot environment to run opera might not be such a bad idea.

[https://wiki.kubuntu.org/DebootstrapChroot?highlight=%28chroot%29](https://wiki.kubuntu.org/DebootstrapChroot?highlight=%28chroot%29)

Takes a little while but its worth it in the end, just installed it today :D Nice to finally have some decent fonts and colours !

---

### Post by desijays on 2006-06-13
I solved the problem albeit with some errors though... the url that helped me was [http://ubuntuforums.org/showthread.php?t=79618&highlight=opera+amd64](http://ubuntuforums.org/showthread.php?t=79618&highlight=opera+amd64)

---

### Post by Fedcer on 2006-06-13
If you don't mind using a beta version of Opera (which at least for me works very well) you don't have to install the static version, you can install the shared one without any problem.
Go here [http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/) and download the shared version of the debian package of opera. Then, do:

sudo dpkg -i --force-architecture "nameofthepackage".deb

My experiences with this beta version have been very good, but maybe you might prefer to stick with the stable one.

---

### Post by steabert on 2006-06-13
you can also run 32 bit ubuntu on AMD64

---

### Post by pdc303 on 2006-06-13
the latest Opera 9 beta is working out fine for me too.

Installing with --force-architecture seems to have caused no problems with any packages so far.

There is a thread which describes exactly which Opera 9 Beta package to install and how to do it.

---

