---
title: "DVD playback is jerky and choppy"
date: 2008-12-02
forum: x86 64-bit Users
---

### Post by davidstoll on 2008-12-02
When I try to play a DVD with the internal player, the video is quite choppy or jerky.  However, if I play the DVD with VLC, mplayer or xine, it plays fine.

The internal player does play other formats fine (i.e. avi, mkv, etc).

I have an Nvidia 8500 and a quad core 2.6GHz cpu with 4Gigs of ram with a Gigabyte mobo.

I would appreciate any help that is offered.

Thank you

---

### Post by nikgare on 2008-12-02
I would recommend removing totem-gtreamer and installing totem-xine.  This installs xine as the backend for the normal movie player - and I've always had more luck with this.

---

### Post by davidstoll on 2008-12-03
> **nikgare said:**
> I would recommend removing totem-gtreamer and installing totem-xine.  This installs xine as the backend for the normal movie player - and I've always had more luck with this.

Is installing totem-xine automatically set it up as the backend player or is there some process for setting it up?

Can I just use mplayer or vlc?  I'm a little more familiar with them.

---

### Post by philinux on 2008-12-03
I only use vlc for dvd's. It handles the menu's much better.

---

### Post by davidstoll on 2008-12-03
> **philinux said:**
> I only use vlc for dvd's. It handles the menu's much better.

The internal player (mythdvd?) skips a bunch of the crap at the beginning of the dvd's, which is nice, but would/could the others do that if used as the default myth player?

Anybody know what the command line flags are (for vlc and/or mplayer and/or xine) to do the skipping?

Thanks!

---

### Post by coskierken on 2008-12-03
Something to check is to turn off compiz.  It does not work well with DVD play.  Another thing is to download Quickstart.  

