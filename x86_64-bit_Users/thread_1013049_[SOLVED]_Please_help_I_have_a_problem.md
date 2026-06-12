---
title: "[SOLVED] Please help I have a problem"
date: 2008-12-16
forum: x86 64-bit Users
---

### Post by BigCityCat on 2008-12-16
I am getting a message you have broken dependicies. Here are 3 different messages I am getting in 3 different areas. I was trying to install mediubuntu so I could set up my dvd players to watch movies.

I am using kubuntu intrepid 8.10

I am inexperienced.

This came from the terminal

libdvdread3 is already the newest version.
libdvdread3 set to manually installed.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gstreamer0.10-plugins-ugly: Depends: libsidplay1 but it is not going to be installed
  libavformat52: Depends: libavcodec51 (>= 3:0.svn20080206-8) but it is not going to be installed or
                          libavcodec-unstripped-51 (>= 3:0.svn20080206-8) but it is not going to be installed
  sun-java6-jre: Depends: sun-java6-bin (= 6-10-0ubuntu2) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-10-0ubuntu2) but it is not going to be installed
  vlc-nox: Depends: libavcodec51 (>= 3:0.svn20080206-8) but it is not going to be installed or
                    libavcodec-unstripped-51 (>= 3:0.svn20080206-8) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

ALSO this came from terminal

Selecting previously deselected package libdvdcss2.
(Reading database ...
dpkg: serious warning: files list file for package `sun-java6-jre' missing, assuming package has no files currently installed.
121902 files and directories currently installed.)
Unpacking libdvdcss2 (from .../dvdcss-X10320/libdvdcss.deb) ...
Setting up libdvdcss2 (1.2.10-0.2medibuntu1) ...

This came from adept package handler.

Download failed.
The list of errors is attached. The recovery for this case is currently not implemented. If you see 404 errors, it might be useful to try fetching package lists (see the Sources tab) and retrying the operation.

The error was: 
APT Error. Context:
****Package download failed, 
****I wasn't able to locate a file for the sun-java6-jre package. This might mean you need to manually fix this package. (due to missing arch), 
****: , 
****: , 
****: , 
****: , 
****: , 
****: , 
****: , 
****: , 
****: , 
****: , 
****: , 
****: , 
****: , 
****: , 
****: , 
****: , 
****: , 
****: , 
****: , 
****: , 
****: , 
****: , 
****: , 
****: , 
****: , 
****:

---

### Post by cariboo on 2008-12-16
You may want to install kubuntu-restricted-extras, this should fix your dependencies problem. It will also install java and the flashplugin-nonfree. In a terminal type:

```
sudo apt-get install kubuntu-restricted-extras
```

Jim

---

### Post by BigCityCat on 2008-12-16
I got it thanks. I just added sun-java6-jre to the adept package manager and it was listed with the option upgradeable so I upgraded it and asked me to accept the conditions and then I  installed. It's working. Thanks

---

