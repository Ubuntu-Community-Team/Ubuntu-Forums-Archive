---
title: "Moviefly and Ant Movie Catalog problems..."
date: 2007-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Arasfang on 2007-01-25
Hi!

I used a program called Ant Movie Catalog in windows before switching over to linux.

My first thought was to use the program under wine since I read it should work. Yea it
runs very nice but I can't get swedish letters when I type in the program. I can see those letters on the imported stuff but I can't type them.

I can use swedish letters in all other applications in KDE. Also tried it in wine Notepad, doesnt work either.

I also tried starting Ant Movie Catalog with LANG=se_SV.UTF-8 but it still doesnt give me swedish characters.

Is there a solution for this?

The second alternative I have is using the python port of Ant Movie Catalog called Moviefly. But I get an error trying to install it.

```
checking for Qt... ls: /lib/libqt*: No such file or directory
/usr/lib/libqt-mt.la    /usr/lib/libqt-mt.so.3.3    /usr/lib/libqtmcop.so
/usr/lib/libqt-mt.prl   /usr/lib/libqt-mt.so.3.3.6  /usr/lib/libqtmcop.so.1
/usr/lib/libqt-mt.so    /usr/lib/libqtmcop.a        /usr/lib/libqtmcop.so.1.0.0
/usr/lib/libqt-mt.so.3  /usr/lib/libqtmcop.la
yes:
    QT_CXXFLAGS=-I/usr/include/qt3
    QT_DIR=
    QT_LIBS=-l/usr/lib -l  -lSM -lICE  -lX11 -lXext -lXmu -lXt -lXi
    QT_UIC=/usr/bin/uic
    QT_MOC=/usr/bin/moc
checking correct functioning of Qt installation... failure
configure: error: Failed to find matching components of a complete
                  Qt installation. Try using more options,
                  see ./configure --help.

```

I have both QT3 and QT4 installed as I can see...

My hope is to get Ant Movie Catalog working, that would be the best solution for me since it has lookups on swedish movie sites.

Thankful for any answers that can help me =)

/Mattias

---

### Post by nicoladimaria on 2007-04-15
bump
why do we need to use wine for a stupid qt error ?

EDIT: I installed the program
make sure you have ALL these packages (yes all)

perl             (>= 5.8.4)
python2.3-dev    (>= 2.3.5) 
python-qt3       (>= 3.13) 
pyqt-tools       (>= 3.13)
python-qt-dev    (>= 3.13)
sip4             (>= 4.1.1)
qt3-dev-tools    (>= 3.3.4)
libqt3-headers   (>= 3.3.4)
libqt3-mt-dev    (>= 3.0.3)
libqt3-dev       (>= 3.0.3)
python           (>= 2.3)
python-qt3       (>= 3.13)
perl             (>= 5.8.4)
libwww-perl
liburi-perl
transcode
eject


although I needed to use 
```
 ./configure --with-Qt-dir=/usr/share/qt3/
```
to get over the qt problem
to find your qt3 directory simply type```

sudo updatedb && locate qt3
```
it may take several minutes

---

