---
title: "Skype for Linux doesn't work on Ubuntu [64-bit]"
date: 2006-09-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by komputes on 2006-09-18
I tried installing Skype and it tells me that it's an i386 app. It won't work on my 64-bit OS! Explain this to me then... I was using SuSe 10.1 [64-bit] before I started with Ubuntu and skype installed and worked fine with that.

](*,) I](*,) Need ](*,) Skype ](*,) 

komputes

---

### Post by RAOF on 2006-09-18
You really should have posted all of your issues in one thread, rather than 1 thread for each.  Also, you should probably have read the sticky thread at the top of the forum "How to get specific programs to run...", because it covers how to get both Skype and flash running.  You should search for a solution before asking for one.

---

### Post by komputes on 2006-09-18
Sorry about the threads, just thought it was how it is done in forums. Thing is, I did search and I couldn't find the solution, can you give me the link or paste the URL of the solutions to my peoblems?

---

### Post by RAOF on 2006-09-18
At the top of **this** forum is a thread [How to get specific programs to run under Ubuntu 64](http://www.ubuntuforums.org/showthread.php?t=191205).  This is where you'll find your solutions.

---

### Post by komputes on 2006-09-18
> **RAOF said:**
> At the top of **this** forum is a thread [How to get specific programs to run under Ubuntu 64](http://www.ubuntuforums.org/showthread.php?t=191205).  This is where you'll find your solutions.

xx@xx:~$ sudo dpkg -i --force-architecture skype_1.2.0.18-2_i386.deb
dpkg: error processing skype_1.2.0.18-2_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 skype_1.2.0.18-2_i386.deb

well that didn't work ](*,) - kind of wanted to use the solid version and not a beta release, but what they hey... I'll get back to you if it works.

komputes

---

### Post by komputes on 2006-09-19
I tried the commands to install skype 1.3 beta:

```
cd /tmp
wget http://www.skype.com/go/getskype-linux-beta-deb
sudo dpkg -i --force-architecture skype-beta-1.3.0.30-1_i386.deb
wget http://bombazyn.mine.nu/Ubuntu/asound32-qtmt32.tar.bz2
cd /usr/lib32
sudo tar xjvf /tmp/asound32-qtmt32.tar.bz2
``` 


I got this output:

```

xx@xx:~$ cd /tmp
xx@xx:/tmp$ wget http://www.skype.com/go/getskype-linux-beta-deb
--00:19:14--  http://www.skype.com/go/getskype-linux-beta-deb
           => `getskype-linux-beta-deb'
Resolving www.skype.com... 198.173.5.35
Connecting to www.skype.com|198.173.5.35|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://download.skype.com/linux/skype-beta-1.3.0.37-1_i386.deb [following]
--00:19:18--  http://download.skype.com/linux/skype-beta-1.3.0.37-1_i386.deb
           => `skype-beta-1.3.0.37-1_i386.deb'
Resolving download.skype.com... 212.72.49.140
Connecting to download.skype.com|212.72.49.140|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 9,907,846 (9.4M) [application/x-debian-package]

100%[====================================>] 9,907,846    121.46K/s    ETA 00:00

00:21:54 (62.82 KB/s) - `skype-beta-1.3.0.37-1_i386.deb' saved [9907846/9907846]
xx@xx:/tmp$ sudo dpkg -i --force-architecture skype-beta-1.3.0.30-1_i386.deb
dpkg: error processing skype-beta-1.3.0.30-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 skype-beta-1.3.0.30-1_i386.deb
xx@xx:/tmp$ wget http://bombazyn.mine.nu/Ubuntu/asound32-qtmt32.tar.bz2
--00:21:55--  http://bombazyn.mine.nu/Ubuntu/asound32-qtmt32.tar.bz2
           => `asound32-qtmt32.tar.bz2'
Resolving bombazyn.mine.nu... 84.107.196.80
Connecting to bombazyn.mine.nu|84.107.196.80|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,092,326 (2.9M) [application/x-tar]

100%[====================================>] 3,092,326     86.58K/s    ETA 00:00

00:22:31 (85.82 KB/s) - `asound32-qtmt32.tar.bz2' saved [3092326/3092326]

xx@xx:/tmp$ cd /usr/lib32
xx@xx:/usr/lib32$ sudo tar xjvf /tmp/asound32-qtmt32.tar.bz2
libasound.so.2
libasound.so.2.0.0
libqt-mt.so.3
libqt-mt.so.3.3
libqt-mt.so.3.3.6
libqui.so.1
libqui.so.1.0
libqui.so.1.0.0
xx@xx:/usr/lib32$
xx@xx:/usr/lib32$ ls
at-spi                              libmdbsql.so.1.0.0
AuErrorDB                           libneon.so.25
bonobo                              libneon.so.25.0.3
firefox                             libnspr4.so
gconv                               libnss3.so
gtk-2.0                             libORBit-2.so.0
i486                                libORBit-2.so.0.1.0
i586                                libORBitCosNaming-2.so.0
i686                                libORBitCosNaming-2.so.0.1.0
libart_lgpl_2.so.2                  libORBit-imodule-2.so.0
libart_lgpl_2.so.2.3.17             libORBit-imodule-2.so.0.0.0
libasound.so.2                      libpango-1.0.so.0
libasound.so.2.0.0                  libpango-1.0.so.0.1201.2
libatk-1.0.so.0                     libpangocairo-1.0.so.0
libatk-1.0.so.0.1114.0              libpangocairo-1.0.so.0.1201.2
libaudio.so.2                       libpangoft2-1.0.so.0
libaudio.so.2.3                     libpangoft2-1.0.so.0.1201.2
libcairo.so.2                       libpangox-1.0.so.0
libcairo.so.2.2.4                   libpangox-1.0.so.0.1201.2
libcrypto.so.0.9.8                  libpangoxft-1.0.so.0
libcurl.so.3                        libpangoxft-1.0.so.0.1201.2
libcurl.so.3.0.0                    libplc4.so
libdb-4.3.so                        libplds4.so
libdes425.so.3                      libpng12.so.0
libdes425.so.3.0                    libpng12.so.0.1.2.8
libdrm.so.2                         libportaudio.so.0
libdrm.so.2.0.0                     libportaudio.so.0.0.18
libexpat.so.0                       libqt-mt.so.3
libexpat.so.1                       libqt-mt.so.3.3
libexpat.so.1.0.0                   libqt-mt.so.3.3.6
libexslt.so.0                       libqui.so.1
libexslt.so.0.8.12                  libqui.so.1.0
libFLAC.so.7                        libqui.so.1.0.0
libFLAC.so.7.0.0                    libsasl2.so.2
libfontconfig.so.1                  libsasl2.so.2.0.19
libfontconfig.so.1.0.4              libsmime3.so
libfreetype.so.6                    libSM.so.6
libfreetype.so.6.3.8                libSM.so.6.0.0
libgcc_s.so.1                       libsndfile.so.1
libgcj.so.7                         libsndfile.so.1.0.12
libgcj.so.7.0.0                     libsoftokn3.so
libgconf2-4                         libssl3.so
libgconf-2.so.4                     libssl.so.0.9.8
libgconf-2.so.4.1.0                 libstartup-notification-1.so.0
libgcrypt.so.11                     libstartup-notification-1.so.0.0.0
libgcrypt.so.11.2.1                 libstdc++.so.5
libgdk_pixbuf-2.0.so.0              libstdc++.so.5.0.7
libgdk_pixbuf-2.0.so.0.800.20       libstdc++.so.6
libgdk_pixbuf_xlib-2.0.so.0         libstdc++.so.6.0.7
libgdk_pixbuf_xlib-2.0.so.0.800.20  libstlport_gcc.so.4.6
libgdk-x11-2.0.so.0                 libtasn1.so.2
libgdk-x11-2.0.so.0.800.20          libtasn1.so.2.0.17
libgij.so.7                         libtiff.so.4
libgij.so.7.0.0                     libtiff.so.4.1.4
libglib-2.0.so.0                    libwmf-0.2.so.7
libglib-2.0.so.0.1000.3             libwmf-0.2.so.7.1.0
libGL.so.1                          libwmflite-0.2.so.7
libGL.so.1.2                        libwmflite-0.2.so.7.0.1
libGLU.so.1                         libwpd-0.8.so.8
libGLU.so.1.3.060401                libwpd-0.8.so.8.0.4
libgmodule-2.0.so.0                 libX11.so.6
libgmodule-2.0.so.0.1000.3          libX11.so.6.2.0
libgnutls-extra.so.12               libXau.so.6
libgnutls-extra.so.12.3.6           libXau.so.6.0.0
libgnutls-openssl.so.12             libXaw3d.so.6
libgnutls-openssl.so.12.3.6         libXaw3d.so.6.1
libgnutls.so.12                     libXaw7.so.7
libgnutls.so.12.3.6                 libXaw7.so.7.0.0
libgobject-2.0.so.0                 libXaw.so.7
libgobject-2.0.so.0.1000.3          libXcursor.so.1
libgpg-error.so.0                   libXcursor.so.1.0.2
libgpg-error.so.0.1.4               libXdmcp.so.6
libgssapi_krb5.so.2                 libXdmcp.so.6.0.0
libgssapi_krb5.so.2.2               libXext.so.6
libgthread-2.0.so.0                 libXext.so.6.4.0
libgthread-2.0.so.0.1000.3          libXfixes.so.3
libgtk-x11-2.0.so.0                 libXfixes.so.3.0.0
libgtk-x11-2.0.so.0.800.20          libXft.so.2
libICE.so.6                         libXft.so.2.1.2
libICE.so.6.3.0                     libXinerama.so.1
libicudata.so.34                    libXinerama.so.1.0.0
libicudata.so.34.1                  libXi.so.6
libicui18n.so.34                    libXi.so.6.0.0
libicui18n.so.34.1                  libxml2.so.2
libicuio.so.34                      libxml2.so.2.6.24
libicuio.so.34.1                    libxmlsec1-nss.so.1
libicule.so.34                      libxmlsec1-nss.so.1.2.9
libicule.so.34.1                    libxmlsec1-openssl.so.1
libiculx.so.34                      libxmlsec1-openssl.so.1.2.9
libiculx.so.34.1                    libxmlsec1.so.1
libicutu.so.34                      libxmlsec1.so.1.2.9
libicutu.so.34.1                    libXmu.so.6
libicuuc.so.34                      libXmu.so.6.2.0
libicuuc.so.34.1                    libXmuu.so.1
libIDL-2.so.0                       libXmuu.so.1.0.0
libIDL-2.so.0.0.0                   libXpm.so.4
libidn.la                           libXpm.so.4.11.0
libidn.so.11                        libXp.so.6
libidn.so.11.5.11                   libXp.so.6.2.1
libjpeg.so.62                       libXrandr.so.2
libjpeg.so.62.0.0                   libXrandr.so.2.0.0
libk5crypto.so.3                    libXrender.so.1
libk5crypto.so.3.0                  libXrender.so.1.3.0
libkrb4.so.2                        libxslt.so.1
libkrb4.so.2.0                      libxslt.so.1.1.15
libkrb5.so.3                        libXTrap.so.6
libkrb5.so.3.2                      libXTrap.so.6.4.0
libkrb5support.so.0                 libXt.so.6
libkrb5support.so.0.0               libXt.so.6.0.0
liblber.so.2                        libXtst.so.6
liblber.so.2.0.130                  libXtst.so.6.1.0
liblcms.so.1                        libXxf86vm.so.1
liblcms.so.1.0.13                   libXxf86vm.so.1.0.0
libldap_r.so.2                      libz.so.1
libldap_r.so.2.0.130                libz.so.1.2.3
libldap.so.2                        orbit-2.0
libldap.so.2.0.130                  pango
libmdb.so.1                         pkgconfig
libmdb.so.1.0.0                     sasl2
libmdbsql.so.1                      ssl
xx@xx:/usr/lib32$

```


the ls was just for me to see if Skype was in there because i could not find it in the applications menu, so where is skype after all this?

komputes

---

### Post by RAOF on 2006-09-19
> **komputes said:**
> I tried the commands to install skype 1.3 beta:

```
cd /tmp
wget http://www.skype.com/go/getskype-linux-beta-deb
sudo dpkg -i --force-architecture skype-beta-1.3.0.30-1_i386.deb
wget http://bombazyn.mine.nu/Ubuntu/asound32-qtmt32.tar.bz2
cd /usr/lib32
sudo tar xjvf /tmp/asound32-qtmt32.tar.bz2
``` 


I got this output:

```

xx@xx:~$ cd /tmp
xx@xx:/tmp$ wget http://www.skype.com/go/getskype-linux-beta-deb
--00:19:14--  http://www.skype.com/go/getskype-linux-beta-deb
           => `getskype-linux-beta-deb'
Resolving www.skype.com... 198.173.5.35
Connecting to www.skype.com|198.173.5.35|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://download.skype.com/linux/skype-beta-1.3.0.37-1_i386.deb [following]
--00:19:18--  http://download.skype.com/linux/skype-beta-1.3.0.37-1_i386.deb
           => `skype-beta-1.3.0.37-1_i386.deb'
Resolving download.skype.com... 212.72.49.140
Connecting to download.skype.com|212.72.49.140|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 9,907,846 (9.4M) [application/x-debian-package]

100%[====================================>] 9,907,846    121.46K/s    ETA 00:00

00:21:54 (62.82 KB/s) - `skype-beta-1.3.0.37-1_i386.deb' saved [9907846/9907846]
xx@xx:/tmp$ sudo dpkg -i --force-architecture skype-beta-1.3.0.30-1_i386.deb
dpkg: error processing skype-beta-1.3.0.30-1_i386.deb (--install):
 cannot access archive: No such file or directory
...

```


the ls was just for me to see if skype wa in there because i could not find it in the applications menu, so where is skype after all this?

komputes
Skype isn't installed.  Notice the dpkg error.  The reason here is that you've downloaded **skype-beta-1.3.0.37-1_i386.deb**, and then asked dpkg to install **sudo dpkg -i --force-architecture *skype-beta-1.3.0.30-1_i386.deb***

To actually install skype, you'll need to run **sudo dpkg -i --force-architecture *skype-beta-1.3.0.37-1_i386.deb***, to match the actual version you've downloaded.

---

### Post by komputes on 2006-09-19
> **RAOF said:**
> Notice the dpkg error. 

D'oh

#-o 

Let me try that one again:

```
cd /tmp
wget http://www.skype.com/go/getskype-linux-beta-deb
sudo dpkg -i --force-architecture skype-beta-1.3.0.37-1_i386.deb
wget http://bombazyn.mine.nu/Ubuntu/asound32-qtmt32.tar.bz2
cd /usr/lib32
sudo tar xjvf /tmp/asound32-qtmt32.tar.bz2

```

that should work.... let me get back to ya

k

---

### Post by komputes on 2006-09-19
We are up and running on Skype, thanks a bunch, it works...
[CENTER][B]
:grin: 
Me so happy, me love you long time...
\\:D/[/B][/CENTER]

---

### Post by m.fred on 2006-09-21
Hi
I have a 5003WMLI, and I installed amd64... I have some problems my wireless for example do not run (bcm43xx).... 

For the application 32 bits, I have installed a chroot with an architecture of i386, Then firefox/flash/mplayer works, Skype also and xine with the win32codecs.

If it help you for the future.

;)

---

### Post by Kilz on 2006-09-21
> **m.fred said:**
> Hi
I have a 5003WMLI, and I installed amd64... I have some problems my wireless for example do not run (bcm43xx).... 

For the application 32 bits, I have installed a chroot with an architecture of i386, Then firefox/flash/mplayer works, Skype also and xine with the win32codecs.

If it help you for the future.

;)

