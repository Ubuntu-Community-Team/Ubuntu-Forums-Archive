---
title: "NForce 250 chipset + AMD 64 = 1 sound channel"
date: 2005-07-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Turmoyl on 2005-07-16
This is just an FYI that I hope may save some of you from the hours it took me to figure this out.

Despite what the /proc system shows and despite both /dev/dsp and /dev/adsp beng present the simple fact is that this chipset - like just about every other on-board audio module out there - has only a single hardware channel.

Most 32-bit users never notice this because ALSA uses DMix to do a software mixing of sound *before* it actually hits the sound device and it works pretty well for the most part.  However, one of the libraries that is essential to this function, libesd-alsa0, has not yet been ported for the AMD64 architecture (nor does the source for it compile cleanly due to some forward-looking dependencies).  Without this library we are dependent on libesd0 and this causes almost a full 1-second lag in the sound system and/or low volume combined with a lot of crackling and popping (a nuisance at best and lethal in some games at worst)

The result was that no matter what I did, no matter what I tweaked on, I could not get solid software mixing.

I had never planned on sticking with the on-board sound module anyway (I just really wanted to see what the on-board module could do) so I figured this was the perfect time to get off my butt and put my SoundBlaster Live! in there.  On the first boot Ubuntu (Kubuntu, actually) picked it up and correctly configured it and - tada - I have my 32 hardware channels back and can mix and match all kinds of simultaneous inputs. :)

---

