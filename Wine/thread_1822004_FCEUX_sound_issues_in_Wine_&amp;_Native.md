---
title: "FCEUX sound issues in Wine &amp; Native"
date: 2011-08-09
forum: Wine
---

### Post by Zeikcied on 2011-08-09
I'm having issues with FCEUX in both Wine and Native.  Both are sound-related, but they're slightly different.

With Wine I'm using FCEUX 2.1.5 and Wine version 1.3.26.  The sound in FCEUX is slightly garbled, with it stuttering and making odd/incorrect sounds on occasion.  I remember this problem was once solved by turning the audio hardware acceleration from Full to Emulation, but that doesn't seem to help anymore.  I tried changing the Windows version, which didn't seem to do anything, and I fiddled with the audio settings in FCEUX to no avail.

As for the native version, I'm using FCEUX 2.1.4 (the current version in the repos).  In this version, the sound just stutters, and I can reduce the stuttering by increasing the sound buffer, but even at the max it doesn't get rid of the stutter (and the max setting introduces some distortion).  It's slightly different, but still a sound problem.

SNES9x also suffers horrible sound issues.  I can get it to somewhat normal by changing the mix interval to 40ms, but that doesn't sound like it should (some notes are slightly delayed).  However, the sound problem isn't in the native SNES9x build, so it's not that big of an issue.  It seems like most, if not all emulators have sound problems in Wine, at least as far as I can tell, and I wish I knew how to fix it.

---

