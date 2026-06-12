---
title: "why won't wine run smoothly on my computer?"
date: 2008-09-25
forum: Wine
---

### Post by themusicalduck on 2008-09-25
I've spent hours trying to get some of my games to run well on wine. After going through all the usual tutorials and searching for tweaks, I can usually get a game to run.. and it is sometimes playable. Pretty much every game though just runs very slowly and very choppy, with random lockups sometimes lasting as long as 3-4 mins. Often turning my computer unstable.. slow, screwed sound, etc, until I do a reboot.

After all this I'm thinking there's just some problem specific to my computer.. I could be missing something silly here, and I know the games I'm using can run well in wine, because 90% of reports on the internet say so.

I'm wondering if anyone on here might know what it could be about my computer that is causing these problems? Or if there is likely some setting that I haven't covered which I should have. Though I feel like I've covered almost every possible option that I can find..

The games I'm trying to play primarily are - WoW, TrackMania and TF2. None of them really run smoothly, Trackmania probably runs best, but has slow loading and is prone to locking up frequently.

My hardware is - Gigabyte GAK8NXP-9 mobo, Nvidia 6600GT video, AMD Athlon X2 3800+ - 64bit, M-Audio 192 sound card. I know details about any other hardware but those are they ones I think might be relevant to anything. I am using ALSA drivers and nvidia-glx-new drivers. and I'm running Hardy with the latest wine version.

I know wine had a problem with the 3800+ before, something about multi-threading? but I think this was fixed in an earlier version and it did make games runnable rather than unusable.

Close to giving up on wine entirely. I tried doing a TrackMania install using PlayOnLinux, but somehow it seemed to run even worse.. and I guess I'm a little bored of having to switch to Windows just to pass a bit of time on TF2 :)

---

### Post by asdfoo on 2008-09-25
> **themusicalduck said:**
> I've spent hours trying to get some of my games to run well on wine. After going through all the usual tutorials and searching for tweaks, I can usually get a game to run.. and it is sometimes playable. Pretty much every game though just runs very slowly and very choppy, with random lockups sometimes lasting as long as 3-4 mins. Often turning my computer unstable.. slow, screwed sound, etc, until I do a reboot.

After all this I'm thinking there's just some problem specific to my computer.. I could be missing something silly here, and I know the games I'm using can run well in wine, because 90% of reports on the internet say so.

I'm wondering if anyone on here might know what it could be about my computer that is causing these problems? Or if there is likely some setting that I haven't covered which I should have. Though I feel like I've covered almost every possible option that I can find..

The games I'm trying to play primarily are - WoW, TrackMania and TF2. None of them really run smoothly, Trackmania probably runs best, but has slow loading and is prone to locking up frequently.

My hardware is - Gigabyte GAK8NXP-9 mobo, Nvidia 6600GT video, AMD Athlon X2 3800+ - 64bit, M-Audio 192 sound card. I know details about any other hardware but those are they ones I think might be relevant to anything. I am using ALSA drivers and nvidia-glx drivers. and I'm running Hardy with the latest wine version.

I know wine had a problem with the 3800+ before, something about multi-threading? but I think this was fixed in an earlier version and it did make games runnable rather than unusable.

Close to giving up on wine entirely. I tried doing a TrackMania install using PlayOnLinux, but somehow it seemed to run even worse.. and I guess I'm a little bored of having to switch to Windows just to pass a bit of time on TF2 :)

Hmm... Do you have the latest nVidia drivers?  Are you running Wine-1.1.5?

---

### Post by themusicalduck on 2008-09-25
Yep, wine 1.1.5 and latest nvidia drivers according to the repositories. Also I have nvidia-glx-new and not nvidia-glx like I said in my post. Edited it..

---

### Post by Bios Element on 2008-09-25
Well one issue is a Nvidia 6600 isn't exactly a high powered card. So at least part of your poor performance could be because of that.

---

### Post by themusicalduck on 2008-09-25
It isn't a great card, but all of these games run pretty well in windows on the same machine. On wine they're unplayable.

---

### Post by Ferrat on 2008-09-25
Well stuff in general lose some preformance compaired to the same game/app in Win XP, how it runs depends heavily on hardware setup and how well all the drivers etc work for your specific stuff, also settings matter alot and are also varying on what hardware you have .

Your best bet is to mess around with settings, I know that at least for me it can vary a lot and it might just be one library here or a setting there that does the difference.

---

### Post by aoanla on 2008-09-26
Also, in the case of TF2, it's worth using the -dxlevel 81 switch (set in Launch Options in Steam) which should improve your performance.

It's also worth using EnvyNG (in the repositories) to upgrade your driver - I guarantee that there will be a newer version than the one in the repositories.

---

### Post by asdfoo on 2008-09-26
> **aoanla said:**
> Also, in the case of TF2, it's worth using the -dxlevel 81 switch (set in Launch Options in Steam) which should improve your performance.

It's also worth using EnvyNG (in the repositories) to upgrade your driver - I guarantee that there will be a newer version than the one in the repositories.


As well as that, some games work better with the OffScreenRenderingMode registry key set to fbo - usually the howto on the AppDB for the program will mention it if so.

---

### Post by themusicalduck on 2008-09-26
Thanks for the replies.

I'll try a couple of these things out and see if they help a bit.

---

