---
title: "installing Mplayer"
date: 2007-04-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Slimshady on 2007-04-01
I have problems installing the Mplayer. when i ran the command ./configure i got all those errors:
> Detected operating system: Linux
Detected host architecture: x86_64
Checking for cc version ... 4.1.2, ok 
Checking for host cc ... cc 
Checking for cross compilation ... yes 
Checking for CPU vendor ... AuthenticAMD (15:43:1) 
Checking for CPU type ...  AMD Athlon(tm) 64 X2 Processor 3800+ 
Checking for GCC & CPU optimization abilities ... CPU optimization disabled. CPU not recognized or your compiler is too old. 
error 
Checking for assembler support of -pipe option ... no 
Checking for compiler support of named assembler arguments ... yes 
Checking for .align is a power of two ... no 
Checking for MPlayer binary name ... mplayer 
Checking for awk ... mawk 
Checking for extra headers ... none 
Checking for extra libs ... none 
Checking for -lposix ... no 
Checking for -lm ... no 
Checking for langinfo ... no 
Checking for language ... using en (man pages:  en) 
Checking for enable sighandler ... yes 
Checking for runtime cpudetection ... no 
Checking for restrict keyword ... none 
Checking for __builtin_expect ... no 
Checking for kstat ... no 
Checking for posix4 ... no 
Checking for lrintf ... no 
Checking for round ... no 
Checking for nanosleep ... no 
Checking for socklib ... no 
Checking for inet_pton() ... no (trying inet_aton next)
Checking for inet_aton() ... no (network support disabled)
Checking for inttypes.h (required) ... no 
Checking for bitypes.h (inttypes.h predecessor) ... 
Error: Cannot find header either inttypes.h or bitypes.h (see DOCS/HTML/en/faq.html).

Check "configure.log" if you do not understand why it failed.

As I understand, im lack of some headers file, but i dont know what exactly and how to install them right.  i barely know how to install a program so i hope i didnt mess it up ....
i have 64bit system if its matter....

---

### Post by Kilz on 2007-04-01
You do know that mplayer is in the repositories, right? All you should need to do is open up a terminal and type in 
```
sudo apt-get install mplayer
```
to install it.

---

### Post by Slimshady on 2007-04-01
Oh my god, no i didnt know that, i saw somewhere i need to download it.....
ok so i installed it, but now i need codecs i think, because there are some audio and video files that still cant be played.

---

### Post by slowcoach on 2007-04-02
Install vcl from the repositories, it comes with better codec support although there will still be some files it can't handle.

