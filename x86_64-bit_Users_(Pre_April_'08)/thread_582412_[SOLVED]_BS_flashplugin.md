---
title: "[SOLVED] BS flashplugin"
date: 2007-10-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by go_beep_yourself on 2007-10-19
I tried to install the flash plugin from Synaptic. Here is what happens.

```
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 154723 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb) ...
Setting up flashplugin-nonfree (9.0.48.0.2+really0ubuntu12) ...
Downloading...
--21:02:05--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.247.202.70
Connecting to fpdownload.macromedia.com|72.247.202.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,608,602 (2.5M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%  286.84 KB/s
   50K .......... .......... .......... .......... ..........  3%  945.67 KB/s
  100K .......... .......... .......... .......... ..........  5%  944.19 KB/s
  150K .......... .......... .......... .......... ..........  7%  950.32 KB/s
  200K .......... .......... .......... .......... ..........  9%  943.56 KB/s
  250K .......... .......... .......... .......... .......... 11%  944.83 KB/s
  300K .......... .......... .......... .......... .......... 13%  818.99 KB/s
  350K .......... .......... .......... .......... .......... 15%  943.67 KB/s
  400K .......... .......... .......... .......... .......... 17%  944.09 KB/s
  450K .......... .......... .......... .......... .......... 19%  945.13 KB/s
  500K .......... .......... .......... .......... .......... 21%  946.95 KB/s
  550K .......... .......... .......... .......... .......... 23%  280.55 KB/s
  600K .......... .......... .......... .......... .......... 25%  944.06 KB/s
  650K .......... .......... .......... .......... .......... 27%  943.01 KB/s
  700K .......... .......... .......... .......... .......... 29%  823.91 KB/s
  750K .......... .......... .......... .......... .......... 31%  939.93 KB/s
  800K .......... .......... .......... .......... .......... 33%  877.61 KB/s
  850K .......... .......... .......... .......... .......... 35%  324.53 KB/s
  900K .......... .......... .......... .......... .......... 37%  945.73 KB/s
  950K .......... .......... .......... .......... .......... 39%  251.06 KB/s
 1000K .......... .......... .......... .......... .......... 41%  164.52 KB/s
 1050K .......... .......... .......... .......... .......... 43%  492.53 KB/s
 1100K .......... .......... .......... .......... .......... 45% 1008.37 KB/s
 1150K .......... .......... .......... .......... .......... 47%  236.77 KB/s
 1200K .......... .......... .......... .......... .......... 49%  286.75 KB/s
 1250K .......... .......... .......... .......... .......... 51%  946.01 KB/s
 1300K .......... .......... .......... .......... .......... 52%  223.91 KB/s
 1350K .......... .......... .......... .......... .......... 54%  341.86 KB/s
 1400K .......... .......... .......... .......... .......... 56%  942.84 KB/s
 1450K .......... .......... .......... .......... .......... 58% 1019.18 KB/s
 1500K .......... .......... .......... .......... .......... 60%  724.32 KB/s
 1550K .......... .......... .......... .......... .......... 62%  936.77 KB/s
 1600K .......... .......... .......... .......... .......... 64%  775.53 KB/s
 1650K .......... .......... .......... .......... .......... 66%  942.96 KB/s
 1700K .......... .......... .......... .......... .......... 68%  945.14 KB/s
 1750K .......... .......... .......... .......... .......... 70%  769.61 KB/s
 1800K .......... .......... .......... .......... .......... 72%  946.54 KB/s
 1850K .......... .......... .......... .......... .......... 74%  877.47 KB/s
 1900K .......... .......... .......... .......... .......... 76%  822.52 KB/s
 1950K .......... .......... .......... .......... .......... 78%  874.81 KB/s
 2000K .......... .......... .......... .......... .......... 80%  883.27 KB/s
 2050K .......... .......... .......... .......... .......... 82%  286.06 KB/s
 2100K .......... .......... .......... .......... .......... 84%  262.35 KB/s
 2150K .......... .......... .......... .......... .......... 86%  944.41 KB/s
 2200K .......... .......... .......... .......... .......... 88%  879.80 KB/s
 2250K .......... .......... .......... .......... .......... 90%  947.11 KB/s
 2300K .......... .......... .......... .......... .......... 92%  822.09 KB/s
 2350K .......... .......... .......... .......... .......... 94%  818.69 KB/s
 2400K .......... .......... .......... .......... .......... 96%  768.54 KB/s
 2450K .......... .......... .......... .......... .......... 98%  175.97 KB/s
 2500K .......... .......... .......... .......... .......   100%  902.12 KB/s

21:02:10 (550.04 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [2608602/2608602]

Download done.
Flash Plugin installed.
invalid option -n
nspluginwrapper, configuration tool.  Version 0.9.91.5

   usage: nspluginwrapper [flags] [command [plugin(s)]]

   -h --help               print this message
   -v --verbose            flag: set verbose mode
   -a --auto               flag: set automatic mode for plugins discovery
   -l --list               list plugins currently installed
   -u --update             update plugin(s) currently installed
   -i --install [FILE(S)]  install plugin(s)
   -r --remove [FILE(S)]   remove plugin(s)

dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up flashplugin-nonfree (9.0.48.0.2+really0ubuntu12) ...
Installing from local file /var/cache/flashplugin-nonfree/install_flash_player_9_linux.tar.gz
Flash Plugin installed.
invalid option -n
nspluginwrapper, configuration tool.  Version 0.9.91.5

   usage: nspluginwrapper [flags] [command [plugin(s)]]

   -h --help               print this message
   -v --verbose            flag: set verbose mode
   -a --auto               flag: set automatic mode for plugins discovery
   -l --list               list plugins currently installed
   -u --update             update plugin(s) currently installed
   -i --install [FILE(S)]  install plugin(s)
   -r --remove [FILE(S)]   remove plugin(s)

dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
```

---

### Post by go_beep_yourself on 2007-10-19
Problem solved. I just needed to remove my previous installation of nspluginwrapper.

---

### Post by RavanH on 2007-10-21
That is strange... I have the same problem but purgeing nspluginwrapper and reïnstalling it all, doesn't resolve it :(

Are you sure you didn't do something else too? Or did you have to reboot between the uninstall and reïnstall?

---

### Post by go_beep_yourself on 2007-10-21
> **RavanH said:**
> That is strange... I have the same problem but purgeing nspluginwrapper and reïnstalling it all, doesn't resolve it :(

Are you sure you didn't do something else too? Or did you have to reboot between the uninstall and reïnstall?

Use ```
nspluginwrapper -r
``` to delete everything that ```
nspluginwrapper -l
``` shows. Then run ```
sudo find / -iname '*libflash*'
``` and delete the flash plugin(s) for your web browsers. Then ```
sudo apt-get --purge remove nspluginwrapper && sudo apt-get --purge autoremove
``` Lastly you can install flashplugin-nonfree from the repositories, and it should work. :popcorn:

---

### Post by RavanH on 2007-10-22
Thanks for you reply :)

