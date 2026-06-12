---
title: "No audio driver selection available in wine"
date: 2011-10-18
forum: Wine
---

### Post by smitty5189 on 2011-10-18
OK so bear with me I'm still pretty noobish with wine.  I have been testing out some of my windows software thru wine as I run Ubuntu 11.10 exclusively on my laptop.  I just installed Rosetta stone v3 with no problems and got the language packs installed.

My issue is this: when I start up rosetta stone it wouldn't recognize my USB microphone.  So after some investigating I found this very issue solved.  However when I go into my audio settings in winecfg the only options available are directaudio (no driver or device selection) how can I get my USB mic to be recognized if there is nowhere to select it as a device?  And sorry in advance if this question has already been asked but if so I haven't been able to find it.

Smitty

---

### Post by smitty5189 on 2011-10-19
someone, anyone... i cant be the only one to have this issue.

---

### Post by Tweak42 on 2011-10-19
What version of wine are you using?  There was a major sound update in 1.3.30 

See the sticky post at the top of the wine forum.

---

### Post by smitty5189 on 2011-10-19
I believe it is 1.3.30 apt tells me that I have latest version installed

---

### Post by Tweak42 on 2011-10-19
Wine version can be found in winecfg 'About' tab, or entering "wine --version" in a terminal.

The reason I asked is when you describe the winecfg audio tab as "only options available are directaudio (no driver or device selection)" it sounds like older wine versions, not 1.3.30.

Attached is a screenshot wine 1.3.30 audio tab.  If your USB mic is setup in ubuntu correctly it should show up in the input device selection menu.  I don't have a usb mic to actually verify if thats the case.

Other things you might try is installing to a clean WINEPREFIX as using multiple programs in the same prefix and upgrading from prefixes created in older wine versions sometimes makes thing wonky.

---

### Post by smitty5189 on 2011-10-19
My mistake my wine is version 1.3.28 here is what my audio tab looks like.  I'll try a new prefix and see if that helps...


UPDATE:  tried using a clean prefix made no difference

---

### Post by Tweak42 on 2011-10-19
> **smitty5189 said:**
> My mistake my wine is version 1.3.28 here is what my audio tab looks like.  I'll try a new prefix and see if that helps...


UPDATE:  tried using a clean prefix made no difference

Hmm.. well I'm kinda stumped to why none of the sound subsystems are showing up.  [Wine appdb]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1867") reports varying success with old wine versions.  I would try 1.3.30 and then try older release if that doesn't work.

---

### Post by smitty5189 on 2011-10-19
compiling + installing 1.3.30 now *crosses fingers*

---

### Post by ubupirate on 2011-10-20
Seems 1.3.30 is now using winealsa.drv for audio. Haven't tested current version yet with any games to see how well it works with other audio apps running (Audacious).

1.3.30 finally hit repos for 10.04, so now don't have to compile it anymore. :P

---

### Post by smitty5189 on 2011-10-20
ok so after 2 hours of building from source finally got wine 1.3.30 installed, and my usb and integrated microphones are both showing in the audio tab.  Rosetta stone still cannot see either one though... tired as hell so leaving it to deal with in the AM

---

### Post by PowerKiKi on 2011-11-09
Hey, I had similar issue, so, for the record, here is my story:

I installed wine and Rosetta Stone 3.3.5 on Ubuntu 11.04 and ran a quick test for the mic, everything was working. So i fresh-installed Ubuntu 11.10 and installed wine 1.3.28 and Rosetta Stone 3.3.5. Mic didn't work. 

After reading your comments, I tried to update to latest wine version, but I did via ppa instead of compiling (as [described here]("http://www.winehq.org/download/ubuntu")). So I got wine 1.3.32 and it still didn't work.

As it used to work with previous Ubuntu release, I gave it a try and installed wine 1.2.3. And it worked ! :-)

So long story short, all I did was:

```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get upgrade # got me wine 1.3.32, but not working
rm -rf ~/.wine # wipe out entire wine directory before downgrading
sudo apt-get install wine1.2 # done :)
```

I must mention though that my mic is a standard "jack" plug, not USB...

---

