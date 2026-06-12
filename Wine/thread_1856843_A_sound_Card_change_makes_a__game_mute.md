---
title: "A sound Card change makes a  game mute"
date: 2011-10-09
forum: Wine
---

### Post by linuxyogi on 2011-10-09
Hi,
Recently my onboard sound went bad so I installed an old sound card which I had in stock.

```
01:09.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
```

I regularly play Tom Clancy's Hawx under wine. But after installing this card the game has no sound whatsoever.

Tried removing pulse audio but same thing. 

```
wine --version
wine-1.3.29
```

This is a 6 channel sound card I have selected Analog Stereo Duplex in Pulse Audio volume control.

Tried alsamixer.

Is there a way ?

---

### Post by ergo-proxy on 2011-10-09
Did you try to emulate sound (via winecfg-sound) options?

---

### Post by linuxyogi on 2011-10-09
> **ergo-proxy said:**
> Did you try to emulate sound (via winecfg-sound) options?

Yes. Still no sound.

---

### Post by linuxyogi on 2011-10-09
Installed Lubuntu 11.04

Using the WINE PPA

Problem Solved.

---

