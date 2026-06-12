---
title: "Still no sound: Counter-Strike Source"
date: 2007-07-03
forum: Wine
---

### Post by Insomn1a on 2007-07-03
ok, im trying to get Counter-Strike: Source to work.


i've gone over all of the forum discussions that i could find about this problem, i've gone through 10 pages of google.


i've tried ALSA, i've tried OSS, neither one of them seem to want to work, here is what im getting from the terminal.

```
garrett@Insomn1a:~$ winecf
bash: winecf: command not found
garrett@Insomn1a:~$ winecfg
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
```

my question is,

is there something that i have to install, such as libjack.so, or DSCapture, or something like this?????

PS: would the audio drivers for my headset be a problem with it? I hear audio whenever i login and everything, it just seems like wine is whats giving me trouble.

---

### Post by Insomn1a on 2007-07-04
> **Insomn1a said:**
> ok, im trying to get Counter-Strike: Source to work.


i've gone over all of the forum discussions that i could find about this problem, i've gone through 10 pages of google.


i've tried ALSA, i've tried OSS, neither one of them seem to want to work, here is what im getting from the terminal.

```
garrett@Insomn1a:~$ winecf
bash: winecf: command not found
garrett@Insomn1a:~$ winecfg
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
```

my question is,

is there something that i have to install, such as libjack.so, or DSCapture, or something like this?????

PS: would the audio drivers for my headset be a problem with it? I hear audio whenever i login and everything, it just seems like wine is whats giving me trouble.

ok, im using USB audio, i read in a post at linux-gamers.net for someone to set teamspeak to access /dev/dsp1, when i did that i got my teamspeak program to start working correctly, now is there a way for me to set OSS or ALSA to default to /dev/dsp1 in wine???

im using ubuntu dapper.

---

### Post by Insomn1a on 2007-07-06
Bump

---

### Post by xdarkxanarchyx on 2007-07-08
Did you fix your sound problem? When I try to launch/install Star Wars: Empire at War it gives me the same error.

```
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
```

---

### Post by Insomn1a on 2007-08-06
nope, still haven't, unfortunately ill have to use windows until i am able to resolve this problem, someone help me :confused:

---

### Post by Sindwiller on 2007-08-07
> **Insomn1a said:**
> nope, still haven't, unfortunately ill have to use windows until i am able to resolve this problem, someone help me :confused:

*sigh*

```
sudo mv /dev/dsp /dev/dsp2
sudo ln -s /dev/dsp1 /dev/dsp
```

Think geek (you won't be able to use TS and your Wine prog of your choice at the same time though)

---

### Post by frodon on 2007-08-07
This is clearly stated in tyhe appDB, don't use alsa with counter strike source, the easiest is to disable alsa in winecfg.
So choose OSS, then close all your apps that use the sound card or run a "killall esd"

Then go here for CS:S wine problems :
[http://appdb.winehq.org/appview.php?iVersionId=3731](http://appdb.winehq.org/appview.php?iVersionId=3731)

---

### Post by Sindwiller on 2007-08-07
> This is clearly stated in tyhe appDB, don't use alsa without counter strike source, the easiest is to disable alsa in winecfg.
So choose OSS, then close all your apps that use the sound card or run a "killall esd"

He already said that he also used OSS and it didn't work (because it accesses /dev/dsp instead of /dev/dsp1)

---

### Post by FilmAficionado on 2007-11-10
I'm not sure if you're still having this problem, so I hate to reply to this thread so long after but I may have a solution:

I followed the second post from [http://www.cedega.com/forum/viewtopic.php?t=8863&sid=a89901292d3f49c510a65f74997133ee](http://www.cedega.com/forum/viewtopic.php?t=8863&sid=a89901292d3f49c510a65f74997133ee)

Solution is that STEAM basically takes the sound card and doesn't let go of it, so when you startup the actual Counter-Strike game, the soundcard is busy with STEAM.

So play an MP3 in Amorak or your mp3 player of choice so you can grab control of the soundcard. Start STEAM. Click on your game, Counter-Strike: Source, and as the pop-up comes that says PREPARING TO START or whatever, stop your mp3 playback and bam. Counter-Strike Source starts, you have your sound. Perfect.

But can someone fix this bug now? I don't know to file a bug-report (or where). Any advice? Comments?

Thanks to the guy who posted this on the CEDEGA site, even though I'm getting this problem with CS:S via WINE.

!!

---

### Post by Insomn1a on 2007-11-10
what the problem is is that it is using the standard soundcard that is available on the motherboard,


I'm using Icemat's with a USB sound card, what i need to happen is for the sound to redirect to the USB soundcard.

---

