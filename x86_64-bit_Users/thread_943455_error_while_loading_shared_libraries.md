---
title: "error while loading shared libraries"
date: 2008-10-10
forum: x86 64-bit Users
---

### Post by bldyman on 2008-10-10
I´m trying to install pd extended on Ubuntu hardy 64bit. after the installation, running "pd" in the shell:

bldyman@franco:~$ pd
/usr/lib/pd/bin/pd-gui: error while loading shared libraries: libtk8.4.so.0: cannot open shared object file: No such file or directory

I tried to make a sl in /usr/lib/ but:

bldyman@franco:/usr/lib$ ln -s libtk8.4.so libtk8.4.so.0
ln: creating symbolic link `libtk8.4.so.0': File exists

wich is th problem?
thanx in advance

---

### Post by Yellow Pasque on 2008-10-10
What is the output from:
```
ls -la | grep tk8
```

---

### Post by bldyman on 2008-10-11
```
bldyman@franco:/usr/lib$ ls -la | grep tk8
-rw-r--r--   1 root root  1028840 2008-02-25 19:25 libtk8.4.so.0
lrwxrwxrwx   1 root root       13 2008-10-10 15:25 libtk8.4.so.1 -> libtk8.4.so.0

```

---

### Post by Yellow Pasque on 2008-10-11
I'm guessing that pd is a 32-bit program and is looking for libraries in /usr/lib32

To resolve this issue, use getlibs: [http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs](http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs)

---

### Post by bldyman on 2008-10-11
I used getlibs to install pd-extended (sudo dpkg -i --force-architecture pd-extended-0.XX.deb)  but maybe I installed needed packages from Synaptic in 64bit version. so when I tipe: 

bldyman@franco:~$ getlibs /usr/bin/pd
This application isn't missing any dependencies

I uninstalled  pd-extended and now I'll try to install 32bit packages using getlibs. I'll tell you soon.

---

### Post by albesan on 2009-01-14
> **bldyman said:**
> I used getlibs to install pd-extended (sudo dpkg -i --force-architecture pd-extended-0.XX.deb)  but maybe I installed needed packages from Synaptic in 64bit version. so when I tipe: 

bldyman@franco:~$ getlibs /usr/bin/pd
This application isn't missing any dependencies

I uninstalled  pd-extended and now I'll try to install 32bit packages using getlibs. I'll tell you soon.

Hey I'm trying to work with pd too having the same issue but unable to solve it.
Did you managed to make it work?

Regards.

a.

---

### Post by Cappy on 2009-01-16
```
sudo getlibs /usr/lib/pd/bin/pd-gui
```
or
```
sudo getlibs -l libtk8.4.so.0
```

---

### Post by albesan on 2009-01-16
> **Cappy said:**
> ```
sudo getlibs /usr/lib/pd/bin/pd-gui
```
or
```
sudo getlibs -l libtk8.4.so.0
```


Thanks for the reply.

I managed to get it going following this:

[http://puredata.hurleur.com/sujet-1947-extended-amd64](http://puredata.hurleur.com/sujet-1947-extended-amd64)

I'm having problems with video formats though, can't get it to open none of the files I've tried so far.
I guess it is a codecs issue...

a.

---

### Post by Cappy on 2009-01-16
Yes, that could be a problem.
> sudo getlibs -w packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu3_i386.deb
will download and install the restricted 32-bit codecs.

or maybe
```
getlibs -p libavcodec51
```

---

