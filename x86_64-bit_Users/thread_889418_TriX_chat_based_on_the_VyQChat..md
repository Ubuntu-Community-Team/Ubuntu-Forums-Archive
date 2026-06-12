---
title: "TriX chat based on the VyQChat."
date: 2008-08-14
forum: x86 64-bit Users
---

### Post by EMCGFX on 2008-08-14
My first attempt on building my own AMD64 deb package based on [http://ubuntuforums.org/showthread.php?t=51003&highlight=checkinstall]("http://ubuntuforums.org/showthread.php?t=51003&highlight=checkinstall") article.

I wanted to try Trix program, but since the author does not release AMD64 version, I've decided to try and build 64bit package my self. 

You can find it here, [http://dl.gravityfx.org/index.php?path=linux/]("http://dl.gravityfx.org/index.php?path=linux/") or on mirrors here [http://www.uploadjockey.com/download/8913845/trix_0.94-1ubuntu1_amd64.deb]("http://www.uploadjockey.com/download/8913845/trix_0.94-1ubuntu1_amd64.deb").

Have fun, I hope it helps some one ;-)

---

### Post by Gourgi on 2008-08-21
As far as i know checkinstall does NOT take care of the dependencies so i may have to install them.
i 'll try to install your deb and give you feedback.
Also i think you/we should contact the developer and ask him to officially distribute amd64.deb files.


I also use trix chat, a truly savior for me to talk with my 'windows' friends. a big big thanks to the developers.

BTW here is the 'Debian/Ubuntu' way to compile Trix:

first take care of the dependencies:
```

sudo apt-get install libqt3-mt-dev

```
then extract the tar.bz somewhere and
configure with the right qt dir:
```

./configure --with-Qt-dir=/usr/share/qt3

```

then if we want to install trix and have an option to uninstall it through synaptic we use checkinstall  :
```

sudo checkinstall

```
and hit 'enter' until checkinstall finishes questions

or the traditional way ... :
```

make 
sudo make install

```

---

### Post by EMCGFX on 2008-08-21
@Gourgi, Thanks for the help, this was my first deb release ;-) Will due this for second package.

When you installed it asked you for libqt3-mt-dev ??

---

### Post by Gourgi on 2008-08-22
> **EMCGFX said:**
> When you installed it asked you for libqt3-mt-dev ??
i just followed official Faq , question 2.
[http://trix.sourceforge.net/index.php?lang=eng&section=4](http://trix.sourceforge.net/index.php?lang=eng&section=4)
i think it is required in order to compile trix
i'll try it again on a live cd without libqt3 and i 'll post back.

---

### Post by Gourgi on 2008-08-22
hi i just donwloaded your .deb from here [http://dl.gravityfx.org/index.php?path=linux/](http://dl.gravityfx.org/index.php?path=linux/) and i tried it with a livecd.
your deb works ! it suggested me to install libaudio2 and libqt3-mt dependencies, trix was successfully installed and it worked as expected.
so no need for libqt3-mt-dev.

i think you should contact the authors of trix and discuss with them about adding your .deb to sourceforge.

It is really helpful to have a amd64.deb for 64 bit version of trix.

---

