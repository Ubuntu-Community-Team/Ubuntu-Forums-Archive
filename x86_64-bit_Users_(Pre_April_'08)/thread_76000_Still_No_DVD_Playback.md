---
title: "Still No DVD Playback"
date: 2005-10-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by fl1pper on 2005-10-14
Ogle... sometimes perfect video, sometimes constant dropped frames [same DVD], BUT, always, no f*****g sound at all. WTF? Says: Configure your sound settings in system blah blah. yeah okay, done. back to Ogle, same bullshit, plus, it has absolutely no place to configure its own audio routing, who wrote this retarded shit?

MPlayer on ppc, I'd say about 6 years behind MPlayerX for the Mac... constant slo-mo...nice work...next...

VLC... not happening at all on ppc, why do they even list it in Synaptic? next

Kaffeine...whoever wrote that ought to be in prison...next

Totem...WTF? What exactly does it think it's supposed to play? I'd like to know. mp3s? Big fucking deal, your bathtub will play those pretty soon, who cares?

it's pathetic, glad I still have OS X for much-needed breaks from sgml coding/editing...that's all i can say

---

### Post by dietrying on 2005-10-14
i don't know, what system u own, but on this mac mini here videoplayback works very good!

I've tested it in totem-xine, vlc and mplayer. no problem.

---

### Post by fl1pper on 2005-10-14
[QUOTE=dietrying]i don't know, what system u own, but on this mac mini here videoplayback works very good!

I've tested it in totem-xine, vlc and mplayer. no problem.[/QUOTE]
Aluminum Powerbook, 1.25 Ghz, 1 gig RAM, Radeon 9600

You have VLC working on a ppc-linux install, that right? How'd you manage that? Where's a link to vlc for a recent port to ppc? And same for MPlayer? You have NVidia, not ATI?

Anyway, I have messed with it enough. The vlc links for installs, on the ubuntuguide all point to either i386 or dead links. No big deal, I reboot into OS X, no problem, but it shouldn't be necessary.

And you are talking about DVD, not wmv, avi, mpg? All those files open fine. Curious what your setup really is, hardware on the graphics, and to see if we're talking about the same media.

---

### Post by dietrying on 2005-10-15
Yeah, I'm using a fresh breezy install on this mac mini. Before i used hoary wich worked very well too. The graphic device in this machine is an ati radeon 9200. VlC comes with ubuntu breezy. I think it's in universe or multiverse. U can simply apt-get it. 
First make sure you have insert universe and multiverse access in your /etc/apt/sources.list. Your sources should look something like this:

> deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network

deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports #main restricted universe multiverse
#deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports #main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse



If that's allright check if you have dma enabled, wich is very important for playing dvd's. You can try: hdparm -d1 /dev/hdb (that's the right device for my mac mini, perhaps on your dvd-rom you have to use /dev/cdrom). 

Also totem is ok in playing dvd's if you take a look at totem-xine (apt-get install totem-xine). 

:D Greetings and good luck

---

### Post by trash on 2005-10-26
yay finally found vlc:)... now anybody got a repo for libdvdcss2?

---

### Post by monway on 2005-10-26
[quote=trash]yay finally found vlc:)... now anybody got a repo for libdvdcss2?[/quote]

Yes, 
you can view it here 
```
http://developers.videolan.org/libdvdcss/
```
:idea:

---

### Post by trash on 2005-10-26
Thank you monway and dietrying that helped a lot!
the dvd problems i am having are ratDVD files so i am figuring it's how the files were ripped, got sound but no vid... dunno if you're having same issues fl1pper

---

### Post by monway on 2005-10-26
[quote=trash]Thank you monway and dietrying that helped a lot!
the dvd problems i am having are ratDVD files so i am figuring it's how the files were ripped, got sound but no vid... dunno if you're having same issues fl1pper[/quote]

