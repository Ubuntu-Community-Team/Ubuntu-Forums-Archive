---
title: "Can't run latest Eclipse on 64 bit Feisty"
date: 2007-06-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by bronson on 2007-06-29
The Eclipse project just launched Europa.  When I try to launch it on my 64 bit Feisty box, I get:

(eclipse:11511): Gtk-WARNING **: Error loading theme icon for stock: Unable to load image-loading module: /usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so: /usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so: cannot open shared object file: No such file or directory

It's right, there is no svg_loader.so in lib32.  Why not?

I found [http://www-space.eps.s.u-tokyo.ac.jp/~amano/ubuntu.html](http://www-space.eps.s.u-tokyo.ac.jp/~amano/ubuntu.html) which says (through Google translation), "However, as for this cause the fact that svg_loader.so is not prepared in libgtk of 32bit edition seems like cause. Compiling /etc/gtk-2.0/gdk-pixbuf.loaders.32, perhaps the one which comment out it does the part of svg_loader.so is good."

Is this a bug in Feisty?  Is the 32 bit libgtk build incomplete?

    - Scott

---

### Post by praxis22 on 2007-06-29
If you're using a 64bit operating system, my guess is that you don't get any 32 bit libs (or shared objects) by default. I had a problem building gcc 4.2.0 yesterday because it was looking for a 32bit library include file, (which also didn't exist) when I told the build not to generate 32 bit libraries, (in addition to the normal 64 bit ones) it ceased being a problem.

Why don't you do what you found, download the source and compile it yourself.

```

sudo apt-get build-essential makeinfo expect flex bison libtool automake autoconf

```

That should get you a working build environment, then all you should need to do is read the instructions then
 ./configure --<flags>
make
make install

In theory at least :)

---

### Post by praxis22 on 2007-06-29
sorry wrong thread :)

---

### Post by bronson on 2007-06-30
Yeah, building Eclipse from scratch sounds like a heck of a lot of work.  It would probably be easier to just find a 32 bit computer.  :)

I found the answer: the Eclipse project neglected to create any turnkey 64 bit Linux packages.  If you want to run the Europa release on a 64 bit machine, you must download the base package yourself, then install everything yourself.

[http://europa-mirror1.eclipse.org/eclipse/downloads/drops/R-3.3-200706251500/index.php](http://europa-mirror1.eclipse.org/eclipse/downloads/drops/R-3.3-200706251500/index.php)

Then download eclipse-platform-3.3-linux-gtk-x86_64.tar.gz .  After that, become very intimate with Help -> Software Updates -> Find And Install, Search For New Features, and enable the Europa Discovery Site.

Hopefully that helps someone else!

---

### Post by asi594 on 2007-07-16
Thanks , thats helped me.

---

### Post by jespdj on 2007-07-17
> **bronson said:**
> I found the answer: the Eclipse project neglected to create any turnkey 64 bit Linux packages.  If you want to run the Europa release on a 64 bit machine, you must download the base package yourself, then install everything yourself.
Not true. There is a complete 64-bit Eclipse SDK package - you do not need to install the bare platform and then install everything yourself.

Look at the [Eclipse 3.3 download page](http://download.eclipse.org/eclipse/downloads/drops/R-3.3-200706251500/index.php).

Download **eclipse-SDK-3.3-linux-gtk-x86_64.tar.gz**. That's the complete Eclipse 3.3 IDE for 64-bit Linux.

For some strange reason Eclipse has "hidden" this download page; the 64-bit version is not easy to find on the front page.

---

### Post by Bokonon on 2007-07-17
Eclipse is great, but it seems best to wait a bit before upgrading unless you know it well.  I don't, will admit it, and will wait a bit.

It is a great program and well done, but I had trouble going 3.1 -> 3.2.

---

### Post by PokerJoker on 2007-09-05
> **jespdj said:**
> Not true. There is a complete 64-bit Eclipse SDK package - you do not need to install the bare platform and then install everything yourself.

Look at the [Eclipse 3.3 download page](http://download.eclipse.org/eclipse/downloads/drops/R-3.3-200706251500/index.php).

Download **eclipse-SDK-3.3-linux-gtk-x86_64.tar.gz**. That's the complete Eclipse 3.3 IDE for 64-bit Linux.

For some strange reason Eclipse has "hidden" this download page; the 64-bit version is not easy to find on the front page.


Thanx, Bronson too. Couldn't find it before. Are you also using the PDT by any chance?

---

### Post by alfredbaudisch on 2007-11-27
Sweet, I had the same problem (Ubuntu 7.10 64bits), then I downloaded Eclipse SDK 64-bits and downloaded PDT and dependencies via Eclipse Update Menu. Thanks everybody. :guitar:

---

### Post by genjosanzo on 2007-12-02
Anyone has noticed many crashes running eclipse on a 64 bit architecture??And when it doesn't crashes I got a strange error: some java files could not be read,so some project are not built anymore. Any possible solution or workaround?

---

### Post by istergiou on 2007-12-22
Verify the version of eclipse you have downloaded and the JDK version you use to start eclipse. The arch must be the same, if you use eclipse 32 bit binaries you must have jdk 32 binaries.

You might find the following commands useful:
java -version # to find out version and if it 64bit or 32bit version 
and 
file eclipse

Examples:
ilias@mobtux:~/usr/eclipse3.3.1.1$ java -version
java version "1.5.0_12"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_12-b04)
Java HotSpot(TM) Server VM (build 1.5.0_12-b04, mixed mode)

OR with different JAVA_HOME and PATH

ilias@mobtux:/mnt/sda3/ilias/usr/eclipse3.3.1.1$ java -version
java version "1.5.0_09"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_09-b03)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_09-b03, mixed mode)


ilias@mobtux:~/usr/eclipse3.3.1.1$ file eclipse
eclipse: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), not stripped

Finally, if you do web development I would suggest you to use the 32 bit version, there is better integration with Mozilla that is necessary by some eclipse plugins.

---

