---
title: "Problems with OSS in 64 bit"
date: 2007-06-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by fakie_flip on 2007-06-10
Has anyone had luck with aoss, jackd, joss, artsd and artsdsp, or any other method to get sound working with OSS apps in 64 bit Ubuntu. I want to use Skype or Teamspeak while playing games in Ubuntu 64, but I can't with many games because they are made with OSS, and nothing that I mentioned is working for me however it is working for my friends that are using 32 bit Ubuntu.

---

### Post by Cappy on 2007-06-11
Yes, my sound/mic work in multiple programs at once with 64-bit, 32-bit, and WINE programs.

I now use an Audigy 4 (non-pro) and now everything mixes (only one program at a time would work when I used a USB headset). If you got a better (non X-Fi) Creative sound card your problems with sound sharing would go away. Unfortunately, there may not be any way to make a nvidia sound card like yours work.

---

### Post by fakie_flip on 2007-06-11
How do you know I have a nvidia sound card?

---

### Post by Kilz on 2007-06-11
> **fakie_flip said:**
> How do you know I have a nvidia sound card?

You do know you can click on a users name in the top of a post and get all there past posts, right? A quick look back [brings up this one]("http://ubuntuforums.org/showpost.php?p=2812538&postcount=8"). Thats probably how.

---

### Post by fakie_flip on 2007-06-11
> **Cappy said:**
> Unfortunately, there may not be any way to make a nvidia sound card like yours work.

It is the software that is not capable, not the hardware. I can have Skype or Teamspeak working with games in windows, but not Linux. I'd prefer to run all my games in Linux except for the ones that do not run native. I have to reinstall windows again for games. It crashed many times from the Nvidia nTune. First I lost sound. Reinstalling the driver didn't help. Then it corrupted badly, so it won't boot at all, but when I use coolbits to OC my gpu under Linux, its working fine and stable.

---

### Post by Kilz on 2007-06-11
> **fakie_flip said:**
> It is the software that is not capable, not the hardware. I can have Skype or Teamspeak working with games in windows, but not Linux. I'd prefer to run all my games in Linux except for the ones that do not run native. I have to reinstall windows again for games. It crashed many times from the Nvidia nTune. First I lost sound. Reinstalling the driver didn't help. Then it corrupted badly, so it won't boot at all, but when I use coolbits to OC my gpu under Linux, its working fine and stable.

I think you both agree. But without the software to make the sound card work right , a replacement with a creative sound blaster might be a easier solution. Its just like the network port on my brothers gateway. I played and played (weeks)trying to get it to work in Linux. It worked fine under windows. But $9 bucks and a dlink card solved the problem in minutes.

---

### Post by fakie_flip on 2007-06-11
How much would a sound blaster cost? I have High Definition audio with 7 sound jacks with a sound card built on my motherboard. Are you sure the sound card is the problem? Could you explain why the sound card is the problem? I would like to read online about it.

---

### Post by Cappy on 2007-06-11
The problem would be that your sound card is either not supported "out of the box" or that it doesn't have hardware mixing capability.
I found two links but both are more for NForce 2's:
[http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix#Hardware_Configurations_-_.7E.2F.asoundrc_Files](http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix#Hardware_Configurations_-_.7E.2F.asoundrc_Files)
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Nvidia&card=.&chip=nForce&module=intel8x0](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Nvidia&card=.&chip=nForce&module=intel8x0)

I don't know anything about trying to configure the sound device since Ubuntu spoils me.

---

