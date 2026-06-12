---
title: "VipBoxSports"
date: 2013-02-22
forum: Wine
---

### Post by paulemony on 2013-02-22
Anyone got this sports streaming service working in Ubuntu 11.10? I can open it using Wine but it just tells me "Flash player is required..". Adobe Flash plugin 11.2.202.270 is installed, so I'm not sure what it wants.

---

### Post by varunendra on 2013-02-23
*Thread moved to **Wine**.*

--------------------

As you are running the application in Wine, the native flash plugin can't be used.

You will have to download and install the windows version separately in wine, although I'm not sure if it would work even then (haven't tested myself).

Also, be aware that adobe flash player is too resource hungry, and added to it the fact that it would be running on wine - may result in a very high CPU usage on your system.

Link for separate download of adobe flash player : [http://get.adobe.com/flashplayer/otherversions/](http://get.adobe.com/flashplayer/otherversions/)
(you may need the one for "internet explorer")

---

### Post by paulemony on 2013-02-23
Good point, I tried downloading as suggested, both the IE and "other browsers" versions; two steps forward, one step back, now I don't get the error message but the prog doesn't load anyway. Adobe Flash currently lives in Downloads folder & doesn't show up under Applications/Wine/Programs or browse C:drive, does it need to be moved into wine folder?

---

### Post by howefield on 2013-02-23
Does it need to be that particular application ?

Sopcast works well on linux and has a native version.

---

### Post by paulemony on 2013-02-23
That should have been my first question, is there a Linux app anyway? Have downloaded Sopcast, just have to figure out how it works!
Thanks

---

### Post by howefield on 2013-02-24
Hopefully you made sure it does what you want it to do ? I don't know the application that you asked about in the OP, but I do use sopcast which seems to be a similar type application.

Using 12.10 64 bit, all I do is firstly install sp-auth followed by sopcast.

File versions are :

sp-auth_3.2.6~ppa~precise~lffl_amd64.deb
sopcast-player_0.8.3-1~lffl~quantal_amd64.deb

---

### Post by paulemony on 2013-02-24
I seem to have got Sopcast working but the problem with it seems to be limited content, I haven't worked out how to find out what channels are available, other than the handful of foreign language stations that appear in the channel guide in Sopcast player.

---

