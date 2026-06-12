---
title: "DVD Playback Problems with Gutsy 64bit"
date: 2007-11-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Rog-Mahal on 2007-11-13
Perhaps this would be a more productive place to post this problem. 

So: I have installed (I think) all of the correct libraries from medibuntu in order to play dvds, namely: libdvdcss2, libdvdread3, libdvdnav4. And I have probably installed every media player known to man including totem-xine, vlc, mplayer, and ogle. Yet, I can't play dvds. When I run vlc from terminal, I get the following errors:

```
VLC media player 0.8.6c Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: THE_ROYAL_TENENBAUMS_DISC_1
libdvdnav: DVD Serial Number: 2caa9747
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/roger/.dvdnav/THE_ROYAL_TENENBAUMS_DISC_1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000133
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00015feb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000170df
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0035133b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x003546d4
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_1.VOB (0x003546d4)!!
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1522 ***
*** for info_length % sizeof(uint32_t) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1522 ***
*** for info_length % sizeof(uint32_t) == 0 ***

libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed - CRASHING
vlc: vm.c:218: ifoOpenNewVTSI: Assertion `0' failed.
Aborted (core dumped)
```

Does anyone understand why libdvdcss can't crack the css keys? I would really like some help as I have no other ideas and I'm contemplating downgrading to 32 bit because I don't know what else to do.

---

### Post by marco123 on 2007-11-13
All I do as part of my install routine is try to play all my video/music type files and install the codecs when prompted, then:

If your on 32bit just run: sudo /usr/share/doc/libdvdread3/install-css.sh

If 64bit you will need to run this command first: "sudo apt-get install debhelper build-essential fakeroot " then run the above command.

This has worked on about 7 or 8 different installs in a row for me.

EDIT: I use ogle to play DVDs with full menus.

---

### Post by Rog-Mahal on 2007-11-15
Thanks for the info. I've successfully gotten DVD's to play, but only in VLC and VERY choppily. hdparm -t is giving me 3MB/sec buffered read speeds. I'm not sure where to turn for this problem, probably not this forum as this sounds like a macbook-related issue.

---

### Post by zorkerz on 2007-11-17
ive been unsuccessful so far getting dvds to play back. I installed all of the but  totem still sends me a link to the codec page. im using an x60 base for a thinkpad x61.

---

### Post by binary_bob on 2007-11-17
This is for those of you having problems playing commercial DVD's with 64bit Gutsy.
Medibuntu should solve your problems.
1) Add the medibuntu repository for Ubuntu 7.10 "Gutsy Gibbon"

 sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

2)Add the GPG Key.

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

3) To play Encrypted DVD's.

 sudo apt-get install libdvdcss2 

(i think this package gets installed by one of the media players anyway, but it's not a problem)

4)To play Non-Native Media Formats.

 sudo apt-get install w64codecs

5)The next part is installing the appropriate players.
6)System>Amin>Synaptic Package Manager.
7)Search.... xine
8)Install the following packages.

gxine
totem-xine
xine-ui

These three packages should install the rest of the requirements for playing various media.

From a clean install, doing the above, i have the following packages installed (search...xine)
gxine
libdmx1
libxine1
libxine1-ffmpeg
libxinerama1
totem
totem-xine
xine-ui

Now i can play Encrypted DVD's.
(I did a quick test with Lord of the Rings)
I hope this makes sense and is useful to you.

---

### Post by zorkerz on 2007-11-17
thanks for the well written post binary_bob. Im not at my computer right now so  I cannot be absolutely sure but I have done all the steps you wrote and a similarly instructed on the three relevant community docs pages.
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) -> for ubuntu-restrictd-extras
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) -> for the various players
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) -> for medibuntu, libdvdcss2

at this point im hoping for a stupid mistake on my part

---

### Post by ViRMiN on 2007-11-17
Just spotted the thread, and as soon as I read the initial post, I thought "libdvdcss2"/"libdvdread3" from Medibuntu but, binary_bob got in there first.  That's the way to go though, works for me as well on encrypted discs.

---

### Post by binary_bob on 2007-11-17
Thanks for the confirmation Virmin,
 I don't think all of the players are necessary, but one of them certainly opened the others for playing DVD's, stage 6 divx's etc.
If anybody is having problems, Don't Give Up, 64bit is worth the effort.

---

### Post by zorkerz on 2007-11-17
Well i have dvd playback now. Im not sure what did it. I switched over to totem-xine instead of gstreamer but now vlc and gxine and the xine-ui all work as well when they did before. Must be some odd package i missed.
cheers all

PS I don't know about anyone else but if anything I have found gutsy 64 to work better than gutsy 32. Only real difference I have noticed is that suspend and hibernate work more often in gutsy 64 for me.

---

### Post by binary_bob on 2007-11-17
ZORKERZ,
When i installed one of the players gstreamer was removed.
movie player, xine movie player, gxine play DVD's etc.
gxine plays streaming media and other stuff as well.

---

### Post by zorkerz on 2007-11-17
It looks to me like gstreamer has the ability to play back dvds but cannot do the dvd menus requiring one to specify each track and things like chapters will not work. So I guess until menus do work xine is a better backend for totem. I just assume not install another player I don't like all the clutter or the idea of  having programs installed I don't need.
cheers

---

### Post by crjackson on 2007-11-18
> **binary_bob said:**
> This is for those of you having problems playing commercial DVD's with 64bit Gutsy.
Medibuntu should solve your problems.
1) Add the medibuntu repository for Ubuntu 7.10 "Gutsy Gibbon"

 sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

2)Add the GPG Key.

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

3) To play Encrypted DVD's.

 sudo apt-get install libdvdcss2 

(i think this package gets installed by one of the media players anyway, but it's not a problem)

4)To play Non-Native Media Formats.

 sudo apt-get install w64codecs

5)The next part is installing the appropriate players.
6)System>Amin>Synaptic Package Manager.
7)Search.... xine
8)Install the following packages.

gxine
totem-xine
xine-ui

These three packages should install the rest of the requirements for playing various media.

From a clean install, doing the above, i have the following packages installed (search...xine)
gxine
libdmx1
libxine1
libxine1-ffmpeg
**libexinerama1**
totem
totem-xine
xine-ui

Now i can play Encrypted DVD's.
(I did a quick test with Lord of the Rings)
I hope this makes sense and is useful to you.

I followed this except I can't find** libexinerama1**, what do I have to do to get this package, and what does it do?

Also, I get choppy sound sound.  It pauses during dvd playback about every 10 seconds.  Any ideas how to fix that?  I get the problem with VLC and every installed player EXCEPT MPlayer Movie Player, it has no audio issues, but when I skip forward a chapter, it reprots gnome screen saver error.

---

### Post by binary_bob on 2007-11-19
crjackson,
libexinerama1 is a typo error.sorry
It should be libxinerama1.
I don't use vlc, so i can't help with that player.
I don't have playback or sound issues with gxine, movie player or xine movie player.
Perhaps your problems are media or drive related..just a thought.
I know there are posts that cover similar issues to yours, perhaps an answer lies out there already.
Not a solution, but i hope it helps.
ps.
The player that gives me grief is, mplayer movie player. I am trying to sort that one out at the moment.
*Typo error fixed

---

### Post by crjackson on 2007-11-19
> **binary_bob said:**
> crjackson,
libexinerama1 is a typo error.sorry
It should be libxinerama1.
I don't use vlc, so i can't help with that player.
I don't have playback or sound issues with gxine, movie player or xine movie player.
Perhaps your problems are media or drive related..just a thought.
I know there are posts that cover similar issues to yours, perhaps an answer lies out there already.
Not a solution, but i hope it helps.
ps.
The player that gives me grief is, mplayer movie player. I am trying to sort that one out at the moment.
*Typo error fixed

Okay thanks.  Strange how the one player that gives you problems is the only player that gives me none:confused:

---

### Post by binary_bob on 2007-11-19
crjackson,
Mplayer movie player problem solved.(i didn't have the preferences sorted out properly.)
So, all of my players play properly. Still doesn't help you though does it.
I will see what i can find out.

---

### Post by binary_bob on 2007-11-19
crjackson,
Just a thought,
Maybe there is a conflict with the players. 
Remove vlc,
reboot.
Try players again.

---

### Post by crjackson on 2007-11-19
> **binary_bob said:**
> crjackson,
Just a thought,
Maybe there is a conflict with the players. 
Remove vlc,
reboot.
Try players again.

Actually, I think it has something to do with ALSA.  The other players default to this, but MPlayer Movie Player lets me change to the older method.  I think it's called OSS or something like  that.  When MPlayer uses ALSA I get all sorts of error notifications, when I switch it runs perfect.  Also turning off the screen saver option of the player eliminates the other error.

---

### Post by locky28 on 2007-12-14
Much love binary_bob, got this sorted on only day 2 or trying to fix it thanks to you! :)

---

### Post by Dive4Life on 2007-12-16
Thanks a whole bunch for the post.  Works perfectly.  I didn't realize at first that the x64 architecture needed special repositories.  I've been trying to get this to work off of the x32 posts to no avail.  Thanks again.

---

### Post by tobydeemer on 2008-01-04
Hi all-

I was excited to find this post to get DVDs working. 

I followed the steps outlined by Binary_Bob, and it worked to get DVDs to load up and display the menu. However, at the menu screen when I click play, Totem hangs and won't actually begin playback. gxine and Xine Movie Player are also in my applications list, and both of them do the same thing (I assume because they're using the same engine source?)

I have libdvdcss2, libdvdread, libdvdnav, etc. all installed and current. In theory, and looking at Synaptic Package Manager to see what's installed, it should be working fine.

I'm stuck... any help would be greatly appreciated.

---

### Post by cawel on 2008-01-20
I followed binary_bob's solution. Just wanted to add that I needed to reboot in order for the DVD playback to work. Wasted a few hours on the problem... but now it works fine!

---

### Post by villindesign on 2008-03-08
I tried the solutions posted above, but I still can not get a commercial DVD to play. This is gxine error codes:
```
britt@britt-R61:~$ gxine
lirc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect to the socket?
libdvdnav: Using dvdnav version 1.1.10 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdnav: DVD Title: Hard_Candy
libdvdnav: DVD Serial Number: 3508a746
libdvdnav: DVD Title (Alternative): Hard_Candy
libdvdnav: Unable to find map file '/home/britt/.dvdnav/Hard_Candy.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000033b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000003bd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00029aff
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0027af48
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_0.VOB (0x0027af48)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0027af81
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x0027af81)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00345dd6
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_0.VOB (0x00345dd6)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00345e0f
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_1.VOB (0x00345e0f)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x0036aa3f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0036aa78
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x0036aa78)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0039a2b8
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_0.VOB (0x0039a2b8)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0039a2f1
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_1.VOB (0x0039a2f1)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003a3a57
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003a3a90
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_06_1.VOB (0x003a3a90)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x003bb1a7
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_07_0.VOB (0x003bb1a7)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003bb1e0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_07_1.VOB (0x003bb1e0)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x003bb5c8
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_08_0.VOB (0x003bb5c8)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003bb601
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_08_1.VOB (0x003bb601)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x003bd348
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_09_0.VOB (0x003bd348)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x003bd381
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_09_1.VOB (0x003bd381)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x003bd906
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_10_0.VOB (0x003bd906)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x003bd93f
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_10_1.VOB (0x003bd93f)!!
libdvdread: Elapsed time 0
libdvdread: Found 10 VTS's
libdvdread: Elapsed time 2
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1522 ***
*** for info_length % sizeof(uint32_t) == 0 ***

libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed
xine-lib: error: Read error from::  Encrypted or faulty DVD

```Thanks for any help.

---

### Post by MasterSushi on 2008-03-14
> **binary_bob said:**
> This is for those of you having problems playing commercial DVD's with 64bit Gutsy.

Binary Bob - Thank you very much for this solution. It worked flawlessly. Thanks!!

---

### Post by AkLogCabin on 2008-03-30
> **binary_bob said:**
> This is for those of you having problems playing commercial DVD's with 64bit Gutsy.
Medibuntu should solve your problems.
1) Add the medibuntu repository for Ubuntu 7.10 "Gutsy Gibbon"

 sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

2)Add the GPG Key.

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

3) To play Encrypted DVD's.

 sudo apt-get install libdvdcss2 

(i think this package gets installed by one of the media players anyway, but it's not a problem)

4)To play Non-Native Media Formats.

 sudo apt-get install w64codecs

5)The next part is installing the appropriate players.
6)System>Amin>Synaptic Package Manager.
7)Search.... xine
8)Install the following packages.

gxine
totem-xine
xine-ui

These three packages should install the rest of the requirements for playing various media.

From a clean install, doing the above, i have the following packages installed (search...xine)
gxine
libdmx1
libxine1
libxine1-ffmpeg
libxinerama1
totem
totem-xine
xine-ui

Now i can play Encrypted DVD's.
(I did a quick test with Lord of the Rings)
I hope this makes sense and is useful to you.

Bob ur the man.....worked like a charm. Thanks from a week-old noob!!!

---

### Post by moizd on 2008-04-13
> **zorkerz said:**
> thanks for the well written post binary_bob. Im not at my computer right now so  I cannot be absolutely sure but I have done all the steps you wrote and a similarly instructed on the three relevant community docs pages.
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) -> for ubuntu-restrictd-extras
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) -> for the various players
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) -> for medibuntu, libdvdcss2

at this point im hoping for a stupid mistake on my part

I could have sworn I had followed the same entire set of instructions myself to no avail and I was beginning to despair.I noticed that binary_bob listed one player no one else had ( or at least hadn't noticed earlier ): gxine. The minute i installed it, everything snapped into place for me. I can now watch encrpted dvds using totem-xine.

This is with 64-bit  Gutsy.

---

