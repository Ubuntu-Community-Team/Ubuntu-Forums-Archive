---
title: "32 bit binaries and other problems"
date: 2005-03-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Lundh on 2005-03-17
I am completly new to ubunto and really using Linux as my main OS at home. We use solaris and redhat in school but that's not really that giving av that system is extremly tweaked. Other then more or less successful configuration of a couple of BSD servers and some test installs om ny desktop that's really all experience with linux I have.

Anyway to my problem; I decided to throw away my Windows installation and figure out Linux as good as I can. I have installed warty for AMD64 and upgraded it to hoary but I can't figure out how to run 32bit applications like Opera on it. How to get flash to work and other things like that. I could really some need advice on that in particular and other Linux thoughts in general.

Another thing I realised now is that the entire system is nrear unusable, its really slow and I cant figure out why.

---

### Post by Pse on 2005-03-17
Probably due to the upgrade. I am running Hoary64 (installed from Array5) and here are a couple of things you need to know.
First, you will not be able to get flash to work unless you use a 32-bit browser. There are 64-bit opensoure alternatives to Macromedia's propietary player-plugin, but they're still in the early stages and there are known problems. One of them is swf-player... You could try that.
By default, Firefox on any AMD64 installation is 64-bit, so you can't get Macromedia's plugin to work. You could do several things, however:
- Get a 32-bit Firefox (you'll probably have to uninstall the 64-bit version).
- Make a chroot (search the AMD64 forums, there's a guide somewhere).
- Get a 32-bit browser and keep the 64-bit Firefox.

To run 32-bit apps you'll first need to get some libs. Install the packages ia32-libs and ia32-libs-gtk. Those should be enough for now (there are obviously some programs which need other libs which aren't there).

A good 32-bit browser I've been using just for Flash is Opera. You'll have to put up with the ads, though. Opera also provides statically linked i386 binaries, so the only thing you really need to do is get the tar.gz, uncompress it in a folder, and run it. There's no need to install it if you don't want to. Nevertheless, there's a problem with this. Opera, to run Flash, needs Motif...so you'll have to install OpenMotif (you can find it on Opera's site). If you want the links for the files, here's a thread: [http://www.ubuntuforums.org/showthread.php?t=16767&page=2&highlight=opera](http://www.ubuntuforums.org/showthread.php?t=16767&page=2&highlight=opera)
Look at my last post.

Good luck.

BTW, if you can't get your system to run smoothly, I'd simply reinstall from the latest Hoary Array CD. It should give you a good and clean system to play with.

---

### Post by Lundh on 2005-03-18
[QUOTE=Pse]To run 32-bit apps you'll first need to get some libs. Install the packages ia32-libs and ia32-libs-gtk. Those should be enough for now (there are obviously some programs which need other libs which aren't there).

A good 32-bit browser I've been using just for Flash is Opera. You'll have to put up with the ads, though. Opera also provides statically linked i386 binaries, so the only thing you really need to do is get the tar.gz, uncompress it in a folder, and run it. There's no need to install it if you don't want to. Nevertheless, there's a problem with this. Opera, to run Flash, needs Motif...so you'll have to install OpenMotif (you can find it on Opera's site). If you want the links for the files, here's a thread: [http://www.ubuntuforums.org/showthread.php?t=16767&page=2&highlight=opera](http://www.ubuntuforums.org/showthread.php?t=16767&page=2&highlight=opera)
Look at my last post.

Good luck.

BTW, if you can't get your system to run smoothly, I'd simply reinstall from the latest Hoary Array CD. It should give you a good and clean system to play with.[/QUOTE]
I tried to run opera but I get this problem:
> ./bin/opera: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

About  reinstalling, I tried to install Hoary from the CD but got an error which is why I iinstalled from Warty instead.

---

### Post by RoccoD on 2005-03-18
libqt3-mt is the qt multithreaded lib. This means you probably got the wrong opera version. You need the static linked version.

Greetz,

RoccoD

---

### Post by Pse on 2005-03-18
Yep, get the statically linked version. Look at the Opera site, there are tons of versions. One of them has QT statically linked into it.
At the download page, you should select Linux i386, and in the distribution package option "static DEB package". You can always tick the option to download it as a tar.gz, in case you don't want to install the package, but the .deb is a good option.
To install it you'll have to do a "dpgk -i [packagename].deb".

---

### Post by ZeroVerteX on 2005-04-20
In Synaptic, I just installed libqt3c102-mt described as:

Qt GUI Library (Threaded runtime version), Version 3
This is the Trolltech Qt library, version 3. It's necessary for
applications that link against the libqt-mt.so.3, e.g. all KDE3
applications.

That fixed my Skype, that will probably help with your Opera. Good luck.

---

