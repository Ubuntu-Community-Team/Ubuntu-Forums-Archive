---
title: "MP3 not working"
date: 2006-09-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by komputes on 2006-09-18
I just installed Ubuntu 6.06.1 [64bit] and I've tried playing my MP3's with Amarok, Juk and Rhytmbox and none of them seem to be reading my MP3 files. No DRM, no special files, just simple MP3 files. Amarok displays the tracks, just streams through all the tunes in a few seconds, never actually playing them (I think it's cuz I'm running gnome and it says it's for KDE) I thought those were desktop environements (i.e. skins) I did not know that apps could be used with one environement and not the other. That kind of sucks. Juk displays the tracks as well, but does nothing when i double click on track and finally RhythmBox (the only gnome player) warns me when i try to import a file that it is not a streaming format. NO S*** SHERLOCK!!!

](*,) I ](*,)  Need ](*,) Music ](*,) 

komputes

---

### Post by RAOF on 2006-09-18
Have you looked at [the RestrictedFormats page on the wiki](https://help.ubuntu.com/community/RestrictedFormats)?  That sounds like your problem.

---

### Post by komputes on 2006-09-18
> **RAOF said:**
> Have you looked at [the RestrictedFormats page on the wiki](https://help.ubuntu.com/community/RestrictedFormats)?  That sounds like your problem.

I just did, and I followed the directions for How to Make Things Work in a Hurry.

Some of the packages in the list arent even in the synaptic package installer, so I thought I would just install all of them from that family (with the same name).

Hope I don't screw up my OS #-o 

This linux stuff is hard...

---

### Post by komputes on 2006-09-18
Actually that didn't go though, I may have prematurely closed the window, but I did install twho packages that came up when I seached for MP3 one was called Gnomp3- I think that was XMMS. I think that one package gave me a good MP3 Player (king of like the old winamp simple interface). The other package I installed was ffmpg, but I doubt that had something to do with it. Rhythm, amarok and juk are still not working... but at least I got my music in XMMS!

---

### Post by RAOF on 2006-09-18
The only thing you **really** need for mp3 playback in Rhythmbox (and many others) is the **gstreamer0.10-plugins-ugly** package, which is in Universe.  If you **can't** find that, it means that you haven't **enabled** the Universe repository, and should look at the "Before you start" section of the RestrictedFormats page.

---

### Post by komputes on 2006-09-18
> **RAOF said:**
> The only thing you **really** need for mp3 playback in Rhythmbox (and many others) is the **gstreamer0.10-plugins-ugly** package, which is in Universe.  If you **can't** find that, it means that you haven't **enabled** the Universe repository, and should look at the "Before you start" section of the RestrictedFormats page.

I previoustly wanted to install VLC and it told me that I had to activate a Universal Repository so I did exactly that, I wnt into the repository and checked the ones that said universal (therefore having all the repositories clicked). So now all my repositories are selected (is there a problem with that?) I don't quite understand what this means or does...

Now gstreamer0.10-plugins-ugly is installed and I tried amaroK, still just speeds through all the titles, RhythmBox gives me a GStreamer encountered a general resource error and JuK still doesn't play a single song, but displays them all.

By the way the resources that were not available through Synaptic were:

gstreamer0.10-pitfdll
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-ugly-multiverse
libxine-extracodecs
w32codecs

Besides that I tried to install all the others, it ask me for the CD, I put it in and it told me there was one error durring the install. But gstreamer0.10-plugins-ugly is installed, I checked.

Any ideas?

---

### Post by John.Michael.Kane on 2006-09-18
please post your sources.list

```
sudo gedit /etc/apt/sources.list
```

---

### Post by komputes on 2006-09-18
> **SD-Plissken said:**
> please post your sources.list

```
sudo gedit /etc/apt/sources.list
```

Arrrr, me ladd. Here yee arrrr

[I][SIZE="1"]# 
deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release amd64 (20060807.1)]/ dapper main restricted


deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release amd64 (20060807.1)]/ dapper main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
[/SIZE][/I]

---

### Post by John.Michael.Kane on 2006-09-18
comment out the following two lines like shown. that will keep you from having can't read from cd error's

##deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release amd64 (20060807.1)]/ dapper main restricted

##deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release amd64 (20060807.1)]/ dapper main restricted

Add this line to bottom of your sources:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

save file.

Reload synaptic.

**Searh for this file gstreamer0.10-fluendo-mp3**

This should get you going.

---

### Post by komputes on 2006-09-19
[QUOTE=komputes;1516890]
Besides that I tried to install all the others, it ask me for the CD, I put it in and it told me there was one error durring the install. But /QUOTE]

I beleive the error it gave me came from libneon25, wtf is libneon25? I tried installing it again, it asked me for the CD again and this time it worked...


how bizzare...

---

### Post by komputes on 2006-09-19
> **SD-Plissken said:**
> comment out the following two lines like shown. that will keep you from having can't read from cd error's

##deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release amd64 (20060807.1)]/ dapper main restricted

##deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release amd64 (20060807.1)]/ dapper main restricted

Add this line to bottom of your sources:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

save file.

Reload synaptic.

**Searh for this file gstreamer0.10-fluendo-mp3**

This should get you going.

Did that, gstreamer0.10-fluendo-mp3 was already selected so i marked it for re-installation, amaroK still speeds through the tracks, Rhythmbox has improved, it now accepted 10 out of 37 mp3's and gave me errors for 27 out of the 37. Sill nothing with JuK.

and they said ubuntu was easy... thanks for the quick help by the way...:lol:

---

### Post by patrickfromspain on 2006-09-19
Ubuntu is easy. But it's not windows, so don't try to go the windows way.

I'll just say... use automatix. [www.getautomatix.com](www.getautomatix.com)

---

### Post by juicemansam on 2006-09-19
For testing purposes, can you play MP3 files with *mpg321*?

---

### Post by komputes on 2006-09-20
> **patrickfromspain said:**
> Ubuntu is easy. But it's not windows, so don't try to go the windows way.

I'll just say... use automatix. [www.getautomatix.com](www.getautomatix.com)

OMG, This thing is sweeeeeeet. I click and it automatically installs all my favorite programs. A little "Y", "Yes" or "OK" here and there, but DAMN, I did not have to compile anything, i didn't have to get dirty and griddy with any of the insides of linux, just an easy setu, thats all any n00b has ever asked for. I love Automatix! They should make every linux app available in there... Support these guys they do great work. I just installed like 15 apps in less time and less click than I would need on a windoze machine, this is the best add on to ubuntu. Revolutionary to say the least; the best thing since sliced bread. If you have Ubuntu and not automatix, it's like having life, but no oxygen. Thanks for the link, I wil pass it to all my friends from now on!

Komputes

hmmmm...this linux thing ain't so bad afterall, all though it is pretty bad A$$.

---

### Post by komputes on 2006-09-20
> **juicemansam said:**
> For testing purposes, can you play MP3 files with *mpg321*?
Haven't tried, everything work now that I re-installed it with automatix!

---

### Post by mrw on 2006-09-20
Try XMMS  - works for me.

---

### Post by komputes on 2006-09-20
> **mrw said:**
> Try XMMS  - works for me.

I used Automatix and now all my MP3 Apps work perfectly, XMMS was working from the start, i don't even know which package I checked to make it work. But serioustly amarok is really cool, check out automatix, it's awesome, they have over 20 apps installable in1 click, it's awesome.

---

### Post by BrewBelly on 2006-09-20
Hello,

I am glued to this thread.  I have exactly the same thing happening on my relatively new install of Ubuntu.  I installed Amarok because the programs under "Sound & Video" (Juk) wouldn't play my MP3 files so I went hunting for one that would.  Amarok was great! It allowed immediate play of my library.  Upon reboot, Amarok flies through the files in the playlist in a second or so and has been unuseable.  I have no way to play a simple MP3.

I was considering installing Ubuntu as the default OS on computers in my lab, but this stuff would make my students kill me.

---

### Post by BrewBelly on 2006-09-20
Sorry, 
I hadn't read your post about Automatix.  I went to install it, but it is illegal in the U.S.?  I am confused.

What did Automatix fix?  I though dependencies were "taken care of" with Ubuntu.

---

### Post by NewbieLearnLinux on 2006-09-20
Automatix is written by an honorable individual, and he releases it as free software. So it's totally legal. However, some codecs may be non-free, you download it at your own risk. Actually Automatix was designed to install and update the most "wanted-but-lack-by-default" Linux softwares.

What Automatix does is similar to Synaptic pakage manager. But Automatic does not enumerate hundreds of packages, it only concentrates on the popular ones: codecs and multimedia players (MPlayer, VLC, Beep Player, Xine, XMMS...) file sharing P2P (Bit Torrent et al) , Games on Windoze (Wine), etc...

There is a sticky topic of Automatix in the HOW-TO section. There is another one, called EasyUbuntu, does similar jobs. However the EasyUbuntu team seems a bit childish toward Automatix Team >_< ...

For Multimedia I recommend MPlayer (better install it using Automatix). It's codecs are legal and MPlayer can play most of media formats, as well as streaming online smoothly...

---

### Post by Cronjob on 2006-09-21
I'm actually having a similar problem. Amarok worked straight from the first installation (though I had to install the codecs, which I did using automatix).

Nothing has changed since it was working, except now everything else will play mp3 files fine except amarok. Kaffeine plays video and audio just fine. Mplayer does so just fine. VLC does it without problem. Amarok just fires up and behaves as if it is playing the file (including the throbbing of the visualizer/equalizer), but there is no audio whatsoever.

The audio engine is set to Xine by default. And that hasn't changed either. I really like Amarok and would prefer to use it.

I'm a long-time linux guy (since 1998), but this is actually the first time I've gotten around to playing with a window manager on linux so there's a lot of new stuff to me. Argh.

---