Chroots are good if you want to install a media player like you have. But just so you know , its possible to install a lot, including a 32bit mplayer, w32codecs,firefox, etc without the chroot.

---

### Post by dbw on 2006-10-11
I am also having issues with this program.  I have tried installing the *.deb package using "--force-architecture", as well as simply unpacking the version with the statically linked qt libraries.  In both cases, the installation (or unpacking) seems to go smoothly, but when I run skype, I get the following error message:
```
dbw@tuatara:~ $ skype
bash: /usr/bin/skype:  No such file or directory
```
but !!
```
dbw@tuatara:~ $ ls -l /usr/bin/skype*
-rwxr-xr-x 1 dbw dbw  15M 2006-09-22 10:39 skype
-rwxr-xr-x 1 dbw dbw  13K 2006-09-22 10:39 skype-action-handler
-rwxr-xr-x 1 dbw dbw 1.8K 2006-09-22 10:39 skype-callto-handler
```

I have a dual-core 64 bit processor (amd x2 4600, AM2 socket).  I run the fluxbox window manager.  The specific code shown above was after installing using dpkg.

Thanks for your help, folks.

---

### Post by kuja on 2006-10-11
To get skype working:

Go to their website and manually download Skype 1.3 (it was released not long ago), the sticky needs updated.

