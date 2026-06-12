---
title: "64 bit masochists ?"
date: 2005-05-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by NoTiG on 2005-05-10
Why use 64 bit ? I mean.. i have an amd64 3000 processor.. and i put the 64 bit ubuntu on it... but im thinking about erasing it and just putting the 32 bit on here. whats the point anyway? i mean there is no performance difference right? . just problems and woes >< . for instance... the FLash plugin for firefox... will not work on 64 bit distros >:(

[http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4](http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4)

---

### Post by CospeFogo on 2005-05-10
[QUOTE=NoTiG]Why use 64 bit ? I mean.. i have an amd64 3000 processor.. and i put the 64 bit ubuntu on it... but im thinking about erasing it and just putting the 32 bit on here. whats the point anyway? i mean there is no performance difference right? . just problems and woes >< . for instance... the FLash plugin for firefox... will not work on 64 bit distros >:(

[http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4](http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4)[/QUOTE]
 There's this great howto: [http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

I've followed it and now I'm able to install 32 bits apps, including Firefox with Flash plugin and Zsnes. That's really simple.

---

### Post by FluffyElmo on 2005-05-10
I think it depends what you are doing. Overall 64bit and 32bit are comparable, there is a performance edge in 64bit but not so much that you'll really miss it. 

For some applications though, 64bit is *much* faster. For video encoding, ffmpeg is 64bit optimized and fast as hell. For Java development I also see a difference in my IDE performance, which is more than welcome and hard to give up day-to-day. 

The only remaining annoyances IMHO are Flash and the Windows Media codecs. Flash can be solved as CaspeFogo points out. So can the codecs if you install 32bit MPlayer, though myself I'll just wait until ffmpeg finishes their WMV implementation.

---

### Post by NoTiG on 2005-05-10
Interesting. its not just that though... i just tried to install the libdvdcss ... so i could watch DVD's with totem-xine........ but I can't even find it with apt-cache search... it doesnt seem like the file is in the repositories. Now i could go to sourceforge and DL it and then compile from scratch right? But there isnt a package for ubuntu yet for 64 bit distros is what i am understanding? Just a minor annoyance but still.........

edit: Btw this was more of a question.. is there a 32 bit package for libdvdcss ??? . sorry . i am all paranoid since ndiswrapper is nowhere to be found in the repositories for the 64 bit distro!.

---

### Post by FluffyElmo on 2005-05-10
Make sure you enable Universe/Multiverse. And have you seen the unnofficial Ubuntu Guide? It's aimed at 32bit but most of the solutions apply to 64bit as well. [http://www.ubuntuguide.org](http://www.ubuntuguide.org) 

For your specific questions, you can get libdvdcss from the marillat repository:
```
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
```

Unfortunately for the ndiswrapper I think you have to build from source. There was a post about it in this forum in the last week, it's an annoyance but at least it works  :neutral: 

There is also a 64bit specific version of the marillat repository here which I used to get ffmpeg, transcode and a few other multimedia packages.
```
deb http://cyberspace.ucla.edu/marillat/ unstable main 
```

However there may be repository conflicts, since Hoary has come out some of the Debian packages have changed. If you really need a package from there you could always add a Debian repository temporarily to grab the odd package dependency you need...but update only what you need, and only if you have to. [http://amd64.debian.net/README.mirrors.html](http://amd64.debian.net/README.mirrors.html)

---

### Post by mthaddon on 2005-05-10
I use 64bit for another reason - it's the future. Since I can afford to go through a little extra hassle to get things working I like to be able to use/test Ubuntu 64bit so that the platform becomes more stable through any bugs I submit or documentation I can help put together.

If everyone just stuck with 32bit, then we'd never get a good 64bit platform. 

Now, I don't mean by that that everyone should be using it - I'm no 64bit zealot. Just that if you can and you're up for it, it's a cool thing to be able to do.

Thanks, Tom

---

### Post by NoTiG on 2005-05-10
[QUOTE=FluffyElmo]Make sure you enable Universe/Multiverse. And have you seen the unnofficial Ubuntu Guide? It's aimed at 32bit but most of the solutions apply to 64bit as well. [http://www.ubuntuguide.org](http://www.ubuntuguide.org) 

For your specific questions, you can get libdvdcss from the marillat repository:
```
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
```

Unfortunately for the ndiswrapper I think you have to build from source. There was a post about it in this forum in the last week, it's an annoyance but at least it works  :neutral: 

There is also a 64bit specific version of the marillat repository here which I used to get ffmpeg, transcode and a few other multimedia packages.
```
deb http://cyberspace.ucla.edu/marillat/ unstable main 
```

However there may be repository conflicts, since Hoary has come out some of the Debian packages have changed. If you really need a package from there you could always add a Debian repository temporarily to grab the odd package dependency you need...but update only what you need, and only if you have to. [http://amd64.debian.net/README.mirrors.html](http://amd64.debian.net/README.mirrors.html)[/QUOTE]
 TY for those depositories... I installed libdvdcss2 ! . I can now play the dvd's . Now i just got to figure out.... why there is no sound. ANd how to fix my graphics card driver... glxgears runs at 114 FPs....... causing dvd playback to be choppy.

---

### Post by FluffyElmo on 2005-05-10
It may not be your video driver, though that is a very low score...

First try enabling DMA on your DVD drive, for whatever reason it's disabled on removable media by default. My dvd is at */dev/hdc*, and the command is: * sudo hdparm -d1 /dev/hdc*. Just typing *mount* should give you a list of devices in your system.

Second try changing your audio and video drivers in your media player. Ubuntu uses ESD for audio, try changing your player driver to it as well. For video some drivers work for me, others not so well and some cause player crashes. Trial and error may find a better choice than the default.

For MPlayer the drivers are in preferences. The global preferences are in System->Preferences->Multimedia System Selector

Hopefully you can get your DVD playback working properly playing with teh settings above. For your video driver, search the forum and check the wiki. There are a lot of how-tos on Nvidia/ATI driver installation.  

Good Luck...

---

### Post by rodri on 2005-05-12
64 bit ubuntu simply suxxxxxxxxxxx

I can't find most packages 

- gnomeburner and its dependencies
- wine
- xcompmgr 
- transset

and so on

can't compile most sources, have trouble with every thing I try... I give up!!!

---

### Post by dewey on 2005-05-12
Rodri, try enabling more repositories...
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Also, 64bit is still in it's infancy, if no one uses it, there will be no incentive to develop for it, and there will be limited bug fixes, due to lack of testers.  WindowsXP 64bit has recently come out, which means 64bit versions of many apps will be released shortly.  If you want, go back to 32bit, but you can run programs on 64bit under a 32bit chroot, and have it just as good.  Even if you don't notice a speed increase, atleast use the 64bit version, and help test it.

---

### Post by psoulocybe on 2005-05-13
I have been using 64 and it's really not that big of a deal to learn how to install 32 bit appz.  It runs well and you get to help step through to the future.  I agree that people using it is the only way it's going to develop well.

---

### Post by gradavies on 2005-05-13
I'm new to Linux and loaded 64 bit Ubuntu a month ago. Followed advice on loading java, flash, adjusting screen resolution, enabling sound, etc. Some worked, most didn't. Also couldn't print from OOo1.1.3 or get chroot working. When free CD arrived from Ubuntu, loaded i386 version, deleting 64 bit (and Windows ME!). Been using this for a week. Everything working brilliantly, now have:

1280x1024 screen resolution with Nvidea
OOo2 beta loaded and printing!
Realplayer, flash, java - all working
Sound working all programmes

I realise it's lack of 64 bit support by third party programmes causing problems at the moment but newbies trying 64 bit could be put off for good. Should be some kind of obvious warning with 64 bit.

I'm really impressed with Ubuntu i386 and may try 64 bit again in the future, once all the above issues have been sorted.

---

### Post by Sam on 2005-05-13
I use Ubuntu 64bit because it's a kind of challenge for me (I haven't too much experience on linux). I can dig a lot, instead of having everything working out-of-the-box. Yes, this is masochism, but I learn a lot by doing this. And I agree with mthaddon: 64bit is the future.

---

### Post by zxc on 2005-05-13
I had no idea that there were any differences between AMD64 and i386 Ubuntu when I downloaded the .iso. I just thought it was optimized to run smoother on the different platforms.

I've spent a good hours in #ubuntu trying to get the "w32codecs" and getting "realplayer" to work with nobody understanding what's wrong  :roll: ...I only really discovered the differences 2 weeks + into using Ubuntu.

Looking back on it now I probably would have gone with i386 as a n00b user but I've managed on AMD64 and it would be too much hassle to change it now.

---

### Post by NoTiG on 2005-05-13
I Got the 32 bit distro. and everything is smooooooth sailing :P . All i had to do was install the distro.. then run this [automated script](http://www.ubuntuforums.org/showthread.php?t=22646) 

and everything "just works" :P . it installs all the codecs necessary. the only other thing i would recommend is [this smal guide](http://www.ubuntuforums.org/showthread.php?t=17727)  to embed totem into firefox and make everything seamless. 

I still have my 64 bit partition.. i have 3 partitions.. one 32bit ubuntu, one 64, and windows. Unfortunately....... i cannot give up my windows partition because i am an isketch addict and it is a shockwave based game :( . i tried using codeweavers crossover shockwave plug in and it still would not work .

---

### Post by nautilus on 2005-05-13
sorry, but might i chime this in...

if you have issues with ubuntu-amd64, i **dare** you to try any other amd64 linux distro.  start with debian-sid, hah! :)

---

### Post by Crad on 2005-05-13
Gentoo's pretty much in pace with Ubuntu with 64 bit support.  I've been using 64 bit Gentoo on AMD64 Servers without issue.  I think it's important to note that it's usually the programs that have 64 bit difficulties, not so much the distro.

I've found Ubuntu on my AMD64's (home and work) to be solid enough for every day use, and using a chroot env, I have access to everything I need that the 64 bit environment doesn't currently allow.

The OOo team, for example, have acknowledged that there are issues with OOo and 64 bit compilations.

[QUOTE=nautilus]sorry, but might i chime this in...

if you have issues with ubuntu-amd64, i **dare** you to try any other amd64 linux distro.  start with debian-sid, hah! :)[/QUOTE]

---

### Post by mrscintilla on 2005-05-16
The automated script rocks!!! cannot wait to try the totem plugin too.
If someone can built an duplicate of the scripts for the 64-bit side, I'll switch to 64 in an instant.  Until then, 32 is my friend..

[QUOTE=NoTiG]I Got the 32 bit distro. and everything is smooooooth sailing :P . All i had to do was install the distro.. then run this [automated script](http://www.ubuntuforums.org/showthread.php?t=22646) 

and everything "just works" :P . it installs all the codecs necessary. the only other thing i would recommend is [this smal guide](http://www.ubuntuforums.org/showthread.php?t=17727)  to embed totem into firefox and make everything seamless. 

I still have my 64 bit partition.. i have 3 partitions.. one 32bit ubuntu, one 64, and windows. Unfortunately....... i cannot give up my windows partition because i am an isketch addict and it is a shockwave based game :( . i tried using codeweavers crossover shockwave plug in and it still would not work .[/QUOTE]

---

### Post by brad.arth on 2005-05-16
I've been working on 64-bit linu for 3 days now, Im a newbie and figured out how to install a few things, but all in all Im having horrible times trying to even compile things, they all give processor unknown errors, whether I use chroot or linux32 it doesnt matter. I think once a few months goes by things will clear up a bit, but until then I may have to switch to 32-bit to get a good taste in my mouth for linux.

---

### Post by NoTiG on 2005-05-16
[QUOTE=mrscintilla]The automated script rocks!!! cannot wait to try the totem plugin too.
If someone can built an duplicate of the scripts for the 64-bit side, I'll switch to 64 in an instant.  Until then, 32 is my friend..[/QUOTE]

```
#!/bin/bash
#												
# +*** WANRING WARNING WARNING WARNING WARNING ***----------------------------------------------+
# | ryan (ubuntu-geek) / site@ubuntuforums.org							|	
# | Purpose of this script is to automate/tweak setting up a new ubuntu system.			|
# |												|
# | This script installs 3rd party programs and are not supported by canonical/ubuntu.		|
# | If this script blows up your installation it's not my fault :)				|
# |												|
# | This script has been tested on Hoary Hedgehog 5.04.						|
# | +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++	|
# | This script will perform the following functions. 						|
# | 1. Install beep-media-player, gstreamer0.8-mad (for mp3's)					|
# | 2. Enable debian-marillat, universe and multiverse repo's					|
# | 3. Install latest java and enable java in firefox						|
# | 4. Give you nice forms in firefox								|
# | 5. Install streamtuner 									|
# | 6. Install msttcorefonts									|
# | 7. Install latest acrobat reader and firefox plugin						|
# | 8. Install dvd playback support								|
# | 9. Install w32codecs and dvd libraries							|
# | 10. Install gnomebaker									|
# | --------------------------------------------------------------------------------------------|
# | 5/2/2005 - using backports for java | remove acrobat reader its broke			|
# +---------------------------------------------------------------------------------------------+

### global options ###
wget="/usr/bin/wget"
apt="/usr/bin/apt-get"
core_packages="build-essential" 
media_packages="beep-media-player gstreamer0.8-mad streamtuner xine-ui totem-xine"
misc_packages="msttcorefonts libdvdcss2 gnomebaker gftp"
#java_jre_url="http://download.ubuntuforums.org/ubuntusetup/jre-1_5_0_02-linux-i586.bin"
firefox_forms="http://download.ubuntuforums.org/ubuntusetup/ff-forms.tar.gz"
#sources_list_url="http://download.ubuntuforums.org/ubuntusetup/sources.list"
misc_fonts_url="http://download.ubuntuforums.org/ubuntusetup/miscfonts.tar.gz"

### functions ###
check_errs()
{
  if [ "${1}" -ne "0" ]; then
    echo "ERROR # ${1} : ${2}"
    exit ${1}
  fi
}
### main script starts here ###

### snag the updated sources.list

#cd /etc/apt/ && mv sources.list sources.list.orig && ${wget} ${sources_list_url}
#gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
#gpg --armor --export 1F41B907 | sudo apt-key add -
#check_errs $? "There was an error downloading the sources.list."
#sleep 5

### lets update the apt repo
${apt} update
check_errs $? "There was an error in apt-get update."
sleep 5

### lets install build-esstential
echo "Additional packages maybe need to be installed select yes if asked"
${apt} install ${core_packages}
check_errs $? "There was an error in ${core_packages} installation."
sleep 5

### lets install media_packages
echo "Additional packages maybe need to be installed select yes if asked"
${apt} install ${media_packages}
check_errs $? "There was an error in ${media_packages} installation."
sleep 5

### lets install misc_packages
echo "Additional packages maybe need to be installed select yes if asked"
${apt} install ${misc_packages}
check_errs $? "There was an error in ${misc_packages} installation."
sleep 5

### lets install misc windows fonts that are not in the msttcorefonts package
echo "Installing Misc fonts"
cd /usr/share/fonts/truetype/msttcorefonts
${wget} ${misc_fonts_url}
tar xvzf miscfonts.tar.gz
rm -f miscfonts.tar.gz
check_errs $? "Misc Fonts Installation has failed..."
sleep 5

### lets install firefox forms
echo "Installing firefox forms"
cd /usr/lib/mozilla-firefox/
${wget} ${firefox_forms}
tar xvzf ff-forms.tar.gz
rm -f ff-forms.tar.gz
check_errs $? "Firefox forms Installation has failed..."
sleep 5

### lets install java
#echo "Installing java"
#${apt} install sun-j2re1.5

echo "If you made it this far job well done."
``` 

This will work for 64 bit. the only problem is... it doesnt install the flash plugin for mozilla, the win32 codecs, and java... because those are all 32 bit. ALso note that this doesn't modify your /etc/apt/sources.list .. because you have to make a slight modification.

Before you run that script you have to backup your repositories

sudo cp /etc/apt/sources.list /etc/apt/sources.list.orig

then you have to run gedit cut and paste this:

[http://download.ubuntuforums.org/ubuntusetup/sources.list](http://download.ubuntuforums.org/ubuntusetup/sources.list)

and comment out 2 of the lines:

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

by putting a # in front of them. then you have to save the file as your /etc/apt/sources.list

---

### Post by gratefulfrog on 2005-05-25
[QUOTE=brad.arth]I've been working on 64-bit linu for 3 days now, Im a newbie and figured out how to install a few things, but all in all Im having horrible times trying to even compile things, they all give processor unknown errors, whether I use chroot or linux32 it doesnt matter. I think once a few months goes by things will clear up a bit, but until then I may have to switch to 32-bit to get a good taste in my mouth for linux.[/QUOTE]

Well I hate to scare you but unless you're willing to become a software devt. expert, those compilation errors won't be going away in the near future.  There is a great deal of complexity in getting the 32bit chroot platform to work 100%, within a 75% working 64bit OS.  

The more demanding the apps you want to install or build, the more grey hairs you will get!

This is independent of the distro Ubunut, Fedora, Suse, etc.

I stick it out because I want to contribute to the future, not wallow in the past. 

Good Luck!  ;-) 
Good Luck

---

