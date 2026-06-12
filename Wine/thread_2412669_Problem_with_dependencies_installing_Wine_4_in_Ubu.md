---
title: "Problem with dependencies installing Wine 4 in Ubuntu 18.04."
date: 2019-02-15
forum: Wine
---

### Post by ciltocruz on 2019-02-15
Hi all.


First of all, I want to indicate that I have looked in the forum for help and I have not come up with any solution that is "correct for me".


Installing wine with the found here I get this output:


sudo apt install --install-recommends winehq-devel


The following packages have unmet dependencies:
 winehq-devel: Depends: wine-devel (= 4.1 ~ bionic)
E: Unable to correct problems, you have held broken packages.


Then I tried to install the dependencies backwards until I have arrived at a dependency that seems to "want to reinstall the whole system". It's a joke, but the number of uninstalled packages is not normal ...


This has happened to me with this dependence:




-------------------------------------
```
winehq-devel: It depends: wine-devel (= 4.1 ~ bionic)

```
-------------------------------------
```
wine-devel: It depends: wine-devel-i386 (= 4.1 ~ bionic)

```
-------------------------------------
```
wine-devel-i386: i386: It depends: libgphoto2-6: i386 (> = 2.5.10) but it will not be installed
                        Recommend: libfontconfig1: i386 but it will not be installed
                        Recommend: libfreetype6: i386 but it will not be installed
                        Recommend: libpng16-16: i386 but it will not be installed or
                                    libpng12-0: i386 but it is not installable
                        Recommend: libsane: i386 or
                                    libsane1: i386 but will not install
                        Recommend: libtiff5: i386 but it will not be installed
```
------------------------------------
```
libgd3: i386
It depends: libfontconfig1: i386 (> = 2.12) but it will not be installed
               It depends: libfreetype6: i386 (> = 2.2.1) but it will not be installed
               It depends: libpng16-16: i386 (> = 1.6.2-1) but it will not be installed
               It depends: libtiff5: i386 (> = 4.0.3) but it will not be installed
```
-------------------------------------
```
libfontconfig1: i386: It depends: libfreetype6: i386 (> = 2.2.1) but it will not be installed

```
-------------------------------------
```
libfreetype6: i386: It depends: libpng16-16: i386 (> = 1.6.2-1) but it will not be installed

```
-------------------------------------


And right here, with > libpng16-16:i386 is where it appears that 714 packages will be deleted and only 5 will be installed. This isn't normal.


```
uname -a
Linux 4.15.0-45-generic # 48-Ubuntu SMP Tue Jan 29 16:28:13 UTC 2019 x86_64 x86_64 x86_64 GNU / Linux
```


It is important to emphasize that I am in Ubuntu 18.04 after updating like this:


Ubuntu 14.04 ---> Ubuntu 16.04 ---> Ubuntu 18.04


I have to say that in Ubuntu 14.04 Wine it worked without problems.


And no, it is not an option to reinstall the entire system.