Sadly, it doesn't work. After following all steps, purging and reinstalling, i get the following error:

```
Flash Plugin installed.
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: error while loading shared libraries: libglitz.so.1: cannot open shared object file: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-nonfree/libflashplayer.so
dpkg: fout bij afhandelen van flashplugin-nonfree (--configure):
 subproces post-installation script gaf een foutwaarde 1 terug
Fouten gevonden tijdens behandelen van:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Some of it is in dutch but the error is related to libglitz? Any thoughts on that would be greatly appreciated...

---

### Post by go_beep_yourself on 2007-10-24
> **RavanH said:**
> Thanks for you reply :)

Sadly, it doesn't work. After following all steps, purging and reinstalling, i get the following error:

```
Flash Plugin installed.
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: error while loading shared libraries: libglitz.so.1: cannot open shared object file: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-nonfree/libflashplayer.so
dpkg: fout bij afhandelen van flashplugin-nonfree (--configure):
 subproces post-installation script gaf een foutwaarde 1 terug
Fouten gevonden tijdens behandelen van:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Some of it is in dutch but the error is related to libglitz? Any thoughts on that would be greatly appreciated...

That should be easy to fix.

```
sudo updatedb && locate libglitz.so
```

Do you have it? If not, you can use apt-file to see which package contains it and then install that package. I don't understand all of your error because it is in a different language. Why don't you translate it?

---

### Post by RavanH on 2007-10-24
> **go_beep_yourself said:**
> That should be easy to fix.

```
sudo updatedb && locate libglitz.so
```
Do you have it? If not, you can use apt-file to see which package contains it and then install that package. 

Ok, that returned
```
/usr/lib/libglitz.so.1
/usr/lib/libglitz.so
/usr/lib/libglitz.so.1.0.0
```
What do I do with that info?

> **go_beep_yourself said:**
> I don't understand all of your error because it is in a different language. Why don't you translate it?

One sentence in Dutch that might give more info roughly translates to
```
dpkg: error while processing flashplugin-nonfree (--configure):
 subproces post-installation returned error code 1
```
but the Dutch language texts basically say the same as the english parts...

