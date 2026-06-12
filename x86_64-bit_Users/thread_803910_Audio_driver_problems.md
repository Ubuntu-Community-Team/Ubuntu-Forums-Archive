---
title: "Audio driver problems"
date: 2008-05-22
forum: x86 64-bit Users
---

### Post by Tsukasah on 2008-05-22
Im assuming this is where I'd post my audio driver problem. I'm on 64 bit Gutsy. My driver can't seem to make up its mind. I want to get audio to come out of TuxGuitar, Mozilla, basically anything, it works sometimes, but not always. The only time the audio seems to work when it doesn't fully work is on Rhythm Box and Totem. Usually after a restart the audio works, sometimes it takes two restarts or more. 

Before I upgraded to 64 bit I used onboard audio, that always worked. This is also before I used TuxGuitar, and it worked fine in Mozilla. After I upgraded I still used the onboard audio drive and it worked for awhile. I downloaded TuxGuitar and it said it couldn't find the Midi port and such, messed with every single option still gave the same answer. Audacity wouldnt work with any option I gave it. I could edit sound, but couldnt listen to it in Audacity. 

Then one day I found a nice HD audio card of my dads that's about 2 years old, maybe a bit less. It's a Realtek Soudlbaster Audigy 2. I only use the regular green input but there really is a bit of a difference in sound. 

In the Sound Prefs, the sound playback is Multichannel Playback(the only one that works when I click test sound), music and movies is ADC Capture/Standard PCM playback, along with everything in the audio conferencing category. 

Default Mixer Tracks, I believe is the problem I had in TuxGuitar before I switched to the Audigy. I have a choice between HDA NVidia(ALSA Mixer) Audigy 2[SB0350b] Alsa Mixer. And then there's Realtek ALC883 (OSS Mixer). 

I have the Audigy 2 selected, and the sound preferences are the same when the audio works and when it doesn't work. 

Also when I went to Configure WINE, I clicked on audio and it told me it couldn't find an audio driver selected in the registry so it picked one for me. Something along those lines, my choices are ALSA and OSS drivers. I can check both. But when I click on Test Sound, there is no sound. 

And wow that was a good 10 minutes of my time typing all that. Maybe I went into too much detail but I'm like that. Talk too much, goes into exact detail. Both a blessing and a curse. Bleaugh... Anyway I hope if anyone has the heart to help me fix this it wont take more than 10 minutes of your time! ^.^ Any help is appreciated, and many thanks will be given!

---