next, install the ia32-libs-kde and ia32-libs-openoffice.org packages
sudo apt-get install ia32-libs-kde ia32-libs-openoffice.org

then install the deb you downloaded
sudo dpkg --install --force-architecture file.deb

---

### Post by fabertawe on 2006-10-11
The static Skype package works without having to force install. Extract the contents of the archive from within Nautilus (right click -> extract to...). Then right click on the desktop and create a launcher. In 'Command' put 'linux32 /<path to skype folder>/skype'. My path is 'linux32 /opt/skype/skype', for example.

The first time I installed I also needed
```
sudo apt-get install ia32-libs ia32-libs-gtk gsfonts gsfonts-x11 linux32
```

Paul

Edit: this is under Gnome of course ;)

---

### Post by kuja on 2006-10-11
> **fabertawe said:**
> The static Skype package works without having to force install. Extract the contents of the archive from within Nautilus (right click -> extract to...). Then right click on the desktop and create a launcher. In 'Command' put 'linux32 /<path to skype folder>/skype'. My path is 'linux32 /opt/skype/skype', for example.

The first time I installed I also needed
```
sudo apt-get install ia32-libs ia32-libs-gtk gsfonts gsfonts-x11 linux32
```

Paul

Edit: this is under Gnome of course ;)

Disadvantages of this route of course being that static QT tends to look different(ugly perhaps? Sure, why not), upgrades won't be nearly as clean, and that you can't later do a simple "dpkg -r skype" to remove it.

