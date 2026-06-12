---
title: "Insalling recoll in intrepid"
date: 2009-01-11
forum: x86 64-bit Users
---

### Post by grappler on 2009-01-11
I've installed the search engine recoll from synaptic on  64-bit intrepid ubuntu. 

When I try to run it I encounter the  following:

> bill@bill-laptop:~$ recoll
recoll: error while loading shared libraries: libxapian.so.15: cannot open shared object file: No such file or directory


This may not be a 64-bit issue - if so apologies for posting here - I've only tried on this architecture. I've tried to install every xapian package I can find in the repositories but the problem remains. In any case this seems to be a dependency problem. 

Does anyone have recoll installed on 64-bit intrepid?

---

### Post by Yellow Pasque on 2009-01-11
On my Intrepid system, libxapian.so.15 is a symlink to libxapian.so.15.5.1, and this symlink is provided by the libxapian15 package.  If you have that package installed, and the file is missing, try reinstalling the package.
```
sudo apt-get --reinstall libxapian15
```
If that still doesn't work, create your own symlink:
```
sudo ln -s /usr/lib/libxapian.so.15.5.1 /usr/lib/libxapian.so.15
```

---

### Post by grappler on 2009-01-11
Thanks Temüjin.

I have the same libxapian libs and links  as you but still getting the recoll problem. I've tried (re)installing libxapian15 as you said and also recoll but the problem remains. 


> bill@bill-laptop:/usr/lib$ ls -al libxap*
-rw-r--r-- 1 root root 3.8M 2008-10-16 01:55 libxapian.a
-rw-r--r-- 1 root root  808 2008-10-16 01:55 libxapian.la
lrwxrwxrwx 1 root root   19 2009-01-12 08:04 libxapian.so -> libxapian.so.15.5.1
lrwxrwxrwx 1 root root   19 2009-01-12 09:08 libxapian.so.15 -> libxapian.so.15.5.1
-rw-r--r-- 1 root root 1.4M 2008-10-16 01:55 libxapian.so.15.5.1


---

### Post by Yellow Pasque on 2009-01-11
Hmm. I installed recoll and it works fine for me. The file command shows it as a 64-bit executable:
Post the output of:
```
ldd /usr/bin/recoll
```
Please use [ code ] instead of [ quote ] for the sake of readability.

---

### Post by grappler on 2009-01-11
Hi Temüjin
```

bill@bill-laptop:~$ ldd /usr/bin/recoll
	linux-vdso.so.1 =>  (0x00007fff949fe000)
	libxapian.so.15 => /usr/lib/libxapian.so.15 (0x00007f6a8c396000)
	libz.so.1 => /usr/lib/libz.so.1 (0x00007f6a8c17e000)
	libqt-mt.so.3 => /usr/lib/libqt-mt.so.3 (0x00007f6a8b6ef000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0x00007f6a8b4dd000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0x00007f6a8b1d5000)
	libpthread.so.0 => /lib/libpthread.so.0 (0x00007f6a8afb9000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00007f6a8acac000)
	libm.so.6 => /lib/libm.so.6 (0x00007f6a8aa27000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00007f6a8a80f000)
	libc.so.6 => /lib/libc.so.6 (0x00007f6a8a49d000)
	libdl.so.2 => /lib/libdl.so.2 (0x00007f6a8a299000)
	libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0x00007f6a8a067000)
	libaudio.so.2 => /usr/lib/libaudio.so.2 (0x00007f6a89e4e000)
	libXt.so.6 => /usr/lib/libXt.so.6 (0x00007f6a89bea000)
	libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0x00007f6a899c7000)
	libpng12.so.0 => /usr/lib/libpng12.so.0 (0x00007f6a897a0000)
	libXi.so.6 => /usr/lib/libXi.so.6 (0x00007f6a89595000)
	libXrender.so.1 => /usr/lib/libXrender.so.1 (0x00007f6a8938b000)
	libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0x00007f6a89183000)
	libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0x00007f6a88f79000)
	libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0x00007f6a88d77000)
	libXft.so.2 => /usr/lib/libXft.so.2 (0x00007f6a88b62000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x00007f6a888de000)
	libSM.so.6 => /usr/lib/libSM.so.6 (0x00007f6a886d5000)
	libICE.so.6 => /usr/lib/libICE.so.6 (0x00007f6a884ba000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0x00007f6a882b8000)
	libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0 (0x00007f6a880b6000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0x00007f6a87e9a000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f6a8c6f9000)
	libexpat.so.1 => /usr/lib/libexpat.so.1 (0x00007f6a87c70000)
	libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0x00007f6a87a6b000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00007f6a87866000)
bill@bill-laptop:~$ 

```

Thanks for helping with this!

---

### Post by Yellow Pasque on 2009-01-11
This is a bit baffling to me. Does the following ldconfig command list /usr/lib?:
```
sudo ldconfig -v | grep /lib
```
The ATI/Catalyst/fglrx driver screwed up my library path configuration. You wouldn't happpen to have that installed on your system at any time, would you?

---

### Post by grappler on 2009-01-12
Hi  Temüjin

Here's the result of 
```

sudo ldconfig -v | grep /lib

```

```

/usr/lib/atlas:
/usr/lib32/alsa-lib:
/usr/lib/alsa-lib:
/usr/local/lib:
/usr/lib/R/lib:
/lib/x86_64-linux-gnu:
/usr/lib/x86_64-linux-gnu:
/lib:
/lib32:
/usr/lib:
/sbin/ldconfig.real: Cannot stat /usr/lib/libglfw.so: No such file or directory
/usr/lib32:
/usr/lib/tls: (hwcap: 0x8000000000000000)
/usr/lib32/i586: (hwcap: 0x0004000000000000)
/usr/lib32/i486: (hwcap: 0x0002000000000000)
/usr/lib32/i686: (hwcap: 0x0008000000000000)
/usr/lib32/tls: (hwcap: 0x8000000000000000)
/usr/lib32/i686/cmov: (hwcap: 0x0008000000008000)

```

I note that libglfw is a library for portable opengl and so I would not have thought relevant to this.  In any case I have both libglfw2 and libglfw-dev installed - these seem to be the only libraries relevant the that issue. 

I doubt that I've ever had the ATI/Catalyst/fglrx driver on my system since it has an nvidia graphics card. 

Thanks for all your help on this.

---