No sweat Trash heh .. 
I have no problems with any dvd viewing .. if its an original dvd libdvdcss is all you need for a decoder. I use xine-ui and load up the themes for the controller with a skin downloader. (to most people in general don't care for that) I however, had more success rate with using xine-ui for all my dvd viewing.

a word of advice for all dvd playing if you can view it at all the most important thing is to modify /etc/hdparm.conf and add these values to the list and uncomment the ones near the bottom such as cdrom, harddrive etc.. depending on what you want. 

```
/dev/dvd {
 dma = on
}

/dev/hdc {
dma = on
}

```

Just add it to the bottom of your hdparm.conf and reboot.

this will clear up the trouble with cdrom and dvdrom viewing with xine
 if you have xine installed you can use the terminal as well and enter
```
xine-check
```
as normal user and it will tell you want you need or what's good etc.. if you have everything working for normal dvd playing.

That's all you really need. In my opinion if xine player is not for you then you can install vlc, mplayer, etc.. according to taste but it's recommended that you install xine-ui , xine, xine development headers.

If anyone has questions about that feel free to ask .. this will also work for x86 users or any linux machine with xine capability.

I hope people will find this easier to understand. 

cheers.:-\"

---

### Post by trash on 2005-10-26
thanks for the tips... there are some issues after all, nothing that looks too serious though.
I can't find xine-lib or xine-config though.

~$ xine-check
Please be patient, this script may take a while to run...
[ good ] you're using Linux, doing specific tests
[ good ] looks like you have a /proc filesystem mounted.
[ good ] You seem to have a reasonable kernel version (2.6.12-9-powerpc)
[ hint ] Architecture is ppc (not intel), assuming there is no MTRR.
         MTRR (Memory Type Range Registers) are used on intel CPUs to
         control caching mechanisms for special memory ranges. There is
         probably nothing like this on ppc CPUs...
         press <enter> to continue...

[ good ] found the player at /usr/bin/xine
[ hint ] multiple xine executables found in your PATH
         I have found more than one occurance of 'xine' in your PATH:
         /usr/bin/X11/xine
         /usr/bin/xine
         You have probably installed xine-ui more than once, or the directory
         where you have installed xine occurs more than once in your PATH.
         Technically, this is not really a problem, but it's probably
         somewhat confusing, as it's not obvious, which xine you're using.
         You should probably uninstall the copies that you don't use...
         Further tests assume, you're using /usr/bin/X11/xine
         press <enter> to continue...

[OUCH!!] no xine-config on this machine.
         This means that xine-lib is either not installed
         or it is installed in a very unusual place.
         So you should probably install xine-lib before running xine-check...
         press <enter> to continue...

[ hint ] unable to determine plugin directory
         I could not determine your plugin directory. That would be much easier
         if you had xine-config installed (see message above)...
         Note that I could not check your xine plugins.
         press <enter> to continue...

[ good ] /dev/cdrom points to /dev/hdc
[ good ] /dev/dvd points to /dev/scd0
[ hint ] Your DVD drive seems not to be attached via ATAPI.
         This might be due to the use of an ide-scsi emulation.
         If you really have a SCSI DVD drive, your SCSI controller is likely
         to do perfect DMA, so there's no reason to worry about this.
         However, if you're using ide-scsi, there is a chance that DMA is
         disabled for the DVD drive. Moreover, I don't know how to enable
         DMA in that case, so you probably have to live with some performance
         loss. (FIXME: check for /proc/ide, provide solution)
         press <enter> to continue...

[ good ] found xvinfo: X-Video Extension version 2.2
[ good ] your Xv extension supports YV12 overlays (improves MPEG performance)
[ good ] your Xv extension supports YUY2 overlays
[ good ] Xv ports:  2YUY YVYU 21VY 024I

---

### Post by monway on 2005-10-26
> thanks for the tips... there are some issues after all, nothing that looks too serious though.
I can't find xine-lib or xine-config though. 
this means you have not installed the development files and library for xine.
to remidy this just cut and paste these in the terminal 
```
sudo apt-get install libxine1c2 libxine-dev  
``` then try again using 
```
xine-check
``` you will see some minor things like some windows features that you cannot use on mac etc.. you can safely ignore those type of warnings and the ones that says you have multiple copies it's not harmful to playback (i am not sure why it has multiple copies even i have this but deleting one or the other will just muck up your system or do wierd ju-ju.  only when it says OUCH! heh .. that's when you have to fix something. as for your configs .. well a general rule is an application needs to be configured so to do that you need to launch it once so it can write xine-config you will see all of this solved when you run the xine check command.

You can't possibly fail from here out. I hope this helps. 

(I made this post for everyone not just for one person.) I hope this helps all. 

Cheers.

---