---

### Post by RavanH on 2007-10-24
Thinking the flashplugin is really still 32bit, it should need libglitz.so in the /user/lib32/ folder. So I tried with simply copying the 3 files from /usr/lib/ to /usr/lib32/ ... That did not solve it but it changed the error:

```
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: error while loading shared libraries: libglitz.so.1: wrong ELF class: ELFCLASS64
```

I feel I'm getting closer ;)

So 'wrong ELF class' instead of 'No such file or directory'... I figure I have to get a 32bit libglitz.so.1.0.0 instead of copying the ones from /usr/lib/ ? If so, where/how do I get them?

Thanks, Chris, for your excellent help :)

---

### Post by go_beep_yourself on 2007-10-24
> **RavanH said:**
> Thinking the flashplugin is really still 32bit, it should need libglitz.so in the /user/lib32/ folder. So I tried with simply copying the 3 files from /usr/lib/ to /usr/lib32/ ... That did not solve it but it changed the error:

```
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: error while loading shared libraries: libglitz.so.1: wrong ELF class: ELFCLASS64
```

I feel I'm getting closer ;)

So 'wrong ELF class' instead of 'No such file or directory'... I figure I have to get a 32bit libglitz.so.1.0.0 instead of copying the ones from /usr/lib/ ? If so, where/how do I get them?

Thanks, Chris, for your excellent help :)

Choose i386 here.

[http://packages.ubuntu.com/gutsy/libs/libglitz1](http://packages.ubuntu.com/gutsy/libs/libglitz1)

to extract the library from that do.

```
sudo dpkg -x name_of_package.deb
```

---

### Post by RavanH on 2007-10-24
> **go_beep_yourself said:**
> Choose i386 here.

[http://packages.ubuntu.com/gutsy/libs/libglitz1](http://packages.ubuntu.com/gutsy/libs/libglitz1)

to extract the library from that do.

```
sudo dpkg -x name_of_package.deb
```

WOW! That worked! After downloading the deb file and running ```
sudo dpkg -x libglitz1_*.deb /usr/lib32
sudo mv /usr/lib32/usr/lib/* /usr/lib32
sudo rm -R /usr/lib32/usr
sudo apt-get upgrade
``` all is well in town :)

--- I wonder how it came about that this all broke on my system... anyway...

Thanks, Chris (beep), you :guitar:

---

### Post by daflame on 2008-04-25
That may have fixed your problem, but not mine.  I have the similar error from flashplugin-nonfree, but no mention of missing libraries.  I'm running on Hardy.

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-gtkhtml2 tango-icon-theme tango-icon-theme-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
Installing from local file /var/cache/flashplugin-nonfree/install_flash_player_9_linux.tar.gz
Flash Plugin installed.
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-nonfree/libflashplayer.so
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Kilz on 2008-04-25
> **daflame said:**
> That may have fixed your problem, but not mine.  I have the similar error from flashplugin-nonfree, but no mention of missing libraries.  I'm running on Hardy.

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-gtkhtml2 tango-icon-theme tango-icon-theme-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
Installing from local file /var/cache/flashplugin-nonfree/install_flash_player_9_linux.tar.gz
Flash Plugin installed.
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-nonfree/libflashplayer.so
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

Did you do an upgrade from Gutsy or a clean install of Hardy? Have you tried completely removing flashplugin-nonfree and nspluginwrapper , purging the setup files, and reinstalled?

---

### Post by daflame on 2008-04-25
> **Kilz said:**
> Did you do an upgrade from Gutsy or a clean install of Hardy? Have you tried completely removing flashplugin-nonfree and nspluginwrapper , purging the setup files, and reinstalled?

I did an upgrade to Hardy and yes I did try to do a full purge and reinstall without success.  My error seems to be different in that there is no definite error reported.  It almost seems like nspluginwrapper is broken?

---

### Post by daflame on 2008-04-25
> **Kilz said:**
> Did you do an upgrade from Gutsy or a clean install of Hardy? Have you tried completely removing flashplugin-nonfree and nspluginwrapper , purging the setup files, and reinstalled?

Now I feel like kicking myself after I made that last post I realized that the problem when looking in the /bin fodler after the apt-get remove --purge nspluginwrapper is that nspluginwrapper had old files (npviewer and some other one I think) left behind though I'm not sure why.  My guess is that at some time in the lifetime of this computer I must have manually install nspluginwrapper.  Sorry everyone.  Maybe someone can learn from my errors.

---

