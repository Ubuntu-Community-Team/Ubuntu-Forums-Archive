---
title: "wmv9 works with xine cvs and mplayer svn without w32codecs"
date: 2006-10-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by dori on 2006-10-02
I got wmv9 support on my computer with 64bit xine and 64bit mplayer.

All you need is bunch of devel packages and CVS for xine or subversion for mplayer.
I compiled x264 from svn (don't know if that is nessasery but I did it).
And ffmpeg from svn.
The last thing you need is to compile xine-lib and/or mpayer from cvs/svn.

I just wanted to let you know of this, good luck.
P.S. I will write a small how to if anyone is intreasted

---

### Post by kuja on 2006-10-02
!!!!!!

Please, do tell. I'm VERY interested.
First though, I think I 'll see if I can figure it out myself before you post the reply :P

---

### Post by kuja on 2006-10-02
I've not yet had an oppurtunity to test yet,  however, I guess the generic proccess would look something like this, not sure if I have all the things you would need in there, but oh well.
> 
First, make sure main restricted universe and multiverse are enabled for both deb and deb-src

mkdir ~/src/ && cd src
svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
cd ~/src/

wget [http://www.mplayerhq.hu/MPlayer/releases/codecs/essential-20060611.tar.bz2](http://www.mplayerhq.hu/MPlayer/releases/codecs/essential-20060611.tar.bz2)
wget [http://www2.mplayerhq.hu/MPlayer/skins/plastik-2.0.tar.bz2](http://www2.mplayerhq.hu/MPlayer/skins/plastik-2.0.tar.bz2)

tar jxvf essential-20060611.tar.bz2
tar jxvf plastik-2.0.tar.bz2 #You can use a differen skin of your choice, if you so choose

sudo mkdir /usr/lib/win32
sudo cp essential-20060611/* /usr/lib/win32

sudo mkdir /usr/share/mplayer/skins
sudo cp -R plastik /usr/share/mplayer/skins/

dpkg -r mplayer mplayer32 #remove previous mplayers

sudo apt-get install liblogfile-rotate-perl
sudo apt-get install libconfhelper-perl
sudo apt-get install build-essential fakeroot debconf subversion
sudo apt-get build-dep mplayer

cd ~/src/mplayer
export DEB_BUILD_OPTIONS="--enable-gui" && fakeroot debian/rules binary

cd ..
dpkg -i mplayer_*deb


I've not tested it yet, I guess I need to find a wmv file to test with.

---

### Post by kuja on 2006-10-03
Awesome! It works! Looks like the FFMPEG developers have finally done it :D

---

### Post by falcon15500 on 2006-10-04
Bloody hell!

What can I say?  It works!  I compiled mplayer with the info above, and can now confirm that WMV9, XVID etc are all playing fine... Awesome news... No need for mplayer32 now...

falc

---

### Post by xstaticxgpx on 2006-10-04
thats great! just one problem though, why am i getting a "svn" unknown command, am i not supposed to do it in terminal?

---

### Post by kuja on 2006-10-04
You must not have subversion installed.

```
sudo apt-get install subversion
```

---

### Post by xstaticxgpx on 2006-10-04
ah ok, i got all the way to the last step, and then it gives me this when i try to dpkg -i

> Preparing to replace mplayer 1.0svn (using mplayer_1.0svn_amd64.deb) ...
Unpacking replacement mplayer ...
Setting up mplayer (1.0svn) ...
Upgrade refused, exiting


---

### Post by kuja on 2006-10-04
You must already have a (different version) of mplayer installed. Unfortunately, the version in the repos likes to think it's newer than the svn one. The best solution is to just remove the current mplayer first, (dpkg -r mplayer), then install the new one.

---

### Post by xstaticxgpx on 2006-10-04
i did. > xsx@xstaticxdesktopx:~/src$ sudo dpkg -r mplayer
(Reading database ... 120418 files and directories currently installed.)
Removing mplayer ...
xsx@xstaticxdesktopx:~/src$ sudo apt-get remove mplayer
Reading package lists... Done
Building dependency tree... Done
Package mplayer is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
xsx@xstaticxdesktopx:~/src$ sudo dpkg -i mplayer_*.deb
Selecting previously deselected package mplayer.
(Reading database ... 120130 files and directories currently installed.)
Unpacking mplayer (from mplayer_1.0svn_amd64.deb) ...
Setting up mplayer (1.0svn) ...
Upgrade refused, exiting

xsx@xstaticxdesktopx:~/src$


edit** fixed it, idk what i did but it just worked...

---

### Post by xstaticxgpx on 2006-10-04
also is there anyway to disable the annoying mplayer upgrade prompt? and indeed this does work with wmv9, yay! :-D

---

### Post by kuja on 2006-10-04
Can you show me what message it is that you're getting?

---

### Post by xstaticxgpx on 2006-10-04
> **kuja said:**
> Can you show me what message it is that you're getting?

[[IMG]http://show.imagehosting.us/show/1648826/0/nouser_1648/T1_-1_1648826.png[/IMG]](http://www.imagehosting.us/index.php?action=show&ident=1648826)

---

### Post by mrehorst on 2006-10-04
> **kuja said:**
> I've not yet had an oppurtunity to test yet,  however, I guess the generic proccess would look something like this, not sure if I have all the things you would need in there, but oh well.


I've not tested it yet, I guess I need to find a wmv file to test with.

Forgive my ignorance, but I am new to this stuff.  I follow your procedure and get down near the bottom and it says:

mark@athlon64:~/src/mplayer$ sudo apt-get build-dep mplayer
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for mplayer

Did I miss something?

Thanks!

MR

---

### Post by kuja on 2006-10-04
Yes, you did, you missed the first line in the quote box.

> 
First, make sure main restricted universe and multiverse are enabled for both deb and deb-src


---

### Post by mrehorst on 2006-10-04
I don't think that's the problem.  Here's what my sources.list file looks like:

## Major bug fix updates produced after the final release of the
## distribution.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb [http://debian.slimdevices.com](http://debian.slimdevices.com) stable main
deb [http://archive.kubuntu.de/ubuntu](http://archive.kubuntu.de/ubuntu) dapper main restricted universe multiverse i18n-de
deb-src [http://archive.kubuntu.de/ubuntu](http://archive.kubuntu.de/ubuntu) dapper main restricted universe multiverse i18n-de

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe main restricted multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main


Thanks,

MR

---

### Post by xstaticxgpx on 2006-10-04
> **mrehorst said:**
> I don't think that's the problem.  Here's what my sources.list file looks like:

## Major bug fix updates produced after the final release of the
## distribution.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe


for deb-src you need deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse, not just universe

---

### Post by mrehorst on 2006-10-04
That got it!  Works fine now!

Thanks,

MR

---

### Post by falcon15500 on 2006-10-04
To get rid of the annoying "upgrade from cvs version to current ubuntu version" message - I had to hack the control file of the DEB I created, with dpkg-deb and set the version higher than the current repo version.

falc

---

### Post by xstaticxgpx on 2006-10-04
> **falcon15500 said:**
> To get rid of the annoying "upgrade from cvs version to current ubuntu version" message - I had to hack the control file of the DEB I created, with dpkg-deb and set the version higher than the current repo version.

falc

yea, i just forced and then locked the version of mplayer in the synaptic package manager and the update message went away

---

### Post by weird_c00kie on 2006-10-05
well, i've failed in my attempt to get this to work.

i got up to the last few lines and then it started giving me the stuff mrehorst quoted.

i'm not entirely sure what you mean by "make sure main restricted universe and multiverse are enabled for both deb and deb-src", so that doesn't really help.

on top of that, whenever i refresh my synaptic package manager now i get an error message saying "could not download all repository indexes", showing these links:
> [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-amd64/Packages.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-amd64/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-amd64/Packages.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-amd64/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-amd64/Packages.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-amd64/Packages.bz2:) Sub-process bzip2 returned an error code (2)

---

### Post by xstaticxgpx on 2006-10-05
> **weird_c00kie said:**
> well, i've failed in my attempt to get this to work.

i got up to the last few lines and then it started giving me the stuff mrehorst quoted.

i'm not entirely sure what you mean by "make sure main restricted universe and multiverse are enabled for both deb and deb-src", so that doesn't really help.

on top of that, whenever i refresh my synaptic package manager now i get an error message saying "could not download all repository indexes", showing these links:
idk why bzip2 would be giving you a error, maybe reseting gnome will help (Control + Alt + Backspace), and by "make sure main restricted universe and multiverse are enabled" we mean do this:

sudo gedit /etc/apt/sources.list
at the beginning of the document there should be 2 lines that begin with "deb" and "deb-src" change them to look like this:


> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

hope this helps you

---

### Post by kuja on 2006-10-05
After adding those lines that xstaticxgpx mentioned, and updating, see how it's doing. If it doesn't seem to be working still, and still gives you the errors regarding bzip2 giving you an error code, it is most likely a repository problem. The best way to resolve a repository problem is to try one of the mirrors (ie: us.archive.ubuntu.com or similar), or to wait.

---

### Post by weird_c00kie on 2006-10-05
still get the bzip2 notifications after entering those two lines

as far as the original process is concerned, once i don't really know what to do once i get to
> export DEB_BUILD_OPTIONS="--enable-gui" && fakeroot debian/rules binary
cd ..
dpkg -i mplayer_*deb

the terminal says 
> dh_testdir
make: dh_testdir: Command not found
make: *** [configure-stamp] Error 127
when i enter "export DEB_BUILD_OPTIONS="--enable-gui" && fakeroot debian/rules binary"

---

### Post by kuja on 2006-10-05
How to put this... You can't do step 2 until you've successfully completed step 1. In other words, until you've got the repositories working, you can't proceed at all.

---

### Post by weird_c00kie on 2006-10-05
ah, gotcha. *crosses fingers and hopes a reset helps* hehe

*edit*

nope. a reset didn't help. still got 3 gzip2 related errors, AND, after that, another window with this slab in it:
> 
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_universe_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_universe_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_multiverse_binary-amd64_Packages)


i know this is mostly unrelated to the topic of this thread, but... who knows, maybe other people will run into this wall while trying to do this too, so it might help them too heheh

---

### Post by StandardBlueCaboose on 2006-10-05
Yeah... You rarely have to reset when using Linux. I know it's difficult at first, because Windows asks you to restart every time you do anything to the system (or it does anything to itself). 

Hooray modularity.

---

### Post by kuja on 2006-10-05
> **weird_c00kie said:**
> ah, gotcha. *crosses fingers and hopes a reset helps* hehe

*edit*

nope. a reset didn't help. still got 3 gzip2 related errors, AND, after that, another window with this slab in it: i know this is mostly unrelated to the topic of this thread, but... who knows, maybe other people will run into this wall while trying to do this too, so it might help them too heheh

Try opening up the file and changing all the lines that say [http://archive](http://archive)....... to [http://us.archive](http://us.archive)...... In other words, changing mirrors. Maybe there's a problem with the main archive right now? One way to find out, and this is it.
 
> **StandardBlueCaboose said:**
> Yeah... You rarely have to reset when using Linux. I know it's difficult at first, because Windows asks you to restart every time you do anything to the system (or it does anything to itself). 

Hooray modularity.

Hooray indeed! My current uptime is sitting at 130 hours (a bit over a week). Hooray for stability!

---

### Post by jbernardo on 2006-10-06
I decided to build mplayer (and x264) in a more "controlled" way.
What I did was as follows:
```

mkdir ~/src
cd ~/src
# you don't need this, just apply my patch to the svn dir
sudo apt-get source mplayer
sudo apt-get source x264

sudo apt-get install build-essential debhelper libx11-dev libxv-dev libpng12-dev checkinstall libavcodec-dev libaa1-dev caca-utils libcaca-dev libavcodec-dev libavifile-0.7-dev libsdl1.2debian-all libsdl1.2-dev libesd0-dev libfaac-dev libfaad2-dev libgtk2.0-dev liblame-dev libice-dev libjpeg62-dev libmatroska-dev libmad0-dev libmpcdec-dev libmp4v2-dev libmikmod2-dev libogg-dev libtheora-dev libvorbis-dev libxinerama-dev libxv-dev xlibs-dev x-dev cvs libquicktime0 libquicktime-dev fakeroot gnome-core-devel libpostproc-dev libx11-dev libxv-dev libavcodec-dev libgtk1.2-dev msttcorefonts nasm subversion
sudo apt-get install docbook-xml docbook-xsl xsltproc libxml2-utils
sudo apt-get build-dep mplayer

#x264 support seems broken, couldn't get it to work
#sudo apt-get build-dep x264
#svn co svn://svn.videolan.org/x264/trunk x264
#cd x264
#cp -r ../x264-0.cvs20060720/debian .
#fakeroot debian/rules binary
#cd ..
#sudo dpkg -i x264-bin*.deb
#sudo dpkg -i libx264*.deb

svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
tar xvjf mplayer-patches.tar.bz2
cd mplayer
#here you apply my mplayer patch
patch -p 1 < ../mplayer-debian.diff
patch -p 1 < ../mpl-config.diff
#svn version, you need to build the docs
cd DOCS/xml
make all
cd ../..
# now get the amr source and patch it
wget -c http://www.3gpp.org/ftp/Specs/latest/Rel-6/26_series/26104-610.zip
wget -c http://www.3gpp.org/ftp/Specs/latest/Rel-6/26_series/26204-600.zip
unzip 26104-610.zip
unzip 26104-610_ANSI_C_source_code.zip
mv c-code libavcodec/amr_float
unzip 26204-600.zip
unzip 26204-600_ANSI-C_source_code.zip
mv c-code libavcodec/amrwb_float

# If you're building on a amd64, dont forget to patch it with the
# patch I got from
# http://lists.mplayerhq.hu/pipermail/mplayer-users/2006-May/060497.html
#
patch -p 0 < ../amr.patch
# 
fakeroot debian/rules binary
cd ..
#workaround for ""Upgrade refused, exiting"
sudo mv /etc/mplayer/mplayer.conf /tmp

sudo dpkg -i mencoder_0.99+1.0pre8-0ubuntu7-svn20079_amd64.deb mplayer_0.99+1.0pre8-0ubuntu7-svn20079_amd64.deb
sudo mv /tmp/mplayer.conf /etc/mplayer/

```

Unfortunately, x264 r565, which had allowed me to built mpeg properly a few days ago, doesn't seem to do it anymore. So I had to disable x264 for now.
if anyone can fix the x264 problem, I'd appreciate it.

---

### Post by nestcrw on 2006-10-17
Thats awesome. thanks for figuring this out!

---

### Post by xtknight on 2006-10-17
Nice, but wma9 isn't working for me.  Is this the case for everyone?

==========================================================================
Requested video codec family [wmv9dmo] (vfm=dmo) not available.
Enable it at compilation.
Requested video codec family [wmvdmo] (vfm=dmo) not available.
Enable it at compilation.
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffwmv3] vfm: ffmpeg (FFmpeg M$ WMV3/WMV9)
==========================================================================
==========================================================================
Requested audio codec family [wma9dmo] (afm=dmo) not available.
Enable it at compilation.
Requested audio codec family [wmadmo] (afm=dmo) not available.
Enable it at compilation.
Cannot find codec for audio format 0x162.

---

### Post by kuja on 2006-10-17
I'd see if it works for me if I had a file to test with, but I lack that. One thing that we need to check is if that file will even play in 32-bit linux.

---

### Post by VFiend on 2006-10-19
If anyone here is using Edgy, the VLC in the repos is compiled with support for wmv9 so there's no need to compile anything yourself.

---

### Post by kuja on 2006-10-19
Thanks for the heads up VFiend! We should definitely get that put into the sticky, or something. One shortcoming though is I don't think there's a browser plugin for VLC, correct me if I'm wrong. I'll probably continue using mplayer from SVN just so I can use it with the KMPlayer Konqueror Plugin.

---

### Post by tall-male on 2006-10-19
> **kuja said:**
> ...One shortcoming though is I don't think there's a browser plugin for VLC, correct me if I'm wrong....

There is a very usefull plugin actually which can be used for many media players, vlc included: MediaPlayerConnectivity

Check [https://addons.mozilla.org/firefox/446/](https://addons.mozilla.org/firefox/446/)

---

### Post by kaboom on 2007-03-12
hey all,
 on this command:  
wget [http://www.mplayerhq.hu/MPlayer/rele...060611.tar.bz2](http://www.mplayerhq.hu/MPlayer/rele...060611.tar.bz2)

i get this output:  
--00:52:01--  [http://www.mplayerhq.hu/MPlayer/rele...060611](http://www.mplayerhq.hu/MPlayer/rele...060611) .tar.bz2
           => `rele...060611.tar.bz2'
Resolving [www.mplayerhq.hu](www.mplayerhq.hu)... 143.248.234.110, 199.125.85.4 1, 213.144.138.186, ...
Connecting to www.mplayerhq.hu|143.248.234.110|:80... conne cted.
HTTP request sent, awaiting response... 404 Not Found
00:52:01 ERROR 404: Not Found.

my knowledge of linux is pretty basic so it is most likely something easy like a missed repository.  any ideas?

---

### Post by Doug11 on 2007-03-12
> **kaboom said:**
> hey all,
 on this command:  
wget [http://www.mplayerhq.hu/MPlayer/rele...060611.tar.bz2](http://www.mplayerhq.hu/MPlayer/rele...060611.tar.bz2)

i get this output:  
--00:52:01--  [http://www.mplayerhq.hu/MPlayer/rele...060611](http://www.mplayerhq.hu/MPlayer/rele...060611) .tar.bz2
           => `rele...060611.tar.bz2'
Resolving [www.mplayerhq.hu](www.mplayerhq.hu)... 143.248.234.110, 199.125.85.4 1, 213.144.138.186, ...
Connecting to www.mplayerhq.hu|143.248.234.110|:80... conne cted.
HTTP request sent, awaiting response... 404 Not Found
00:52:01 ERROR 404: Not Found.

my knowledge of linux is pretty basic so it is most likely something easy like a missed repository.  any ideas?

Yea, I'm getting the same thing. It's like the site is down. Will try to look for it somewhere else. Will post if I have any luck.

---

### Post by kaboom on 2007-03-12
> **Doug11 said:**
> Yea, I'm getting the same thing. It's like the site is down. Will try to look for it somewhere else. Will post if I have any luck.

ok thanks for checking

---

### Post by KnightHawk on 2007-03-12
Ok I'm stuck. For some reason I can't "sudo mkdir /usr/share/mplayer/skins" it says mkdir: cannot create directory '/usr/share/mplayer/skins' : No such file or directory.


And I got that missing file. I looked through the codec page and picked [http://www.mplayerhq.hu/MPlayer/releases/codecs/essential-amd64-20061203.tar.bz2](http://www.mplayerhq.hu/MPlayer/releases/codecs/essential-amd64-20061203.tar.bz2)
hopefully that will work. Newer date and it says amd64. I have a amd64 turion64 in my laptop and that is what I have Ubuntu in.


I am completely new to the linux seen. So I'm not sure what I'm doing when you say make sure I have deb and deb-src. Hoping I got it right. I have all of the repositories checked in the synaptic package manager.

---

### Post by rajeev1204 on 2007-03-29
hello

Does this mean the mplayer browser plugin will play wmv 9 or we have to pass that on to the player? ( Open mplayer i.e)


I am going to try this too !. 

THe  mplayer website doesnt mention this thing .

how do u guys know these things !.:) 

Thanks a lot for this

regards

rajeev

P.S This thread is around 4 months old but i saw it only now. Been trying to get wmv9 for a long time now.

---

### Post by Kilz on 2007-03-29
> **rajeev1204 said:**
> hello

Does this mean the mplayer browser plugin will play wmv 9 or we have to pass that on to the player? ( Open mplayer i.e)


I am going to try this too !. 

THe  mplayer website doesnt mention this thing .

how do u guys know these things !.:) 

Thanks a lot for this

regards

rajeev

P.S This thread is around 4 months old but i saw it only now. Been trying to get wmv9 for a long time now.

If you have installed firefox 32 in Edgy, it has already installed that version of mplayer that can open wmv files. Right click on the file, select open with other application, at the bottom click on "use a custom command, in the box that pops up type in mplayer, then click open.

---

### Post by rajeev1204 on 2007-03-29
hi

i had followed ur howto on my dapper once and gotten that to work.

RIght know i only have 64 bit firefox and wondering if the above mentioned thing works. 

Somewhere in the initial part of this thread ROAF mentiones that they (ffmpeg?)devel) have made native 64 bit wmv 9 code to work in 64 bit mplayer

Have u tried that? 

regards

rajeev

P.S. i have followed ur howto and installed wine .THANKS

---

### Post by Kilz on 2007-03-29
> **rajeev1204 said:**
> hi

i had followed ur howto on my dapper once and gotten that to work.

RIght know i only have 64 bit firefox and wondering if the above mentioned thing works. 

Somewhere in the initial part of this thread ROAF mentiones that they (ffmpeg?)devel) have made native 64 bit wmv 9 code to work in 64 bit mplayer

Have u tried that? 

regards

rajeev

P.S. i have followed ur howto and installed wine .THANKS

nope , I haven't. I just know that the mplayer the edgy script uses has this in it.

---

### Post by hamil on 2007-04-07
Hello guys.

I have added deb-src to my sources.list, but not been able to compile.
I end up with:
```
lasse@njord:~/src$ sudo apt-get build-dep mplayer
Reading packagelists ... Done
Creating list of dependencies       
Reading state information ... Done   
E: Could not satisfy the dependencies for mplayer.
```

Badly translated to English ... 

I read the control file from the folder, ~/src/mplayer/debian and installed everything mentioned there, without any error-messages. 
sudo apt-get install libgtk1.2-dev libgtk2.0-dev libpng12-dev zlib1g-dev x-dev libx11-dev libxext-dev libxinerama-dev libxv-dev debhelper libdv4-dev

Any ideas to why it does not work?

---

### Post by rajeev1204 on 2007-04-08
have u tried feisty yet?

Totem plays wmv9 (including browser plugin) out of the box . lalala. Initially when u try to play , the codec guided wizard pops up and shows u what codecs are needed , then it does an automated install and voila -- it works . No need for mplayer now .

I thought totem was the worst player in ubuntu .Now it doesnt seem so bad .

U should try it .or install as soon as its released this month (april 19 ?)


regards

rajeev

---

### Post by hamil on 2007-04-08
@rajeev1204

Sounds nice! Will surely test it, after the stable release. This machine is a production machine, which I do not feel comfortable running beta's on ...

I am currently using Ubuntu Ultimate 1.3, but needed support for amr and 3gp with sound in mPlayer, hence the need for compiling mPlayer from source/svn. I finally made it, but the old fashioned way with compile, make and checkinstall.

Make also presented me with some errors regarding ivtv support, so i had to use the option: --disable-ivtv in ./configure. After that, everything went fine.

I am not really fond of Totem, and would like to have one media player that is able to play all my files, regardless of the video/audio format. In that way, I do belive that mPlayer is superior to all other mediaplayers. But i also must say that I really like the simplicity of VLC, it really looks appealing to me.

Brgds
Lasse

---

### Post by cypher35 on 2007-05-14
The tutorials I'm seeing in this thread all seem tailored to mplayer...  What do I need to do to compile *xine* with WMV9 support?

I'm running amd64 Kubuntu Feisty

---

### Post by kuja on 2007-05-14
> **cypher35 said:**
> The tutorials I'm seeing in this thread all seem tailored to mplayer...  What do I need to do to compile *xine* with WMV9 support?

I'm running amd64 Kubuntu Feisty
You need do nothing to have WMV9 support in Feisty. The 64-bit players, included but not limitted to Xine, Mplayer, and VLC have support for WMV9.

---

### Post by cypher35 on 2007-05-15
That's strange then, because I just tried playing an HD WMV9 video on my new setup (one that I know worked in Kaffeine on my old 32bit Dapper installation), and it just showed up as a bunch of muti-colored blobs like those old paid access channels back when cable companies used filters to block them.  I can get the video to work in VLC, but I'd rather be able to just use Kaffeine for everything.

---

### Post by brazzmonkey on 2007-05-23
i'm running feisty but i don't seem to be able to play wmv9 files... for instance : ```
$ mplayer mms://vipmms.canalplus.fr/canalplus/zapping_070523_a.wmv
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing mms://vipmms.canalplus.fr/canalplus/zapping_070523_a.wmv.
STREAM_ASF, URL: mms://vipmms.canalplus.fr/canalplus/zapping_070523_a.wmv
Resolving vipmms.canalplus.fr for AF_INET6...
Couldn't resolve name for AF_INET6: vipmms.canalplus.fr
Resolving vipmms.canalplus.fr for AF_INET...
Connecting to server vipmms.canalplus.fr[193.201.103.108]: 1755...
Connected
unknown object
unknown object
file object, packet length = 1444 (1444)
unknown object
unknown object
stream object, stream ID: 1
stream object, stream ID: 2
unknown object
data object
mmst packet_length = 1444
Cache size set to 64 KBytes
Cache fill:  0.00% (0 bytes)
ASF file format detected.
VIDEO:  [WMV3]  240x180  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 name: zapping   23-05-07
 author:
 copyright:
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Requested video codec family [wmv9dmo] (vfm=dmo) not available.
Enable it at compilation.
Requested video codec family [wmvdmo] (vfm=dmo) not available.
Enable it at compilation.
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[wmv3 @ 0xf04c30]Profile value 2 is forbidden (and WMV3 Complex Profile is unsupported)
Could not open codec.
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x33564D57.
Read DOCS/HTML/en/codecs.html!
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 48.0 kbit/3.40% (ratio: 6003->176400)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  32.3 (32.3) of 298.0 (04:58.0) 12.0% 15%
Exiting... (Quit)
```

does this mean i should recompile mplayer ?
it doesn't work with VLC either. in both players i get sound but no video.

---