[http://quickstart.phpbb.net/viewtopic.php?f=8&t=11](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11)

Use the install common apps (pick your choices) and then install the codecs.  All should be well.

---

### Post by davidstoll on 2008-12-03
> **coskierken said:**
> Something to check is to turn off compiz.  It does not work well with DVD play.  Another thing is to download Quickstart.  

[http://quickstart.phpbb.net/viewtopic.php?f=8&t=11](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11)

Use the install common apps (pick your choices) and then install the codecs.  All should be well.

I don't think compiz is installed with MythBuntu by default, so I don't think have it...?

Installing an external app doesn't really fix the problem.  The internal DVD player in Mythtv should be able to play back a DVD smoothly.  By the way, I did try quickstart, but it didn't help.  In fact, now mplayer isn't working properly.  :(  I'm fairly new to linux, so I'm going to have a tough  time getting it back to where it was I think. 

There is some setting in Myth or maybe a command line operator I need to add (or remove) from the launch process of the internal Myth DVD player....but I'm just speculating.

---

### Post by coskierken on 2008-12-04
Check your settings anyway for your desktop

right click anywhere on the screen and from the menu "adjust desktop background".  When there, there maybe a tab for visual effects.  If it is not set to none, it will effect DVD playback.  

Ubuntu does not load compiz-manager initially, but does load some of the programs needed for this.  It caused me headaches when I first started in Ubuntu.  Just my 2 cents worth.  

Oh, what type of machine are you loading it on?

---

### Post by davidstoll on 2008-12-04
> **coskierken said:**
> Check your settings anyway for your desktop

right click anywhere on the screen and from the menu "adjust desktop background".  When there, there maybe a tab for visual effects.  If it is not set to none, it will effect DVD playback.  

Ubuntu does not load compiz-manager initially, but does load some of the programs needed for this.  It caused me headaches when I first started in Ubuntu.  Just my 2 cents worth.  

Oh, what type of machine are you loading it on?

I have attached a screen shot of my desktop settings.  Remember, I'm using Mythbuntu, not a full Ubuntu.  So, it's quite stripped down.

My machine is a quad core 2.6 MHz with 4GB of ram and a 8500 Nvidia video card.  My DVD player is a 16x and my hard drive is sata 3.0MB/s.

Again, it plays DVD's just fine with external players, but not with the internal Myth player.  So, I think it's a setting inside Myth.  For numerous reasons, I want to keep the internal player as the player within Myth rather than using an external player.

---

### Post by coskierken on 2008-12-04
ok, gotcha!  Fast system and hardware more than enough!  Geez, I wish I had it!  It looks like a version of Xubuntu.  I just loaded it on an ol P4 due to effects screwing it up.  It does not load any effect either.  I am in the process of loading every version on the old machine to test them all out.  Sorry I could not help.

---

### Post by philinux on 2008-12-04
In order to play/rip encrypted DVDs (most commercial DVDs), you need to install libdvdcss before installing mythDVD. 

Maybe there's some help here.
[http://www.mythtv.org/wiki/index.php/MythDVD](http://www.mythtv.org/wiki/index.php/MythDVD)

---

### Post by davidstoll on 2008-12-13
> **philinux said:**
> In order to play/rip encrypted DVDs (most commercial DVDs), you need to install libdvdcss before installing mythDVD. 

Maybe there's some help here.
[http://www.mythtv.org/wiki/index.php/MythDVD](http://www.mythtv.org/wiki/index.php/MythDVD)


libdvdcss is already installed

---

### Post by synthetic_fenix on 2008-12-18
I am having the same exact issue with my system my setup is a dual core 1.9Ghz AMD with 1Gb of ram and an 8600GT, DVD playback has worked fine in the past I believe in version 7.10 and also in 8.04 but I am running the latest version and I am no seeing this problem.

---

### Post by chestnut1969 on 2008-12-19
Same issue here with the choppy DVD playback using the internal DVD player in Mythbuntu 8.10. My HTPC is by no means underpowered for the task. 

I resorted to changing to Xine for smooth DVD playback, replacing the command for the internal player with

xine -pfhq -D --no-splash -s DVD


taken from
[http://www.mythtv.org/wiki/index.php/Configuring_Xine](http://www.mythtv.org/wiki/index.php/Configuring_Xine)

Cheers

---

### Post by davidstoll on 2008-12-20
> **chestnut1969 said:**
> Same issue here with the choppy DVD playback using the internal DVD player in Mythbuntu 8.10. My HTPC is by no means underpowered for the task. 

I resorted to changing to Xine for smooth DVD playback, replacing the command for the internal player with

xine -pfhq -D --no-splash -s DVD


taken from
[http://www.mythtv.org/wiki/index.php/Configuring_Xine](http://www.mythtv.org/wiki/index.php/Configuring_Xine)

Cheers

Can the same thing be done for live and recorded TV?

---

### Post by teetniin on 2009-01-25
No it is not possible to change livetv player!
I have same problem, what i noticed, when i enable automatic removable media detection and usage, player is very choppy!
When i disabled automatic plugin usage it gets little better, but it skips still.
I hope there is solution to this problem!
Internal player has some really good features(menu skip, VFD support).
BTW i had same problem with gentoo installation(which had evilwm as window manager).

---

### Post by moodog on 2009-02-01
Try changing the deinterlacer used. It was successful for some other guys in a thread here:

[http://www.gossamer-threads.com/lists/mythtv/users/335290](http://www.gossamer-threads.com/lists/mythtv/users/335290)

might work for you too. 

see here for information on recording profiles, where you set the deinterlacer

[http://www.mythtv.org/wiki/Playback_profiles](http://www.mythtv.org/wiki/Playback_profiles)

---

### Post by marcelkoopman on 2009-02-02
It this not a question of using the right codecs? I mean using codecs that do hardware decompression? I know of medibuntu repos, which has w64codecs, but i'm not sure these are hardware codecs.

I would think the used video player is not important but the backend codecs are. And in that case it would be wise to use the hardware enables ones. I've heard of these codecs for windows, but i'm not sure if Linux also has these.

---

### Post by korgman on 2009-07-16
I'm having choppy playback here too.  It started after an upgrade to mythbuntu 9.04.  Worked fine in 8.x.  DVD is very choppy, xorg grabs about 90% CPU, using the internal player.  The weird thing is, it works fine with ISO images I've ripped to drive.

---

### Post by davidstoll on 2009-07-16
Nobody has been able to solve this issue.

My solution was to install XBMC (or Boxee) and use that to playback DVD's.  After installation, you can just make a custom entry in one the the menus in mythbuntu (edit the xml files).

It's not ideal, but it works REALLY well.  Xbox Media Center and Boxee (based on XBMC) are well written and are smooooooooooth.

---

### Post by korgman on 2009-07-16
I wonder what changed.  I was using a simple profile I created that used Xvideo and ffmpeg no matter what and I had Bob2x set.

I switched to HighQuality and set the deinterlacer to GreedyHighmotion 2x with Yadif as a backup and its working fine...for now.  This is weird.

---

### Post by korgman on 2009-07-16
Nope, I take that back.  It started to get choppy again.  Xorg is up well over 80% when watching disks.

---

### Post by korgman on 2009-07-28
I switched to xine and though the DVDs play fine now the video quality is terrible.  I'm calling "xine -pfhq -D --no-splash dvd:/" .  It plays, but it looks, soft and fuzzy.  I was watching a home movie on DVD so its really noticeable.  Regular movies at 24fps and film grain come across fine, really cant tell any problem there.  But, this same home movie is also ripped to the drive and it looks totally different (and better) when when you play it from Watch Videos.

---

### Post by korgman on 2009-09-08
I just did a fresh reinstall of Mythbuntu 9.04.  Its better, much better, but it is still choppy.  Using a VDPAU profile now and Bob2x.  I'll play with it later tonight.

---