---

### Post by fabertawe on 2006-10-13
> **kuja said:**
> Disadvantages of this route of course being that static QT tends to look different(ugly perhaps? Sure, why not), upgrades won't be nearly as clean, and that you can't later do a simple "dpkg -r skype" to remove it.

I can only speak personally of course but Skype looks great and upgrading/removing is as simple as replacing/deleting the directory I have extracted Skype to ;) 

Paul

---

### Post by dbw on 2006-10-14
@kuja- Does this program really need the openoffice libs?

@fabertawe - I have installed the list of 32 bit libraries that you suggest. After unpacking the statically linked skype-1.3 package, I tried to run the excecutable "skype", to which I recieved the message: 
```
bash: ./skype: No such file or directory
```

note that the file skype indeed exists, and is taking up 15M on my HDD.

any advice?

---

### Post by kuja on 2006-10-15
ia32-libs-openoffice.org has some things in it that are in fact not OOo related. What's needed out of it is the 32-bit asound library.

---

### Post by fabertawe on 2006-10-15
> **dbw said:**
> @kuja- Does this program really need the openoffice libs?

@fabertawe - I have installed the list of 32 bit libraries that you suggest. After unpacking the statically linked skype-1.3 package, I tried to run the excecutable "skype", to which I recieved the message: 
```
bash: ./skype: No such file or directory
```

