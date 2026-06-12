---
title: "Developing Applications for Ubuntu 64-bit (Intel)"
date: 2007-11-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mattuntu on 2007-11-08
Hello everyone!!:guitar:,
Very new to the Linux(Ubuntu) world.  But not to programming in general.  Does any body know where I could find a good application development package for 64-bit (Ubuntu) Linux?  Something that doesn't require a PHD to setup and use?:confused::)

---

### Post by stmiller on 2007-11-08
Check out Kdevelop, or QT4 Designer. Kdevelop is sort of like XCode in OS X, roughly speaking.

---

### Post by azbarcea on 2007-11-09
what Programing Language do you use?

solution:
1. eclipse - for almost anything ... 
2. emacs - text editor
3. kate - a text editor for many many things
4. Kdevelop

should I continue ? be more specific on language and scope!

---

### Post by Mattuntu on 2007-11-09
> **azbarcea said:**
> what Programing Language do you use?

solution:
1. eclipse - for almost anything ... 
2. emacs - text editor
3. kate - a text editor for many many things
4. Kdevelop

should I continue ? be more specific on language and scope!

Sorry about that:smile:, C/C++.

stmiller: "Check out Kdevelop, or QT4 Designer."
Thanks, I'll do that

---

### Post by Mattuntu on 2007-11-11
PLEASE:( Tell me there is an easier way to install kdevelop (see below):confused:
To a person whose used linux for years this is normal business, but to a new person this is command line hell.  I use ubuntu 64-bit, I like Ubuntu, it installed on my hardrive virtually no problems(except for it wanting another partitian for the swap file, that sucked!), and it booted all the way without a single crash! .  How ever, the install process for new software is terrible, this REALLY needs to be worked on in future versions of Ubuntu.  I had previous DOS command line experience, which helped me a lot with the install process,  but for a new user who doesn't have that experience, it could be a real turn-off and back to windows/mac they go. There is no way I'm going to type all that BS below!  This is the kind of thing that should have been pre-installed to begin with, ready to go.  Having all the IDE programming and package upload tools pre-installed would be a great help in the overall development of Linux/Ubuntu applications.  Hopefully this will also be rectified in future versions of Ubuntu/Linux.  End of Complaint.

>    1. Before continuing please check if your computer has the required software installed.

   2. Get the sources for the KDE/3.5 branch like is explained above.

   3. Initialize the build system:

          $ cd kdevelop
          $ make -f Makefile.cvs

   4. In order to compile and install KDevelop on your system, type the commands (we assume you have bash shell) from below in the base directory.

          $ export KDEDIR=/where/your/kde3/is
          $ export QTDIR=/where/your/qt3/is
          $ export KDEVELOPDIR=/where/kdevelop/will/be/installed
          $ export KDEDIRS=$KDEVELOPDIR:$KDEDIR
          $ export LD_LIBRARY_PATH=$QTDIR/lib:$KDEDIR/lib:$LD_LIBRARY_PATH
          $ export LIBRARY_PATH=$QTDIR/lib:$KDEDIR/lib:$LIBRARY_PATH
          $ export PATH=$KDEVELOPDIR/bin:$QTDIR/bin:$KDEDIR/bin:$PATH

      Note: For obvious reasons you should edit the first three lines to match your configuration!
      On RPM based linux distributions, you can find the location of your Qt3 and KDE3 directories using the configuration program of your linux distribuition or simply issuing "rpm -ql qt3" and "rpm -ql kdebase3".
      If you are a gentoo user and want to use ctags then you need to issue:

          ln -sf /usr/bin/exuberant-ctags /usr/bin/ctags



   5. The next step is to configure it, to find out more about all the available configure options invoke:

          $ ./configure --help

      Here is an example of a debug-compiled version:

          $ ./configure --enable-debug=full --prefix=$KDEVELOPDIR --with-kdelibsdoxy-dir=$KDEDIR/share/doc/HTML/en/kdelibs-apidocs

      Here is an example of a release-compiled version:

          $ ./configure --prefix=$KDEVELOPDIR --with-kdelibsdoxy-dir=$KDEDIR/share/doc/HTML/en/kdelibs-apidocs

      You can avoid compiling some KDevelop components that you do not need, for example, I use the following configure command:

          $ ./configure --enable-debug=full --prefix=$KDEVELOPDIR --with-kdelibsdoxy-dir=$KDEDIR/share/doc/HTML/en/kdelibs-apidocs --disable-ada --disable-bash --disable-fortran --disable-haskell --disable-java --disable-pascal --disable-perl --disable-php --disable-python --disable-ruby --disable-sql --disable-antproject --disable-genericproject --disable-scriptproject --disable-trollproject --disable-clearcase --disable-perforce --disable-subversion

   6. Finaly you can build it and install it:

          $ make
          $ make install (as root, using for example the "su" command)

      If for some reason the make command fails you can force it to ignore errors by adding the -k option like this:

          $ make -k
          $ make -k install (as root)

      Depending on the error gravity you might end up with a working or non-working version of kdevelop. So do the "make -k install" at your own risk!!!. 

---

### Post by Steveway on 2007-11-11
Kdevelop should be in the repositories.
So you should be able to easily install it with Synaptic.
Or type this in a terminal: sudo apt-get install kdevelop

---

### Post by Mattuntu on 2007-11-11
> **Steveway said:**
> Kdevelop should be in the repositories.
So you should be able to easily install it with Synaptic.
Or type this in a terminal: sudo apt-get install kdevelop

Thanks, But tried both methods, but keeps telling me it cannot install certain packages:
Depends: kdelibs4c2a but it is not going to be installed
 Depends: libapr1  but it is not installable
 Depends: libaprutil1  but it is not installable
 Depends: libaudio2  but it is not installable
 Depends: libcvsservice0 (>=4:3.5.7-1) but it is not installable
 Depends: libqt3-mt (>=3:3.3.8really3.3.7) but it is not installable
 Depends: libsvn1 (>=1.4) but it is not installable
 Depends: kdebase-bin  but it is not installable

---

### Post by Cappy on 2007-11-11
Try going to **System> Administration> Software sources> and Check all of the boxes** and then try either way again.

---

### Post by azbarcea on 2007-11-12
> **Mattuntu said:**
> Thanks, But tried both methods, but keeps telling me it cannot install certain packages:
Depends: kdelibs4c2a but it is not going to be installed
 Depends: libapr1  but it is not installable
 Depends: libaprutil1  but it is not installable
 Depends: libaudio2  but it is not installable
 Depends: libcvsservice0 (>=4:3.5.7-1) but it is not installable
 Depends: libqt3-mt (>=3:3.3.8really3.3.7) but it is not installable
 Depends: libsvn1 (>=1.4) but it is not installable
 Depends: kdebase-bin  but it is not installable

If u are a developer, U certainly want to understand first what is happening:

1. '''apt''' is a package manager for debian based OS's (like Ubuntu also). There are different UI's to this program, including Synaptic, Adept (you should find them in Settings).

if the command:
```

apt-get install kdevelop

```

fails ... than, there must be something wrong with repositories ... e.g. Independent packages are not available from that repository (and you should add more). Depending on the distrubution u have: 

```

lsb_release -a

```

If u have Gutsy Gibbon then ... read here:
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method).

After all this:
```

apt-get install kdevelop

```

---

### Post by Mattuntu on 2007-11-12
[SIZE="3"]Thanks!:D azbarcea, 
     That manual install info did the trick. It downloaded a bunch of stuff, and then I installed kdevelop, which in-turn, downloaded a bunch more stuff.  And now everything appears to be working.  Thanks for everyones help.[/SIZE]

---

