---
title: "Problems trying to install Savage under Feisty 64"
date: 2007-06-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by virgilnilson on 2007-06-22
Hi, after following many tips and guides I have finally gotten to this point where I can't seem to proceed any further:

```
sudo linux32 sh Savage_with_sep3t.run
Verifying archive integrity... All good.
Uncompressing Savage and SEP3T Installer..........................................................
/home/virgil/.setup18970: error while loading shared libraries: libgmodule-1.2.so.0: cannot open shared object file: No such file or directory

```

Previous to this there was another shared library problem, but I used getlibs and it seems to have downloaded it, and now I am getting this new roadblock. Getlibs is telling me that I am not missing any dependencies, and I've tried to find that library on my own, even installing several VMware packages as a post on a google search said that the library was a part of them.

Also, I am running AMD 64 +3200 if that helps.

---

### Post by Cappy on 2007-06-22
The reason is that .run is a loki installer and not a binary.
Here is my script: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
You have the version I released yesterday?

Just do this:
```
getlibs -32 libgmodule-1.2.so.0
```
=)

P.S. I'll add a message when the file isn't a binary and instructions on the above command.

Also that gives me another idea .. I could run the program myself if it isn't a binary and intercept the error and go from there .. hmm .. interesting

---

### Post by fabertawe on 2007-06-22
The file you need is in **[this package]("http://packages.ubuntu.com/feisty/libs/libglib1.2")**.

Download the i386, navigate to where you saved it (i.e. desktop)...
```
cd ~/Desktop
dpkg -x libglib1.2_1.2.10-17build1_i386.deb libglib_files
sudo cp libglib_files/usr/lib/* /usr/lib32
rm -rf libglib_files
```

Edit: Cappy got there first.. seems getlibs is proving very useful indeed! :)

---

### Post by virgilnilson on 2007-06-22
Thanks a lot guys! However now I'm getting a new error

```
./savage
Traceback (most recent call last):
  File "<string>", line 11, in ?
  File "iu.py", line 277, in importHook
  File "iu.py", line 362, in doimport
  File "/home/slothy/cvs/src/s2update/builds2update/out1.pyz/wxPython", line 20, in ?
  File "iu.py", line 277, in importHook
  File "iu.py", line 338, in doimport
  File "iu.py", line 184, in getmod
  File "archive.py", line 386, in getmod
  File "iu.py", line 46, in getmod
ImportError: libtiff.so.3: cannot open shared object file: No such file or directory
There was an error (error 65280 - Unknown error 65280) running the updater!  bailing out

```


Googling for libtiff.so.3 brings up a ton of files and I have no idea what to look for.

---

### Post by Cappy on 2007-06-22
Try this:
```
getlibs -32 libtiff.so.4
```
```

sudo ln -s /usr/lib32/libtiff.so.4 /usr/lib32/libtiff.so.3
```

---

### Post by virgilnilson on 2007-06-24
> **Cappy said:**
> Try this:
```
getlibs -32 libtiff.so.4
```
```

sudo ln -s /usr/lib32/libtiff.so.4 /usr/lib32/libtiff.so.3
```

It works now! Thank you so much, you kick ***.

---

### Post by virgilnilson on 2007-06-24
Ugh, I'm going to cry, after applying the SFE patch, I am now getting this error:

```
 sudo linux32 ./savage

Gdk-WARNING **: locale not supported by C library

Gdk-WARNING **: locale not supported by Xlib, locale set to C

Gdk-WARNING **: can not set locale modifiers
./silverback.bin: error while loading shared libraries: libcom_err.so.2: cannot open shared object file: No such file or directory

```

The initial GUI starts up fine and tells me my version is up to date, then it simply disappears and I see that in terminal.

Getlibs isn't finding libcom_err.so.2.

---

### Post by Cappy on 2007-06-24
o .. I know why too .. that library is in /lib and not /usr/lib
Bug T_T

Here's a manual install:
```
cd /tmp
wget http://mirrors.kernel.org/ubuntu/pool/main/e/e2fsprogs/libcomerr2_1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1_i386.deb
dpkg -x libcomerr2_1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1_i386.deb libcom
sudo mv libcom/lib/* /lib32

```

---

