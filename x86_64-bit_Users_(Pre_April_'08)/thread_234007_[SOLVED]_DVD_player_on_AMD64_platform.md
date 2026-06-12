---
title: "[SOLVED] DVD player on AMD64 platform"
date: 2006-08-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by Cariboo1938 on 2006-08-10
Hi all AMD 64 users, 
I discussed the DVD issue already at the Beginners Forum, with no result, except that I should bring it to this forum. Here is the history of the case and I appreciate if somebody would have the nerve and patients to read it...and maybe drop I line with a good advice....

The discussion until now

Cariboo
Hello all,
I have Ubuntu 6.06 on a 64 bit computer successfully installed and I tried to play a DVD movie. I got the error message:  
[COLOR="Blue"]'No  URI handler implemented for "dvd"'[/COLOR].
What is to do?

Jagot
Go to this page:

[COLOR="DarkOrange"]http://help.ubuntu.com/community/RestrictedFormats[/COLOR] 

On the menu to the left you will see something about playing encrypted DVD's. Click on the link and it will take you to the instructions you need to enable DVD playback.

Cariboo
I went to this page and did everthing as it was described for the AMD64 architecture. I checked if the installation of the necessary packages was ok and when I ran the command line
*sudo /usr/share/doc/libdvdread3/examples/install-css.sh*
I got the message: [COLOR="DarkOrange"]command not found[/COLOR]

Jagot
OK, so you're sure you have build-essential, debhelper and fakeroot installed before you run it?

Cariboo
Yes, I'm ablolutely sure because I checked with Synaptic Package Manager what packages are installed!

Jagot
I have no idea what to do. [COLOR="Magenta"]You really need other 64bit users to help you out with this one[/COLOR] - 'fraid I'm only a 32er. Good luck.

---

### Post by John.Michael.Kane on 2006-08-10
libdvdread3 is not listed under your synaptic? this could be the main reson  why dvd's won't play. if you can run a search under synaptic for libdvdread3.

---

### Post by Kilz on 2006-08-10
> **Cariboo1938 said:**
> Hi all AMD 64 users, 
I discussed the DVD issue already at the Beginners Forum, with no result, except that I should bring it to this forum. Here is the history of the case and I appreciate if somebody would have the nerve and patients to read it...and maybe drop I line with a good advice....

The discussion until now

Cariboo
Hello all,
I have Ubuntu 6.06 on a 64 bit computer successfully installed and I tried to play a DVD movie. I got the error message:  
[COLOR="Blue"]'No  URI handler implemented for "dvd"'[/COLOR].
What is to do?

Jagot
Go to this page:

[COLOR="DarkOrange"]http://help.ubuntu.com/community/RestrictedFormats[/COLOR] 

On the menu to the left you will see something about playing encrypted DVD's. Click on the link and it will take you to the instructions you need to enable DVD playback.

Cariboo
I went to this page and did everthing as it was described for the AMD64 architecture. I checked if the installation of the necessary packages was ok and when I ran the command line
*sudo /usr/share/doc/libdvdread3/examples/install-css.sh*
I got the message: [COLOR="DarkOrange"]command not found[/COLOR]

Jagot
OK, so you're sure you have build-essential, debhelper and fakeroot installed before you run it?

Cariboo
Yes, I'm ablolutely sure because I checked with Synaptic Package Manager what packages are installed!

Jagot
I have no idea what to do. [COLOR="Magenta"]You really need other 64bit users to help you out with this one[/COLOR] - 'fraid I'm only a 32er. Good luck.


Did you install the libdvdread3 package?

---

### Post by Cariboo1938 on 2006-08-11
> **SD-Plissken said:**
> libdvdread3 is not listed under your synaptic? this could be the main reson  why dvd's won't play. if you can run a search under synaptic for libdvdread3.
Thanks SD-Plissken, you are right it's not installed....Where do I get it?
would *apt-get -install libdvdread3* do the job?

---

### Post by Cariboo1938 on 2006-08-11
> **Kilz said:**
> Did you install the libdvdread3 package?Yes I did after I read SD-Plissken's reply. It looks like the information in [http://help.ubuntu.com/community/RestrictedFormats](http://help.ubuntu.com/community/RestrictedFormats) is not complete. There it says:[QUOTE=http://help.ubuntu.com/community/RestrictedFormats]Enable playback of encrypted DVD's

    o Applies to the AMD64 architecture only: 
  
  Installing libdvdcss2

    The install-css.sh script will compile the libdvdcss2 library for you         
    instead of downloading a prebuilt binary. Make sure you install the 
    debhelper, build-essential and fakeroot packages first. 

    Then issue the command:

                  sudo /usr/share/doc/libdvdread3/examples/install-css.sh

        o Your DVD player should now play back encrypted DVDs.[/QUOTE]
If I issue the command I get again "command not found"....

*sudo: /usr/share/doc/libdvdread3/examples/install-css.sh: command not found* 

In my installed packages list is no libdvdcss2 either. I download this from Debian repository, is that ok?

---

### Post by John.Michael.Kane on 2006-08-11
> **Cariboo1938 said:**
> Thanks SD-Plissken, you are right it's not installed....Where do I get it?
would *apt-get -install libdvdread3* do the job?

you should be able to use **sudo aptitude install libdvdread3** also downloading libdvdcss2 from Debian repository should be ok. I think once you get the libdvdread3 file you should be good to go.

---

### Post by Cariboo1938 on 2006-08-11
> **SD-Plissken said:**
> you should be able to use **sudo aptitude install libdvdread3** also downloading libdvdcss2 from Debian repository should be ok. I think once you get the libdvdread3 file you should be good to go.now it is definetivly installed: > /usr/lib
/usr/lib/libdvdread.so.3.2.0
/usr/share
/usr/share/lintian/overrides/libdvdread3 
/usr/share/doc
/usr/share/doc/libdvdread3
/usr/share/doc/libdvdread3/copyright
/usr/share/doc/libdvdread3/changelog.Debian.gz
/usr/share/doc/libdvdread3/install-css.sh
/usr/share/doc/libdvdread3/changelog.gz
/usr/share/doc/libdvdread3/README.Debian
/usr/share/doc/libdvdread3/TODO
/usr/lib/libdvdread.so.3  I still get the same message when trying to play a DVD movie:> **[COLOR="Red"]Totem could not play 'dvd:///media/dvdrecorder'.[/COLOR]** *[COLOR="Red"]No URI handler implemented for "dvd".[/COLOR]* Any other thought?

---

### Post by Kilz on 2006-08-11
You ran ```
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
```
After getting the libdvdread3 package installed?

---

### Post by Cariboo1938 on 2006-08-11
> **Kilz said:**
> You ran ```
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
```
After getting the libdvdread3 package installed?Yes I did, here is the terminal print out:>  
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
sudo: /usr/share/doc/libdvdread3/examples/install-css.sh: command not found

I figured out in directory libdvdread3 is no '/examples': 
> 
owner@Owner-Desktop:~$ sudo -s
root@Owner-Desktop:~# cd /usr/share/doc
root@Owner-Desktop:/usr/share/doc# cd libdvdread3
root@Owner-Desktop:/usr/share/doc/libdvdread3# cd examples  
bash: cd: examplesls: No such file or directory
root@Owner-Desktop:/usr/share/doc/libdvdread3# ls -l 
changelog.Debian.gz  copyright       README.Debian
changelog.gz         install-css.sh  TODO
root@Owner-Desktop:/usr/share/doc/libdvdread3# 

therefore the message 'command not found'.

I changed the command line to:
```

*sudo /usr/share/doc/libdvdread3/install-css.sh* 
```

and this happened:
> 
root@Owner-Desktop:/usr/share/doc/libdvdread3#  sudo /usr/share/doc/libdvdread3/install-css.sh
--20:27:41--  [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_amd64.deb](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_amd64.deb)
           => `/tmp/libdvdcss.deb'
Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.30.198
Connecting to www.dtek.chalmers.se|129.16.30.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 26,176 (26K) [text/plain]
100%[====================================>] 26,176         3.53K/s    ETA 00:00
20:27:53 (3.53 KB/s) - `/tmp/libdvdcss.deb' saved [26176/26176]
Selecting previously deselected package libdvdcss2.
(Reading database ... 82746 files and directories currently installed.)
Unpacking libdvdcss2 (from /tmp/libdvdcss.deb) ...
Setting up libdvdcss2 (1.2.5-1) ...
root@Owner-Desktop:/usr/share/doc/libdvdread3#

I thought I'm through with this one and I tried my movie "National Lampoon's Cristmas Vacation" and again:
> 
**[COLOR="Red"]Totem could not play 'dvd:///media/dvdrecorder'[/COLOR]**.
[COLOR="Blue"]No URI handler implemented for "dvd"[/COLOR]
I'm having a beer now.....to comfort my frustration...:confused:

---

### Post by Kilz on 2006-08-12
> **Cariboo1938 said:**
> Yes I did, here is the terminal print out:
I figured out in directory libdvdread3 is no '/examples': 


therefore the message 'command not found'.

I changed the command line to:
```

*sudo /usr/share/doc/libdvdread3/install-css.sh* 
```

and this happened:


I thought I'm through with this one and I tried my movie "National Lampoon's Cristmas Vacation" and again:

I'm having a beer now.....to comfort my frustration...:confused:

Have you tried to open it up with another media player like mplayer?

---

### Post by Cariboo1938 on 2006-08-12
> **Kilz said:**
> Have you tried to open it up with another media player like mplayer?No, I didn't yet. It looks like Ubuntu only came with Totem. Where can I get another player?

---

### Post by John.Michael.Kane on 2006-08-12
```
sudo aptitude install mplayer
``` should download it for you.

---

### Post by Cariboo1938 on 2006-08-12
> **SD-Plissken said:**
> ```
sudo aptitude install mplayer
``` should download it for you.It didn't work: > owner@Owner-Desktop:~$ sudo aptitude install mplayer
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find package "mplayer".  However, the following
packages contain "mplayer" in their name:
  kmplayer-base kmplayer-doc kmplayer-konq-plugins
[B][COLOR="Red"]No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/COLOR][/B]
Need to get 0B of archives. After unpacking 0B will be used.
owner@Owner-Desktop:~$
Is MPlayer for 64-bit platform available?

