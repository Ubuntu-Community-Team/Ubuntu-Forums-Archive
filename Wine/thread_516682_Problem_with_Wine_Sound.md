---
title: "Problem with Wine Sound"
date: 2007-08-03
forum: Wine
---

### Post by cjules86 on 2007-08-03
Hello,

I posted in the WoW Howto but for lack of response, and in an effort to help others who have the same problem and are using the search feature of these boards, I decided to make a separate post.

I play WoW and for the longest time I have not been able to get sound in game.  At first I thought it was a WoW problem but now I'm thinking it is probably a Wine problem.  Before I get pointed to WoW howto, I tried all those solutions for sound.

I dont really have any other apps that I run in wine to test if this is a wine problem or a WoW problem but the following error which I get when I click the audio tab in winecfg is entered into my terminal:

```
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:mixer:ALSA_MixerInit No master control found, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found, disabling mixer

```

I am using a Sound Blaster Audigy SE (CA0106).  Is this a problem where Wine is not detecting the sound card or something bigger?

Also, I'm using Ubuntu 7.04 on AMD64.  Any help is _greatly_ appreciated!

---

### Post by cogadh on 2007-08-03
Nope, I have the same card and the same errors, which I just ignore, since sound works fine for me. What are your sound settings in winecfg set to?

---

### Post by cjules86 on 2007-08-03
ATM I have it on ALSA drivers but have tried it on OSS drivers as well.  And I believe both with Driver emulation ticked as well... Gonna go back and recheck though :)

EDIT: Just retried all the drivers listed with and without driver emulation ticked.

---

### Post by cogadh on 2007-08-03
I just realized, I should have been more specific, I don't play WoW, but sound works for me in all other games I use with Wine. Sorry if you though I meant sound in WoW worked.

However, the settings I use in Wine that seem to work well for nearly everthing are the ALSA driver, full hardware accelleration, 48000 sample rate, 16 bits per sample and driver emulation on.

---

### Post by cjules86 on 2007-08-03
I'll try these settings real quick.


EDIT:
Nope no go for me :(
Any other thoughts?

---

### Post by ev5unleash1 on 2007-08-03
Problems with programs like WINE are really not handled here you should go to winehq.com and submit the bug or ask for help.

---

### Post by cogadh on 2007-08-03
> **ev5unleash1 said:**
> Problems with programs like WINE are really not handled here you should go to winehq.com and submit the bug or ask for help.
Huh!? I spend most of my time on these forums helping with Wine game problems.  This is the "Gaming & Leisure" forum after all.

Anyway, back to the subject at hand. You mentioned you had used several how to's  for the game, just to confirm, have you already edited the Config.wtf file with this:
```
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
```

---

### Post by atomkarinca on 2007-08-03
> I have exaclty the same problem. I have fixed enabling the "Sound in background" option in Sound Option of WOW.

or you can open wine-config, hit alt+f2 or type in the terminal
```
winecfg
```
and in the audio tab deselect alsa and select oss.

---

### Post by cjules86 on 2007-08-03
Cogadh -- Yes I've added those lines

And i've tried all the drivers, none of them worked.

---

### Post by cogadh on 2007-08-03
Ack! I forgot, OSS is the recommended sound system for WoW. ](*,)

Did you try the "sound in background" option that atomicarinka suggested?

---

### Post by cjules86 on 2007-08-03
Yes I have sound in background enabled and:

> And i've tried all the drivers, none of them worked.

---

### Post by cogadh on 2007-08-03
Yes, I understand you have already tried several combinations, but if you are going to get it to work, we need to first make sure the game and Wine are configured in such a way that is already known to work (for other people), then we can look at what needs to be tweaked or changed on your setup to fix the problem you are having. 

One question I have is could this be symptom of having a 64 bit system? I know in the past Wine's 64 bit support was not the best, but I don't know if that has improved much (still in 32 bit world here). Perhaps one of the other 64 bitters out there could answer that.
Also, what version of Wine are you using?