Revised posts:
[https://forum.winehq.org/viewtopic.php?f=8&t=31949](https://forum.winehq.org/viewtopic.php?f=8&t=31949)
[https://forum.winehq.org/viewtopic.php?f=8&t=31807#p120342](https://forum.winehq.org/viewtopic.php?f=8&t=31807#p120342)
[https://forum.winehq.org/viewtopic.php?f=8&t=31950](https://forum.winehq.org/viewtopic.php?f=8&t=31950)


Any help is welcome.
Regards!

---

### Post by kc1di on 2019-02-17
Hello ciltocruz  and Welcome to Ubuntu,

Might I suggest that your trying too hard :)  The packages from wineHQ have too many dependencies that are unmet yet.  There is an easier way. Wine-stable is in the ubuntu repositories.  you can install it easily by terminal with these commands ```
sudo apt install wine-stable wine32
``` If you need a newer version of wine than the one available and tested.  The I would suggest you install playonlinux ```
sudo apt install playonlinux
```. Once installed run it go to tool tab and then manage wine version. There you can install any wine version up to the most current available.  And when you install a program through Playonlinux you will be offered the choice of using the system version or the version you've installed via POL.  Good Luck.

---

### Post by ciltocruz on 2019-02-18
Hello! Thanks for your answer.


This afternoon I will try what you say but I have proceeded to the installation by following these steps:


[https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu)


That is, I have first imported the Wine Key and then the repository.


I'll test this afternoon from the ubuntu repositories ...


Regards!

---

### Post by kc1di on 2019-02-18
The one at winehq is actually built on older stable ubuntu base and that is why your running into dependency problems.  
Good luck.

---

### Post by ciltocruz on 2019-02-18
I tried to install as you tell me. I have eliminated Wine's PPA and Wine's Key.


I have executed this:


sudo apt-get install wine-stable wine32 and I have obtained this ...


The following packages have unfulfilled dependencies:
  wine32:i386: It depends: libwine:i386 (= 3.0-1ubuntu1) but it will not be installed.


I think I will not be able to do it without doing a clean installation of the system...

---

### Post by Claus7 on 2019-02-19
Hello,

as I'm able to understand you look for a wine version that will work under ubuntu 18.04. The version that I can see in the repositories is 3.6.1. The latest one you are trying to install is 4.1. 

First of all I would suggest you to remove everything about wine, before installing anything new. Purge the ppa and from synaptic the package that is named wine. In addition purge the folder .wine.

If done, reopen synaptic and check which packages are obsolete. You should see some wine packages there. Remove them as well. When done, try to install the wine version from the repositories, unless you need to install the 4.1 version from the ppa.

If in the process more that a reasonable amount of packages are requesting you to remove them, then something wrong is taking place between the current situation and upgrade processes you have already implemented. 

Before reinstalling your system, try to clear wine first without messing with different versions of wine at the same time.
Also,
sudo apt-get update
sudo apt-get upgrade

should show no errors and under synaptic you should not have broken packages.

Regards!

---

### Post by kc1di on 2019-02-20
again I would suggest playonlinux to help you with wine.

---

### Post by ciltocruz on 2019-02-21
> **Claus7 said:**
> Hello,

as I'm able to understand you look for a wine version that will work under ubuntu 18.04. The version that I can see in the repositories is 3.6.1. The latest one you are trying to install is 4.1. 

First of all I would suggest you to remove everything about wine, before installing anything new. Purge the ppa and from synaptic the package that is named wine. In addition purge the folder .wine.

If done, reopen synaptic and check which packages are obsolete. You should see some wine packages there. Remove them as well. When done, try to install the wine version from the repositories, unless you need to install the 4.1 version from the ppa.

If in the process more that a reasonable amount of packages are requesting you to remove them, then something wrong is taking place between the current situation and upgrade processes you have already implemented. 

Before reinstalling your system, try to clear wine first without messing with different versions of wine at the same time.
Also,
sudo apt-get update
sudo apt-get upgrade

should show no errors and under synaptic you should not have broken packages.

Regards!


I am going to try these steps this afternoon. I'll tell you ...


> **kc1di said:**
> 
again I would suggest playonlinux to help you with wine.

 

I'll try also installing playonlinux


Thanks!

---

### Post by kc1di on 2019-02-22
When you install playonlinux you will find it in the menu under the games section, once running you can install which ever version of wine you want by going to the tool tab and manage wine versions.  once the wine version is installed you will be give a choice of which version to use when you install a program. Good luck.

---

### Post by ciltocruz on 2019-02-22
> **kc1di said:**
> When you install playonlinux you will find it in the menu under the games section, once running you can install which ever version of wine you want by going to the tool tab and manage wine versions.  once the wine version is installed you will be give a choice of which version to use when you install a program. Good luck.


I have installed PlayOnLinux and some versions of Wine that I can manage.


I tried installing, for example, Office and for now I am having problems (I do not have the 32bit version). I'm getting a 32 bit version to see if it works.


Then I will try Notepad ++ for example.


With PlayOnLinux can I install my own EXEs, both 64-bit and 32-bit?

---

### Post by ciltocruz on 2019-02-22
> **ciltocruz said:**
>  Voy a intentar estos pasos esta tarde. Te lo diré ... 




Intentaré también instalar playonlinux 


¡Gracias! 


This first option has not worked for me in any way. For any version of Wine that I want to install I just get to the same package whose version i: 386 uninstalls 715 packages of the system ...

---

### Post by kc1di on 2019-02-23
Yes you can install both 64 and 32 bit versions.

---

### Post by ciltocruz on 2019-02-24
I installed office 32 bits and, in spite of appearing installed in playonlinux, it does not work. It does not open the files or the program.


Then I will try to install the 64 bit exe. But I'm afraid it will not work either.

---

### Post by ciltocruz on 2019-02-26
I did not manage to install a 64-bit "setup.exe" (Office 2013 64 bits) manually. :(

---

### Post by kc1di on 2019-02-27
MS Office 2013 is quite a heavy load for wine and POL.  But here is a [blog ]("https://www.maketecheasier.com/install-microsoft-office-in-linux/")that may help you get there. The 64 bit version will not work with wine.

---

### Post by idleroamer2 on 2019-04-27
I faced the same problem of endless dependencies installing winehq-* on my Ubuntu 18.04.2 (upgraded from ubuntu 16.04). After lots of googling and trying out what worked for me at the end was to build wine locally, which was way faster than I thought. 

So here how I done it: (Token from [winehq official wiki][1])

1. clone: 
 
        git clone git://source.winehq.org/git/wine.git ~/wine-dirs/wine-source 

2. build 64-bit version: 

        cd ~/wine-dirs/wine-build/
        ../wine-source/configure --enable-win64
        make
        DO NOT INSTALL (32-bit version should be installed first)

3. build 32-bit verions:

        cd ~/wine-dirs/wine32-build/
        PKG_CONFIG_PATH=/path/to/pkgconfig ../wine-source/configure --with-wine64=../wine64-build
        make

        PKG_CONFIG_PATH should point to the location of the 32 bit pkgconfig files, probably /usr/lib or /usr/lib32. 

**DEPENDECIES**:

**libfaudio**
  
1. depends on SDL2-2.0.9 (follow [instruction][2])
2. clone [https://github.com/FNA-XNA/FAudio](https://github.com/FNA-XNA/FAudio)
3. build

        cd build_faudio/ 
        cmake ../FAudio-master/
        make -j 4

**i386 version of some libs** 

1. sudo apt-get install libx11-dev libx11-dev:i386 [from][3]
2. sudo apt-get install libfreetype6-dev:i386 libfreetype6-dev [from][4]


  [1]: [https://wiki.winehq.org/Building_Wine](https://wiki.winehq.org/Building_Wine)
  [2]: [http://www.linuxfromscratch.org/blfs/view/svn/multimedia/sdl2.html](http://www.linuxfromscratch.org/blfs/view/svn/multimedia/sdl2.html)
  [3]: [https://askubuntu.com/questions/189430/wine-x-development-files-not-found](https://askubuntu.com/questions/189430/wine-x-development-files-not-found)
  [4]: [https://askubuntu.com/questions/114460/how-to-install-lfreetype-using-wine](https://askubuntu.com/questions/114460/how-to-install-lfreetype-using-wine)

---

### Post by kc1di on 2019-04-27
I think that if you want to install msoffice that virtual box may be your best bet.
This [page]("https://vitux.com/how-to-install-virtualbox-on-ubuntu/") maybe of help.

---

### Post by machmum on 2019-05-12
> **idleroamer2 said:**
> I faced the same problem of endless dependencies installing winehq-* on my Ubuntu 18.04.2 (upgraded from ubuntu 16.04). After lots of googling and trying out what worked for me at the end was to build wine locally, which was way faster than I thought. 

So here how I done it: (Token from [winehq official wiki][1])

1. clone: 
 
        git clone git://source.winehq.org/git/wine.git ~/wine-dirs/wine-source 

2. build 64-bit version: 

        cd ~/wine-dirs/wine-build/
        ../wine-source/configure --enable-win64
        make
        DO NOT INSTALL (32-bit version should be installed first)

3. build 32-bit verions:

        cd ~/wine-dirs/wine32-build/
        PKG_CONFIG_PATH=/path/to/pkgconfig ../wine-source/configure --with-wine64=../wine64-build
        make

        PKG_CONFIG_PATH should point to the location of the 32 bit pkgconfig files, probably /usr/lib or /usr/lib32. 

**DEPENDECIES**:

**libfaudio**
  
1. depends on SDL2-2.0.9 (follow [instruction][2])
2. clone [https://github.com/FNA-XNA/FAudio](https://github.com/FNA-XNA/FAudio)
3. build

        cd build_faudio/ 
        cmake ../FAudio-master/
        make -j 4

**i386 version of some libs** 

1. sudo apt-get install libx11-dev libx11-dev:i386 [from][3]
2. sudo apt-get install libfreetype6-dev:i386 libfreetype6-dev [from][4]


  [1]: [https://wiki.winehq.org/Building_Wine](https://wiki.winehq.org/Building_Wine)
  [2]: [http://www.linuxfromscratch.org/blfs/view/svn/multimedia/sdl2.html](http://www.linuxfromscratch.org/blfs/view/svn/multimedia/sdl2.html)
  [3]: [https://askubuntu.com/questions/189430/wine-x-development-files-not-found](https://askubuntu.com/questions/189430/wine-x-development-files-not-found)
  [4]: [https://askubuntu.com/questions/114460/how-to-install-lfreetype-using-wine](https://askubuntu.com/questions/114460/how-to-install-lfreetype-using-wine)

I also having trouble install wine as OP.
Did this step, but in my case, after clone the git files, I can't find **wine-build** directory under wine-dirs. I got wine-dirs/wine-source
I got stuck after make in step 2 and can't figure out what this lines mean

```
PKG_CONFIG_PATH=/path/to/pkgconfig ../wine-source/configure --with-wine64=../wine64-build
```
since I dont have the wine32-build dirs, where should I run above commands.

thanks

---

### Post by idleroamer2 on 2019-07-24
The **wine-build (or any build directory mentioned) **is simply the build directory, you can create it anywhere you like.
 
You can find more info over PKG_CONFIG_PATH in [https://wiki.winehq.org/Building_Wine](https://wiki.winehq.org/Building_Wine)

---