---

### Post by John.Michael.Kane on 2006-08-12
Cariboo1938 mplayer is listed under synaptic with my sources.list. can you post your sources.list ```
sudo gedit /etc/apt/sources.list
```

---

### Post by BatteryCell on 2006-08-12
For me okle did the trick, might help.

---

### Post by kuja on 2006-08-12
Alrighty then, lets try this.

First, do you know what drive your dvd recorder is? it should be something such as /dev/hdc or something of the like. Once you've got that, lets pull up the abundantly useful terminal.

```
totem dvd:///dev/hd?
``` (The question mark being the rest of the identifier for you drive)

Type in:

First, pull up a terminal and do the following:
```
sudo gedit /etc/apt/sources.list
```

Add the following line to this file, and save
```
deb http://archive.ubuntu.com/ubuntu dapper universe
```

Next, in the terminal again, type ```
sudo apt-get update && sudo apt-get install mplayer
```

That should get it installed without any problems.

Try running this command from a terminal and see if it works.
```
mplayer dvd:///dev/hd?
``` (the ? mark referring again to the identifier of your drive)

And hopefully one, if not the other, will do it for you.Good luck.

---

### Post by Cariboo1938 on 2006-08-12
> **kuja said:**
> Alrighty then, lets try this.

First, do you know what drive your dvd recorder is?  No I don't! How excactly can I identify it. There is a line in fstab: ```
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
```but I have installed a CD-RW drive and DVD-drive. It looks like the system knows only one drive.?????????????
when I run ```
otem dvd:///dev/hdb
```I get the Error message:> Totem could not play 'dev:///dev/hdb'
No URI handler implemented for "dev".I believe my DVD drive is not known at all...

---

### Post by kuja on 2006-08-12
Hmm, well that certainly is odd now isn't it?
Is it an IDE drive (most internal), Firewire(some external), or a USB Most External) drive? 

Can you give me the output of this command run in a terminal:

```
ls -l /media/dvdrecorder
```

---

### Post by RedBoot on 2006-08-13
Am going to throw in some suggestions for setting up a DVD player from the book 'Ubuntu Hacks' (Great book by the way.)
Note: Not tested by me yet!
Install gen stuff: 
```
sudo apt-get install totem-xine vorbis-tools sox faad lame imagemagick ffmpeg mjpegtools
```
Install gstreamer stuff:
```
sudo apt-get install gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg gstreamer0.8-mad gstreamer0.8-plugins gstreamer0.8-lame
```
Register gstreamer:
```
gst-register-0.8
```
Install codecs:
```
wget ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb

```I noticed the 'i386' above and figured it wouldn't work, but when I tried to navigate the ftp site listed, nothing regarding codecs showed up. The legalities of this may be involved since it's this part that deals with the DRM of the DVD movies. May have luck at the [MPlayer site]("http://www.mplayerhq.hu/design7/dload.html")  
Also MPlayer for you is, I believe:
sudo apt-get install mplayer-amd64

Hope some of this might help. I'll follow this thread to hear how this turns out for you.

---

### Post by jmcguinness on 2006-08-13
Hi, I had the same issue but it all seems easily resolvable with Easyubuntu

open a terminal window and proceed as follows:

command 1:
wget [http://robotgeek.org/eu/easyubuntu-3.0.tar.gz](http://robotgeek.org/eu/easyubuntu-3.0.tar.gz)

command 2:
tar -zxf easyubuntu-3.01.tar.gz

command 3:
cd easyubuntu

command 4:
sudo python easyubuntu.py

You will receive a dialogue box with 4 tabs, MultiMedia being the first.  Select the third check box with the label "libdvdcss: Read commercial encrypted DVDs"

---

### Post by Cariboo1938 on 2006-08-13
> **SD-Plissken said:**
> Cariboo1938 mplayer is listed under synaptic with my sources.list. can you post your sources.list ```
sudo gedit /etc/apt/sources.list
```> deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release amd64 (20060531)]/ dapper main restricted

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universeHere is my sources list, and I think I need to un-comment the universe source, right?

---

### Post by John.Michael.Kane on 2006-08-13
Cariboo1938 you can un-comment all those except the deb-src unless you plan to build from soruce. 

Then Run:
```
sudo aptitude update
```

you may get a notification icon letting you know you have updates. also you should now see mplayer,and any other missing files you may have needed. I'm hoping you won't have to go though a reinstall.

---

### Post by Cariboo1938 on 2006-08-13
> **kuja said:**
> Hmm, well that certainly is odd now isn't it?
Is it an IDE drive (most internal), Firewire(some external), or a USB Most External) drive? 

Can you give me the output of this command run in a terminal:

```
ls -l /media/dvdrecorder
```Both are IDE drives (internal connected with this wide,flat cable).
Here we are....> owner@Owner-Desktop:~$ ls -l /media/dvdrecorder
ls: /media/dvdrecorder: No such file or directory
owner@Owner-Desktop:~$
Now CD-drive here...But both CD-drives are somehow working...I can boot, burn, play music..

---

### Post by Cariboo1938 on 2006-08-13
> **jmcguinness said:**
> command 2:
tar -zxf easyubuntu-3.01.tar.gzI wonder why I only got easyubuntu-3.0.tar.gz and not ...-3.01...?> 
You will receive a dialogue box with 4 tabs, MultiMedia being the first.  Select the third check box with the label "libdvdcss: Read commercial encrypted DVDs"What comes after this....just try to play the movie???
If I do so I get the well known message:
[SIZE="3"][COLOR="SeaGreen"]Totem could not play 'dvd:///media/dvdrecorder'.[/SIZE]
No URI handler implemented for "dvd"[/COLOR]

---

### Post by hajk on 2006-08-13
Been away from this forum for a few days and now, while catching up on a few threads, I'm reading the above with mounting exasperation. Why?
Because the whole issue would have been easily resolved if the OP had followed the instructions in RestrictedFormats *exactly*, starting at the top and working his way through to the bottom without skipping a step... 

Mind you, I consider this not so much a failing of the OP (and others trying to help him out) but a short-coming in the Ubuntu project. Let us hope that  the upcoming Edgy release at least contains clear instructions as to the RestrictedFormats that are impossible to miss.

(I feel better now, thank you.;) )

---

### Post by kuja on 2006-08-13
Cariboo, can you give the output of "cat /etc/fstab" in a terminal?

---

### Post by Cariboo1938 on 2006-08-13
> **kuja said:**
> Cariboo, can you give the output of "cat /etc/fstab" in a terminal?I certainly can:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda3       /Storage        ext3    defaults        0       2
/dev/sda1       /boot           ext3    defaults        0       2
/dev/sda5       /home           ext3    defaults        0       2
/dev/sda6       /usr            ext3    defaults        0       2
/dev/sda7       /var            ext3    defaults        0       2
/dev/sda8       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/pktcdvd/0=/dev/cdrom   /mnt/cdrw    udf    noauto,noatime,rw,dev,users 0  0

PS:I just thought maybe'hajk' is ...I'll do what he recommended!

---

### Post by kuja on 2006-08-13
Certainly worth a shot, I'd say.

I've never seen something like your last mount point though, quite odd, however it gives me a thing or two that may make what I was trying to do work.

```
totem dvd:///dev/pktcddvd/0 OR totem dvd:///dev/cdrom
```
Now that we have the mount point, one of those may work. Trying the same thing in MPlayer may also work too.

---

### Post by Cariboo1938 on 2006-08-13
> **kuja said:**
> I've never seen something like your last mount point though, quite odd, however it gives me a thing or two that may make what I was trying to do work.This line came in because I followed some instructions submitted by mepiswala in order to get udftools installed...with the goal to do packet writing to use CD-R/Ws like a large Floppy disk, i.e. write/add to the CD-R/W files and directories without beeing forced to erase the whole CD.
But it didn't work yet. I can uncomment this line and the we have the original fstab.

---

### Post by Cariboo1938 on 2006-08-13
> **hajk said:**
> Been away from this forum for a few days and now, while catching up on a few threads, I'm reading the above with mounting exasperation. Why?
Because the whole issue would have been easily resolved if the OP had followed the instructions in RestrictedFormats *exactly*, starting at the top and working his way through to the bottom without skipping a step...
Mind you, I consider this not so much a failing of the OP (and others trying to help him out) but a short-coming in the Ubuntu project. Let us hope that  the upcoming Edgy release at least contains clear instructions as to the RestrictedFormats that are impossible to miss.
(I feel better now, thank you.;) )That's ok! I hope I didn't make you angry....
I read it through and through but stumbled at the line 
> "Make sure you have enabled the Universe and Multiverse repositories.See Managing Repositories in Ubuntu or Kubuntu for help with this".I was afraid to do this because of the serious warnings in my sources.list.> ## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that [COLOR="Red"]software in
## universe WILL NOT receive[/COLOR] any review or updates from the Ubuntu security
## team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
##N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that [COLOR="Red"]software in backports WILL NOT receive[/COLOR] any review
## or updates from the Ubuntu security team.
New to Linux it is very easy to mess up the whole installation, you know what I mean? So, how save is it really to use these repositories?:?:

---

### Post by Cariboo1938 on 2006-08-13
> **kuja said:**
>  
```
totem dvd:///dev/pktcddvd/0 OR totem dvd:///dev/cdrom
```
Now that we have the mount point, one of those may work. Trying the same thing in MPlayer may also work too.Thanks for the hint...I tried it and got the following terminal message: > root@Owner-Desktop:~# totem dvd:///dev/pktcddvd/0

** (totem:8187): WARNING **: Failed to connect to the session bus: No reply within specified time
root@Owner-Desktop:~# totem dvd:///dev/cdrom

** (totem:8246): WARNING **: Failed to connect to the session bus: No reply within specified time

Also Totem player window opened on the screen and I got the message in the Error window: > otem could not play 'dvd:///dev/pktcddvd/0'
No URI handler implemented for "dvd".

Totem could not play 'dvd:///dev/cdrom'
No URI handler implemented for "dvd".What or who on earth is this "URI handler"?

---

### Post by kuja on 2006-08-13
It should be plenty safe enough to use the Universe and Multiverse repositories, or they of course wouldn't be there :) Just bear in mind that they won't be getting any security updates... so if you're running a mission critical server or something, those repositories might not be for you, or something like that.

As per the URI handler thing, I think it's a pain in everyone's [expletive deleted].

Try making sure the following are installed:
```
 sudo apt-get install libdvdread3 libdvdnav4 libdvdplay0