Fluendo now do 64bit codecs  [https://shop.fluendo.com/](https://shop.fluendo.com/)   28 euro for the bundle, but they only work with gstreamer based applications.

---

### Post by Hutom on 2007-04-02
Check this,
Resticted Formats (Codecs): [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Otherwise copy paste in your terminal,
> sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

> wget -c [http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb)
sudo dpkg -i w32codecs_20061022-0.0_i386.deb

Hope this will help.

---

### Post by Slimshady on 2007-04-02
when i run the the first command i get the error 'E: Couldn't find package gstreamer0.10-pitfdll' . should i remove this package and continue anyway?

---

### Post by Hutom on 2007-04-02
Check whether all your repositories are enabled or not. 
Go to **system>Administration>Synaptic Package Manager>Settings>repositories**. Now 'ADD' or just **check** the community maintained **universe** and non-free (copyright restricted) **multiverse** boxes. Then close the window and click 'reload' tab in Synaptic Package Manager. 

Then copy paste the command in the terminal, ```
sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui
```

```
wget -c http://www.debian-multimedia.org/poo...2-0.0_i386.deb
sudo dpkg -i w32codecs_20061022-0.0_i386.deb 
```

See what happens.

---

### Post by Majorix on 2007-04-02
Install mencoder:
```
sudo apt-get install mencoder
```

---

### Post by Slimshady on 2007-04-02
> **Hutom said:**
> Check whether all your repositories are enabled or not. 
Go to **system>Administration>Synaptic Package Manager>Settings>repositories**. Now 'ADD' or just **check** the community maintained **universe** and non-free (copyright restricted) **multiverse** boxes. Then close the window and click 'reload' tab in Synaptic Package Manager. 
.
yes they are already checked, and i reloaded the synaptic, but still i dont have this package : gstreamer0.10-pitfdll.

> Install mencoder:
I installed it and it still cant play some files.....

---

### Post by Hutom on 2007-04-02
Paste it in the terminal and post the reply here,

```
sudo gedit /etc/apt/sources.list
```

---

### Post by Slimshady on 2007-04-02
Ho i thought i have edited this file. anyway now i  edited and uncomment all the sources and i think its ok, but just for case here it is :
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

its ok?

anyway, after editing this file i reload again the synaptic and at the end i got this error:
> W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_universe_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_universe_binary-amd64_Packages)


and still, no package called 'gstreamer0.10-pitfdll'.
thanks for your help.

---

### Post by diesel1 on 2007-04-02
> **Slimshady said:**
> when i run the the first command i get the error 'E: Couldn't find package gstreamer0.10-pitfdll' . should i remove this package and continue anyway?

Me too.

Diesel1.

---

### Post by Slimshady on 2007-04-03
may be its because the 64bit? 
i checked the web for this plugin and i saw it onli for 32bit. is there no other alternative?

---

### Post by Hutom on 2007-04-03
Ignore the package for the time being. See what happens. If it does not create a problem don't bother about it. What is the file type that mplayer cannot play? 

You may also like to try 
**preferences>video>x11driver**. 
and
**preferences>codecs and demuxer>FFmpeg's libavcodec codec family**.

---

### Post by Slimshady on 2007-04-03
Yes i installed all the other packages, skipping the missing one, but there are still some files that arent played well - for example, when i open a wmv video file i only hear sound, but there is no video. and i get this error:
> Cannot find codec matching selcted -vo video format 0x33564D57

Plus when i open a mp3 file, although it is opened correctly,  i always get the error:
> Requested audio codec family [mp3 (afm=mp3lib) not available. Enable it at compilation.

AND, i cant watch any embedded video on the internet.....

---

### Post by Hutom on 2007-04-04
Check,
[https://help.ubuntu.com/community/Re.../WindowsCodecs](https://help.ubuntu.com/community/Re.../WindowsCodecs)

You may also try gxine, gxineplugin, libxine1, libxine-extracodecs.

---

### Post by Slimshady on 2007-04-04
Ok i tried everything, i tried to install all the codecs you can possibly install, and nothing works , still the same files arent played, still i get the same errors, still i cant watch any embedded video.......](*,) ](*,) ](*,) ](*,) ..
Help! :(

---

### Post by Kilz on 2007-04-04
> **Slimshady said:**
> Ok i tried everything, i tried to install all the codecs you can possibly install, and nothing works , still the same files arent played, still i get the same errors, still i cant watch any embedded video.......](*,) ](*,) ](*,) ](*,) ..
Help! :(

This could be a product of your system not being able to run any shell scripts.

---

### Post by Hutom on 2007-04-04
Hey, come on. Don't give up. You can play other video and audio formats. Your problem is with playing .wmv files. With w32codecs installed I can play these files in totem-xine, mplayer and vlc. But I am confused why it is not working in your machine.

---

### Post by Slimshady on 2007-04-04
> **Kilz said:**
> This could be a product of your system not being able to run any shell scripts.
Hmm no actually i have formatted the linux and now im using just gnome, and the scripts are working fine on gnome (this problem was only when i used KDE), so thats not it....

> Hey, come on. Don't give up. You can play other video and audio formats. Your problem is with playing .wmv files. With w32codecs installed I can play these files in totem-xine, mplayer and vlc. But I am confused why it is not working in your machine.
maybe because of the 64bit? anyway here is the error when i try to install it :
> Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate


---

### Post by Kilz on 2007-04-04
> **Slimshady said:**
> Hmm no actually i have formatted the linux and now im using just gnome, and the scripts are working fine on gnome (this problem was only when i used KDE), so thats not it....


maybe because of the 64bit? anyway here is the error when i try to install it :

By any chance did you maybe, possibly , just happen to look at the sticky posts in the 64bit section? You know, like maybe the one on [installing applications that have problems in the 64bit version?]("http://ubuntuforums.org/showthread.php?t=191205")
If you did, did you happen to maybe, possiblly , just happen to notice that there is a link to a howto on installing mplayer and these exact codecs? That on that howto , instructions 4 and 5 may just, possibly, maybe, colud be the solution to this problem?

---

### Post by Slimshady on 2007-04-04
Actually i did try some of guides there but i just keep getting mass errors.
thanks anyway ill keep trying on myself....

---

### Post by Kilz on 2007-04-04
> **Slimshady said:**
> Actually i did try some of guides there but i just keep getting mass errors.
thanks anyway ill keep trying on myself....

When you disregard clear solutions to your problem it is like ](*,)  pounding your head into a wall.

---

