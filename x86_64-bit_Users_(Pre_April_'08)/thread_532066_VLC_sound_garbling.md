---
title: "VLC sound garbling"
date: 2007-08-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by raijinsetsu on 2007-08-22
I'm having a problem with my VLC player(but not Kaffeine w/xine libs or mplayer). I've tested multiple audio and video/audio files, and I get the same result. VLCs forums are... not helpful.
The problem: audio playback "hiccups". It will play fine for a period of time, and then "hiccup", then continue to play fine.
Looking at the messages window, I see that "mpgatofixed32" is reporting "huffman buffer underruns". Now, because this same version of VLC works on my 32-bit Ubuntu install on my server, but not on my 64-bit install on my laptop, I think it's a problem with VLC 64-bit compatibility.
It doesn't matter whether I try Alsa, Oss(AOss), or Esound, they all have the same "hiccup". This does not happen in Kaffeine or MPlayer, but I dislike they're interfaces.
So, I have two options:
1) find a fix for VLC
2) install the 32-bit VLC

Any help would be appreciated.

---

### Post by dabl on 2007-08-22
You could be right, or it could be that your server has a better/faster CPU doing the processing.  In other words, the "64 vs. 32-bit" suspicion might be changed to "laptop processing vs. server processing".

Can you watch your CPU resources meter on the laptop, and see what happens when it "hiccups"?

---

### Post by raijinsetsu on 2007-08-22
> **dabl said:**
> You could be right, or it could be that your server has a better/faster CPU doing the processing.  In other words, the "64 vs. 32-bit" suspicion might be changed to "laptop processing vs. server processing".

Can you watch your CPU resources meter on the laptop, and see what happens when it "hiccups"?

My pocket watch can decode and watch these streams. I guarantee it's not a processing power problem. :) Plus, it works in Mplayer and Kaffeine, but not in VLC.
Just in case, I will check CPU usage during one of the hiccups when I get home. But I don't think that's the problem. :)

---