```
In addition, I expect you probably need to have the infamous libdvdcss2 installed also.

---

### Post by RAOF on 2006-08-13
> **kuja said:**
> ...
In addition, I expect you probably need to have the infamous libdvdcss2 installed also.
...AMD64 packages of which can be had from [my repository](raof.dyndns.org/falcon) (mirrors: [Germany](ubuntu.moshen.de) [US](ubuntu.systemadministrator.org)).

---

### Post by Cariboo1938 on 2006-08-13
> **kuja said:**
> As per the URI handler thing, I think it's a pain in everyone's [expletive deleted]:-$ 
Try making sure the following are installed:
```
 sudo apt-get install libdvdread3 libdvdnav4 libdvdplay0
```
In addition, I expect you probably need to have the infamous libdvdcss2 installed also.I checked in "Synaptic" Installed:
> Information when checking "Synaptic" Installed (local or obsolete)

libdvdread3
library for reading DVDs 
Status: installed

libdvdcss2
a portable abstraction library for DVD decryption
Status: installed

libdvdnav4
The DVD navigation library
Status: installedMissing is 'libdvdplay0' which is not in the list of uninstalled packages either. How do I get it?

---

### Post by hajk on 2006-08-14
> **Cariboo1938 said:**
> That's ok! I hope I didn't make you angry....
I read it through and through but stumbled at the line 
I was afraid to do this because of the serious warnings in my sources.list.
New to Linux it is very easy to mess up the whole installation, you know what I mean? So, how save is it really to use these repositories?:?:

Ah, those warnings... they're just covering themselves. A bit like bear warnings in your neck of the woods... don't keep you from leaving the house, do they? Never had any problems with packages from uni- and multiverse, besides what is the worst that could happen?

---

### Post by Cariboo1938 on 2006-08-14
> **hajk said:**
> ...., besides what is the worst that could happen?For me, it's the fact, that I would have to spend time again to get some basics running ...Modem,DVD player,Dual Boot,...which just don't work when you get the Live CD. And for somebody who is new to Linux, that can be very frustrating.

PS:-k 
I wonder if anybody knows What or Who **[FONT="Comic Sans MS"][SIZE="3"][COLOR="DarkOrchid"]"URI handler"[/COLOR][/SIZE][/FONT]** is. He/she/it prevents obviosly my computer from playing DVDs!?:-k

---

### Post by kuja on 2006-08-15
I've had issues with it before, Cariboo, and I've still got an ace or two up my sleeve. Give me a few minutes yet, I'll have it working for ya ;)

Hmm, I forget how exactly I did it though... and I've got it working right now (just because I have a LOT of packages installed).

Try installing ogle and vlc, not because they're special or important, or even to use them directly - but because they carry quite a few dvd related dependencies. (I do believe that is what I did before). Give it a try.

```
apt-get install ogle vlc
```

---

### Post by Lonthong on 2006-08-15
Hi Caribo,
I am also very new to linux (2 weeks old). If I understand you properly you want to play DVD using Totem that came in the installation package (Totem-gstreamer). However according to this [link]("https://help.ubuntu.com/community/RestrictedFormats"), Totem-gstreamer doesnot/cannot play DVD. So that could be the source of all yr problem.

What I did was:
Enable universe & multiverse
Install Totem-xine (It automatically uninstall Totem-gstreamer) & libxine-extracodecs 
install the debhelper, build-essential and fakeroot packages
apt-get install liba52-0.7.4-dev libdvdread3-dev libdvdnav-dev
sudo /usr/share/doc/libdvdread3/examples/install-css.sh

Now, I am able to play any DVD movie
However, to play WMV9 file you must follow other howto in a separate thread BY Cong if I remember correctly

---

### Post by Cariboo1938 on 2006-08-15
> **kuja said:**
> I've had issues with it before, Cariboo, and I've still got an ace or two up my sleeve. Give me a few minutes yet, I'll have it working for ya ;)

Hmm, I forget how exactly I did it though... and I've got it working right now (just because I have a LOT of packages installed).

Try installing ogle and vlc, not because they're special or important, or even to use them directly - but because they carry quite a few dvd related dependencies. (I do believe that is what I did before). Give it a try.

```
apt-get install ogle vlc
```
Thank you kuja for the help: I started apt-get install... I got this > The following NEW packages will be installed:
  liba52-0.7.4 libdc1394-13 libdvbpsi4 libgsm1 libid3tag0 libiso9660-4 libmad0
  libmodplug0c2 libmpeg2-4 libtar libvcdinfo0 libwxgtk2.6-0 libxosd2 ogle vlc
  vlc-plugin-alsa wxvlc
0 upgraded, 17 newly installed, 0 to remove and 0 not upgraded.Need to get 12.3MB of archives.
After unpacking, 34.3MB of additional disk space will be used.  This takes about 2hrs on my Dial-Up connection. But that's ok. I hope we are getting there[-o< 
Can 'Totem' player itself be the problem? This is the only player I find under -->Application -->Sound & Video.

---

### Post by Lonthong on 2006-08-15
> **RAOF said:**
> ...AMD64 packages of which can be had from [my repository](raof.dyndns.org/falcon) (mirrors: [Germany](ubuntu.moshen.de) [US](ubuntu.systemadministrator.org)).
Seems that yr repo is down at the moment

> **Cariboo1938 said:**
> 
Can 'Totem' player itself be the problem? This is the only player I find under -->Application -->Sound & Video.
Yes, I believe that is yr main problem. see my post above

---

### Post by kuja on 2006-08-15
Oh, should have known... I forgot that Ubuntu (as opposed to Kubuntu) defaulted to GStreamer (as opposed to Xine, which Kubuntu uses in its players).

Cariboo - if this is correct, then this should probably work.

```
sudo apt-get install totem-xine
sudo apt-get remove totem-gstreamer
```

---

### Post by Cariboo1938 on 2006-08-15
> **Lonthong said:**
> Hi Caribo,
I am also very new to linux (2 weeks old). If I understand you properly you want to play DVD using Totem that came in the installation package (Totem-gstreamer). However according to this [link]("https://help.ubuntu.com/community/RestrictedFormats"), Totem-gstreamer doesnot/cannot play DVD. So that could be the source of all yr problem.

What I did was:
Enable universe & multiverse
Install Totem-xine (It automatically uninstall Totem-gstreamer) & libxine-extracodecs 
install the debhelper, build-essential and fakeroot packages
apt-get install liba52-0.7.4-dev libdvdread3-dev libdvdnav-dev
sudo /usr/share/doc/libdvdread3/examples/install-css.sh

Now, I am able to play any DVD movie
However, to play WMV9 file you must follow other howto in a separate thread BY Cong if I remember correctlyMany thanks to all of you helping me to get this thing running. Finally, with following the steps in your short description, Longthong, the DVD player is working now. BTW hajk was right when he said my problem could have been solved earlier when I only had followed the instruction "exactly" in [http://help.ubuntu.com/community/RestrictedFormats](http://help.ubuntu.com/community/RestrictedFormats). For newcomers these instructions are often hard to grasp because, in my opinion, they are often written in a language only experts can understand. Thanks again...SD-Plissken, Kilz, kuja, Lonthong, ...all others in this thread.=D>

---

### Post by scapps on 2006-09-05
Thank you for the information.  I cannot install libxine-extracodecs.  When I do a aptitude search, it does not find it.  Attached is my sources.list file.....

---

### Post by Kilz on 2006-09-05
> **scapps said:**
> Thank you for the information.  I cannot install libxine-extracodecs.  When I do a aptitude search, it does not find it.  Attached is my sources.list file.....

That package is in the multiverse. [Click here to learn how to add the multiverse and universe repositories.]("http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories")

---

