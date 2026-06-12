---
title: "Problem running 32 bit program"
date: 2007-12-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by badrunner on 2007-12-04
I'm trying to run skychart from here:

[http://sourceforge.net/projects/skychart](http://sourceforge.net/projects/skychart)

I'm using the 32 bit download, as there isnt a 64bit one, and i can't for the life of me figure out how to get the thing to build to try and do my own 64bit build. I have every ia32-lib* package installed, and other 32 bit programs work (well enemy territory and some wine things), just this one doesn't. 

There is no useful console info printed when i run it, it just stops without printing anything immediately, and ldd says it's not a dynamic executeable, so i'm stuck for ideas what to do next.

---

### Post by Cappy on 2007-12-04
**Short answer**
Install getlibs from here: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

```

sudo apt-get install upx-ucl ia32-libs
sudo upx -d /usr/bin/skychart
sudo getlibs /usr/bin/skychart

```

**Process of figuring out the solution:**

From looking in the .deb file I see that the binary is
usr/bin/skychart

```

$file /usr/bin/skychart
/usr/bin/skychart: ELF 32-bit LSB executable, Intel 80386, version 1, statically linked, corrupted section header size

```

not very helpful ...

I opened it with nano /usr/bin/skychart and saw this:
```

linux UPX executable packer

```

so ```

$ apt-cache search upx
upx-ucl-beta - an efficient live-compressor for executables (beta version)
......
upx-ucl - an efficient live-compressor for executables
upx-nrv - an efficient live-compressor for executables
.......

```

and so I did a 
```
sudo apt-get install upx-ucl
```

and from there I found out what it did
```

$ upx
                       Ultimate Packer for eXecutables
  Copyright (C) 1996,1997,1998,1999,2000,2001,2002,2003,2004,2005,2006,2007
UPX 3.00        Markus Oberhumer, Laszlo Molnar & John Reiser   Apr 27th 2007

Usage: upx [-123456789dlthVL] [-qvfk] [-o file] file..

Commands:
  -1     compress faster                   -9    compress better
  -d     decompress                        -l    list compressed file
  -t     test compressed file              -V    display version number
  -h     give more help                    -L    display software license
Options:
  -q     be quiet                          -v    be verbose
  -oFILE write output to 'FILE'
  -f     force compression of suspicious files
  -k     keep backup files
file..   executables to (de)compress

```

Aha! It can decompress!

```
$ sudo upx -d /usr/bin/skychart

 Ultimate Packer for eXecutables
  Copyright (C) 1996,1997,1998,1999,2000,2001,2002,2003,2004,2005,2006,2007
UPX 3.00        Markus Oberhumer, Laszlo Molnar & John Reiser   Apr 27th 2007

        File size         Ratio      Format      Name
   --------------------   ------   -----------   -----------
   8357812 <-   2887034   34.54%    linux/386    skychart

Unpacked 1 file.

```

It decompressed!

```
$skychart
/usr/bin/skychart: error while loading shared libraries: libgdk_pixbuf.so.2: cannot open shared object file: No such file or directory

```

Ack! Okay well I just need to run getlibs on it (installed from here: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790) )

```

sudo getlibs /usr/bin/skychart
Matched library libgdk_pixbuf.so.2 to /gutsy/libs/libgdk-pixbuf2
The following i386 libraries will be installed:
/gutsy/libs/libgdk-pixbuf2
Continue? (y/n) y
Downloading. Installing libraries ...

```

And now it is working!

---

### Post by badrunner on 2007-12-04
Brilliant, thanks for the help.

---