---

### Post by cjules86 on 2007-08-03
Ok, I set the audio settings to exactly as they are in the howto.

I'm using version 0.9.42.  I installed it through the synaptic package manager and not through the Applications -> Add/Remove Programs method... Not sure if that makes a difference.

---

### Post by cogadh on 2007-08-03
Okay, this one is a long shot, but it has corrected buggy sound for me before. 
[LIST=1]
[*]In a terminal, run "regedit"
[*]Browse through the file tree to  HKEY_CURRENT_USER\Software\Wine
[*]Create a new key and label it "Alsa Driver"
[*]In the new key, create a new string and label it "UseDirectHW"
[*]Change the value of the string to "y"
[*]Exit out of regedit
[*]Set your sound system to ALSA again in winecfg
[*]Try the game
[/LIST] 
See the attached screenshot if that didn't make sense.

---

### Post by cjules86 on 2007-08-03
No difference... Later tonight I'm gonna try taking the card out and try working without it.  Will post back the results.

Well no difference booting w/o the SB Card (didn't really think it would make one anyways).  I've got no more ideas :(

---

### Post by sysctl on 2007-08-04
I am having a similar problem. I have two sound cards: Intel HDA (on-board) and Audigy4. Some applications under Wine tend to pick the first available sound card with WINE. For example, I have FL Studio playing sound on Audigy4 (however it slows down the whole application), but Civilization IV will play only on on-board sound card and I can't seem to find a way to force all WINE applications to use Audigy4.

Also, the following,
```

err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture

```
seems to be due to the fact that Audigy4 does not have this control item in **/var/lib/alsa/asound.state**, as it has items named like 'PCM Front Playback Volume', 'PCM Surround Playback Volume', etc, but Intel has. So it makes the whole situation a lot more confusing.

---

### Post by cjules86 on 2007-08-04
Was looking through my Sound Manager (right click volume control -> open volume control) and it says  I have three devices:

CA0106 (Alsa Mixer)
NVidia CK804 (Alsa Mixer)
mixer00 (OSS Mixer)

Could this have anything to do with it.  Similar to what the last poster was saying where it is just sending it to a diff sound card?  Although I plugged my speakers into the onboard speaker jack and got no sound for WoW either.

---

### Post by cogadh on 2007-08-04
Both of you disable the onboard sound in your BIOS. Having the extra sound card will definitely confuse the issue. The OSS mixer entry is normal, however.

---

### Post by cjules86 on 2007-08-04
Did a complete fresh reinstall of World of Warcraft and the problem is no longer... So my only guess as to the problem was it had to be something in the WoW directory that I was using.

So happy I can hear sounds again!

Thanks for your assistance Cogadh.  It's nice to see such helpful people on these forums.

---

### Post by cogadh on 2007-08-04
Not sure how much help I really was, but I'm glad you got it working. Happy WoW-ing! :)

---

### Post by cjules86 on 2007-08-04
Grr -- so angry right now haha

It was working all day then out of nowhere the screen went black.  So I restarted Gnome and bam! no sound again :(

Dont feel like troubleshooting it tonight though... maybe tomorrow.

---

### Post by cjules86 on 2007-08-06
Well, after trying all day with reinstalling and all kinds of tips I've gotten from people in the winehq chat, im still at square one -- no sound in WoW.  It worked for a few hours after the first reinstallation as I said earlier and then after a restart it no longer works.  Any help is appreciated.

---

### Post by emji on 2007-08-09
I'm having a simular sound issue but with all apps under Wine 9.42 and earlier versions on edgy with an Audigy 2 card.  It's very hit and miss, but I could almost always get the sound to work after doing a kill -9 -1 and restarting the Wine app.  Something is obviously running in the background that's conflicting but I'm not sure what it is.

At this point in time, killing and restarting no longer works and I'm without sound in Wine.

---