note that the file skype indeed exists, and is taking up 15M on my HDD.

any advice?

You need to run it prefixed with 'linux32', e.g.
```
linux32 /path/to/skype
```

Cheers ... Paul

---

### Post by Grym on 2006-10-28
> **fabertawe said:**
> You need to run it prefixed with 'linux32', e.g.
```
linux32 /path/to/skype
```

Cheers ... Paul
Hi!

I have the same problem. I can't run any 32bit binaries. I've tried running with linux32, but it still said that "No such file or directory".

It works fine on 64bit Dapper.
Any idea?

---

### Post by fabertawe on 2006-10-28
> **Grym said:**
> Hi!

I have the same problem. I can't run any 32bit binaries. I've tried running with linux32, but it still said that "No such file or directory".

It works fine on 64bit Dapper.
Any idea?

Did you install the dependencies as per post #14? This worked for me on Dapper.

Paul

---

### Post by Grym on 2006-10-28
> **fabertawe said:**
> Did you install the dependencies as per post #14? This worked for me on Dapper.

Paul

Oh thanks. I must be blind. It works now, but it needed libaudio2.so (32bit) also.

---

### Post by sfarber on 2007-07-08
I still have a problem.
It says at my computer :

skype: error while loading shared libraries: libQtDBus.so.4: cannot open shared object file: No such file or directory

What Is wrong on my computer?

---

### Post by Cappy on 2007-07-08
[http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)

or

[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

Don't post in old threads please

---

### Post by Mr_bleu on 2007-07-08
Could you mark you thread as resolved? Log in and click Thread. The drop down menu will list Mark as Solved.

---

### Post by Gigcsjcx on 2007-07-08
Let me have a try.:confused:

---

