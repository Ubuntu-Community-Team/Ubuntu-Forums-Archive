---
title: "Howto: Opera with Flash 7 on 64-bit kubuntu"
date: 2007-02-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by mikerobinson on 2007-02-08
I couldn't find any other how-to's about getting Opera with flash to work on 64-bit ubuntu, so here's how I did it:

First download Opera [http://www.opera.com/download/index.dml?platform=linux](http://www.opera.com/download/index.dml?platform=linux)
Select "**Other/Static DEB**" from the drop-down list

Install Opera:
> sudo dpkg -i --force-architecture opera-static_[COLOR="Red"]stuff[/COLOR].deb
Substitute "stuff" for whatever the package name is. --force-architechture is necessary on a 64-bit system

You may also need to install the i386 version of lesstif2. I'm not sure whether this is necessary or not but I did because of [this]("http://www.ubuntuforums.org/showthread.php?t=75940") post.

Next use apt-get to install the following (again, I'm not sure if this is necessary or not, but I did it):
xlibs
motif-clients
libmotif3

Next, download the following packages:
[LIST]
[*][libx11-6_1.0.3-5_i386.deb]("http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Flibx%2Flibx11%2Flibx11-6_1.0.3-5_i386.deb&md5sum=a11404e213c4eecd17c37207b1d78211&arch=i386&type=main")
[*][libxau6_1.0.1-2_i386.deb]("http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Flibx%2Flibxau%2Flibxau6_1.0.1-2_i386.deb&md5sum=65b423e2c93774b164adea25b5b44cde&arch=i386&type=main")
[*][libxdmcp6_1.0.1-2_i386.deb]("http://packages.debian.org/unstable/libs/libxdmcp6")
[*][libxext6_1.0.1-2_i386.deb]("http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Flibx%2Flibxext%2Flibxext6_1.0.1-2_i386.deb&md5sum=4913f1d126411f7f875ce9ae596e015f&arch=i386&type=main")
[*][xlibs-dbg_4.1.0-16woody7_i386.deb]("http://security.debian.org/debian-security/pool/updates/main/x/xfree86/xlibs-dbg_4.1.0-16woody7_i386.deb")
[*][zlib1g_1.2.3-13_i386.deb]("http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fupdates%2Fmain%2Fz%2Fzlib%2Fzlib1g_1.2.2-4.sarge.2_i386.deb&md5sum=f1d25909fcc26fb653ff92083e3c6b1c&arch=i386&type=security")
[/LIST]

**Do not try to install these packages!**

Next use ark (or another archiving program) to extract the data.tar.gz file from the deb files and from that file pretty much whatever needs to go in the /usr/lib directory, extract and put in your /usr/lib/opera/9.10-20061214.1directory (you may need to substitute 9.10-20061214.1for whatever the directory name is on your system). You will need the following files:
[HTML]mike@mike:~$ ls /usr/lib/opera/9.10-20061214.1/
libICE.so.6      libXau.so.6        libXmu.so.6.2   operaplugincleaner
libICE.so.6.3    libXau.so.6.0.0    libXt.so.6      operapluginwrapper
libnpp.so        libXdmcp.so.6      libXt.so.6.0    spellcheck.so
libSM.so.6       libXdmcp.so.6.0.0  libz.so.1       works
libSM.so.6.0     libXext.so.6       libz.so.1.2.3
libX11.so.6      libXext.so.6.4.0   missingsyms.so
libX11.so.6.2.0  libXmu.so.6        opera[/HTML]
The files missingsyms.so, opera, spellcheck.so, works I believe should already be there. If not, get them from the opera .deb file.

Next [download flash]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash"). 

* Edit :: After writing this, I realized it doesn't work with Flash 9, so here's a link to download [Flash 7]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_7_linux.tar.gz"). If anyone can figure out how to get it to work with Flash 9, let me know.

Extract flashplayer.xpt and libflashplayer.so to your /usr/lib/opera/plugins directory. The contents of this directory should now be:
[HTML]mike@mike:~$ ls /usr/lib/opera/plugins/
flashplayer.xpt    libnpp.so           operapluginwrapper
libflashplayer.so  operaplugincleaner[/HTML]

I believe that's it. Extracting those files is rather tedious, but worth it IMO. Let me know if I missed anything.

---

