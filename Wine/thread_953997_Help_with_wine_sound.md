---
title: "Help with wine sound"
date: 2008-10-20
forum: Wine
---

### Post by madtyper on 2008-10-20
I've been trying without luck to get sound in wine so I can run games. DirecXs dxdiag.exe shows "No sound card was found."

wincfg shows in the terminal "ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave"

I tried installing the windows drivers using wine, because I saw that worked on another post.  However, no matter what mode I set wine to -- XP, Vista, 98 ... -- my driver's setup gives "Does not support this operating system : WNT_[and some number -- this time it was _5.1P)"

I am running 64-bit wine on a 64 bit processor, I tried the windows setup for both the 64 and 32 bit driver. 

I can run new games,I've tested Spore on wine-- the sound just doesn't work. 

(I also played with whatever audio options through trial and error in winecfg's "audio" tab. No luck ...)

Does anyone have any ideas? Is it a compatibility issue with Hardy Heron? :popcorn:

---

### Post by billybag on 2008-10-20
Hey. I am having an issue with sound as well. The sound worked the very first time i used a game in wine, which was also the first time i ran wine. But then i close the game and the sound has never worked since. 

I tried various threads and their methods on how to fix it and i have had no luck :(

---

### Post by jyaan on 2008-10-20
my sound didnt work properly in wine unless i set it for OSS audio output becasue of pulseaudio, but what youve posted doesnt look familiar to me anyways. worth a shot at least.

---

### Post by billybag on 2008-10-20
[http://appdb.winehq.org/commentview.php?iAppId=5936&iVersionId=9432&iThreadId=29466](http://appdb.winehq.org/commentview.php?iAppId=5936&iVersionId=9432&iThreadId=29466)


unfortunately the latter worked for me... at least i get sound in the game now though... just no sound from anything else.

---

### Post by jyaan on 2008-10-20
well, i used the pulseaudio fixes. i havent had any problems with sound since, aside from the fact that some need to be set to OSS output.

it was this page taht i used
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by madtyper on 2008-10-21
> **jyaan said:**
> well, i used the pulseaudio fixes. i havent had any problems with sound since, aside from the fact that some need to be set to OSS output.

it was this page taht i used
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Thanks, J, your fix is great I've made some progress. Though, the audio does stutter now. Do you have any tips on how to adjust that file **~/.pulse/daemon.conf** listed in the guide? I tried increasing ten decreasing both, neither worked-- the sound is still unbearable. I also tried the other two drivers in winecfg, but it only works with ALSA.

---

### Post by david_kt on 2008-10-21
> **madtyper said:**
> Thanks, J, your fix is great I've made some progress. Though, the audio does stutter now. Do you have any tips on how to adjust that file **~/.pulse/daemon.conf** listed in the guide? I tried increasing ten decreasing both, neither worked-- the sound is still unbearable. I also tried the other two drivers in winecfg, but it only works with ALSA.

Go to the menu:

System > Administration > System Monitor

And on the "processes" tab, look for pulseaudio, right click on it, and choose "kill process".

After that, restart your game, or whatever program you want to run.

DK

---

### Post by madtyper on 2008-10-22
> **david_kt said:**
> Go to the menu:

System > Administration > System Monitor

And on the "processes" tab, look for pulseaudio, right click on it, and choose "kill process".

After that, restart your game, or whatever program you want to run.

DK

Thanks, Dave. I don't know how or why, but the final piece of the puzzle solved. 

Thx

---

### Post by 2hot6ft2 on 2008-12-08
This should fix you all up [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

Along with this from the same thread [http://ubuntuforums.org/showpost.php?p=5001395&postcount=112](http://ubuntuforums.org/showpost.php?p=5001395&postcount=112)

---

