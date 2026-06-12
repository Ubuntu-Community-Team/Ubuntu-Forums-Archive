---
title: "audio volume bug"
date: 2008-05-07
forum: x86 64-bit Users
---

### Post by Julius on 2008-05-07
I have a problem/bug, although I can't tell whether it is specific to my onboard sound adapter (mobo asus p5k-e wifi) or if the problem is in the alsa mixer.

Anyway, if I set the volume to the highest in the volume applet next to the clock, it doesn't sound as loud as I know it should. If I double click the volume control, the alsa mixer opens, and then I can set the "Front" volume to the highest, then it WILL sound loud.

The thing is, if I set the "front" volume bars to the maximum, and then attempt to change the volume of the "master" one, it will go back to the previous not-so-loud max volume, even though the "Front" is still to the max. 

If the "front" volume is set to something below the max, let's say, the middle, then the master volume will abide to that and there won't be anything sounding louder than what's set in front. 

So the only way of getting the loudest volume is to manually set the 'front' bar  to the maximum, and leave it there. WHenever I try to change the volume of either the master or the front channels, it will revert back to a point in which the maximum is REALLY quiet rather than loud.


DOes it make sense, what I'm saying? It's difficult to explain.

ANybody else experiencing this?

Update: apparently all bars have to be set to the max (headphone, PCM, front, and master) to get the loudest volume.  It's a known bug
[https://bugs.launchpad.net/ubuntu/+bug/192040](https://bugs.launchpad.net/ubuntu/+bug/192040)

---

