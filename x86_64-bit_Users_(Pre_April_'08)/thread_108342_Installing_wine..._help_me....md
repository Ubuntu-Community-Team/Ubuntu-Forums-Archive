---
title: "Installing wine... help me..."
date: 2005-12-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by aptsonic on 2005-12-25
I've tried every how to guide i can to install wine... 
and now i'm turning to the forum for help...

[http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")
i used wine's own ubuntu howto and i get no results...

i seemed to get the farthest with "building the wine package" section but i get an error at the end, here are the instructions and the terminal read out... please help!

The instructions:
> Building the Wine Package from Source using APT:

APT also allows easy compilation from source of a package. This is useful if there is no binary package available for your architecture, or if you wish to create a fresh .deb file from scratch. To do this, first follow the instructions for installing from the console above, except instead of running apt-get install wine run '**apt-get build-dep wine**'. This will download the needed development packages for your system to make the wine package. Then, run 'apt-get --build source wine', have a snack, and wait for the compiling to finish.

To install your newly created package (which should be in whatever directory you were in when you ran apt-get --build source), run 'dpkg -i wine*.deb' as root.

When I do "apt-get build-dep wine", it seems like to me that everything downloads without issue, (i'd post the results but its over the character limit of the forum) and if i run that command again it says that there are no upgrades...

here is step two's results (apt-get --build source wine):
> /$ sudo apt-get --build source wine
Reading package lists... Done
Building dependency tree... Done
Need to get 13.2MB of source archives.
Get:1 [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ wine 0.9.3-winehq-1 (dsc) [1137B]
Get:2 [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ wine 0.9.3-winehq-1 (tar) [13.1MB]
Get:3 [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ wine 0.9.3-winehq-1 (diff) [46.2kB]
Fetched 3B in 0s (3B/s)
Skipping unpack of already unpacked source in wine-0.9.3-winehq
dpkg-buildpackage: source package is wine
dpkg-buildpackage: source version is 0.9.3-winehq-1
dpkg-buildpackage: source changed by Scott Ritchie <scott@open-vote.org>
dpkg-buildpackage: host architecture amd64
 debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp
# Add here commands to clean up after the build process.
/usr/bin/make distclean
make[1]: Entering directory `/wine-0.9.3-winehq'
make[1]: *** No rule to make target `distclean'.  Stop.
make[1]: Leaving directory `/wine-0.9.3-winehq'
make: [clean] Error 2 (ignored)
#-/usr/bin/make -C documentation clean
dh_clean
 debian/rules build
dh_testdir
# Add here commands to configure the package.
CFLAGS="-Wall -g -O2" ./configure --host=x86_64-linux-gnu --build=x86_64-linux-gnu --prefix=/usr --mandir=\${prefix}/share/man --infodir=\${prefix}/share/info
checking build system type... x86_64-pc-linux-gnu
checking host system type... x86_64-pc-linux-gnu
checking whether make sets $(MAKE)... yes
checking for x86_64-linux-gnu-gcc... gcc -m32
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [config.status] Error 77
Build command 'cd wine-0.9.3-winehq && dpkg-buildpackage -b -uc' failed.
E: Child process failed


and of course the third and final step results in this:
> $ sudo dpkg -i wine*.deb
dpkg: error processing wine*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 wine*.deb


does anyone know what i'm doing wrong?

this is my last step in switching over from windows, and i'd like to do it soon..

---

### Post by arphe_el on 2005-12-25
Dear Aptsonic,

Please try the synaptic.

system > administration > synaptic package manager > click the search and type wine then  right click in your mouse and click mark for installation then click apply 

hope this will do the trick since it work out for me that way and now i'm runnin my wine but since i change my screen from 800x600 to 1024x768 still working out to make it to 800x600 screen set-up again. GODspeed!

---

### Post by aptsonic on 2005-12-25
[QUOTE=arphe_el]Dear Aptsonic,

Please try the synaptic.

system > administration > synaptic package manager > click the search and type wine then  right click in your mouse and click mark for installation then click apply 

hope this will do the trick since it work out for me that way and now i'm runnin my wine but since i change my screen from 800x600 to 1024x768 still working out to make it to 800x600 screen set-up again. GODspeed![/QUOTE]

this is a screen shot of my synaptic repositories
[http://aptsonic.com/myspace/ubuntuscreens/Screenshot.png]("http://aptsonic.com/myspace/ubuntuscreens/Screenshot.png")

this is the results of a search for wine:
[http://aptsonic.com/myspace/ubuntuscreens/Screenshot-1.png]("http://aptsonic.com/myspace/ubuntuscreens/Screenshot-1.png")

if u can't tell, there's no wine... what am i doing wrong?

thanks for the advice!

---

### Post by dannyngweekiat_85 on 2005-12-26
i got the smae error as urs... the build source fail.. dun know what i did wrong there.

Found this [http://www.ubuntuforums.org/showthread.php?t=96620](http://www.ubuntuforums.org/showthread.php?t=96620)
. This will install it on a 64 bit system... which i am using. Think u r using it also.

---

