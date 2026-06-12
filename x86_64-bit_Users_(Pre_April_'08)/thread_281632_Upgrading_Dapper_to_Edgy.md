---
title: "Upgrading Dapper to Edgy"
date: 2006-10-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by fabertawe on 2006-10-21
Hi Folks...

I have decided I will upgrade to Edgy (when it's officially released, about 5 days?) and was wondering if anyone's actually done this yet? I'm sure we'll get a raft of threads about this soon and want to prepare myself as much as is possible. I had considered a fresh install of the Edgy i386 but after all I've been through I just can't do it ;) 

I understand there will be only one 'generic' version of the kernel... is this correct and if so, does this pose any upgrade problem in itself?

How will the use of 32bit apps/libs be affected (if at all)... should I back up '/usr/lib32' for future use, for instance?

I've read a fair bit on the upgrade process itself with much dispute about the best method, is```
gksu "update-manager -c -d"
```the best choice?

My questions might be unnecessarily paranoid (or pointless) but I've read enough threads with upgrade problems to feel the need to ask ;) If there are any precautions I need consider then please post!

Cheers ... Paul

[Ubuntu Dapper 6.06, amd64-k8]

---

### Post by dasyar613 on 2006-10-21
I just did a live CD of Edgy RC. Umm, will I upgrade, at this point no. Some general observations: Look and feel is still the same, I guess that is good. I ran firefox, you will still have to go through the hassle of making all the eye candy work. I was hoping that their would be a built in feature for this, something like - add firefox with plugins and other stuff. The add printer still needs to be updated, the kubuntu version still works more efficiently. Those were just a few things that I looked at. For now, not worth the hassle to upgade.

---

### Post by kuja on 2006-10-21
Everything seems to be the same as dapper 32-bit wise, a relief for me anyway.

What I do for my upgrades is download the alternate cd, then add it to my repo list with apt-cdrom. That way I get my upgrade and the cd at the same time :)

---

### Post by ghostofcain on 2006-10-21
Ran the upgrade via **gksu "update-manager -c -d"** on thursday night and so far **no major** issues, I suppose it's always a good idea to back up **/home** and so forth before any updgrade, but then again I'm not that sort of person really, only issues so far appear to be minor issues with a couple of apps. it appears mplayer(32bit) doesn't work at present but hopefully the automatix crew will be on to that soon

---

### Post by kuja on 2006-10-21
> **ghostofcain said:**
> Ran the upgrade via **gksu "update-manager -c -d"** on thursday night and so far **no major** issues, I suppose it's always a good idea to back up **/home** and so forth before any updgrade, but then again I'm not that sort of person really, only issues so far appear to be minor issues with a couple of apps. it appears mplayer(32bit) doesn't work at present but hopefully the automatix crew will be on to that soon
There are two good ways to work around the lack of a working mplayer32 package (if I remember right, it involves conflicting files between mplayer32 and one of the ia32-libs packages, or something of that nature, among possibly other things). Anyway, Mplayer from SVN works fine. The version of VLC in Edgy Universe also works.

---

### Post by fabertawe on 2006-10-22
Thanks for the feedback everyone :mrgreen: 

@dasyar613 - you're probably right about the hassle but I get itchy and can only resist so long... plus I've been hanging back on trying Compiz/Beryl until I move to Edgy as I don't fancy the challenge twice ;) and I've locked Cupsys at the moment but I understand the driver (Lexmark Z53) for my printer is fixed in Edgy. And I'd be running i386 if I wasn't some kind of masochist :rolleyes:

@ghostofcain - thanks for the confirmation. I do backup these days.. a full disk image every couple of weeks and an incremental of ~/home as often as I remember. I've been stung too often not to now!

@kuja - that's a good idea regarding the ISO, I'll do that :KS I actually tried Mplayer from SVN yesterday but it didn't help my system lockups when watching video so that's another reason to try Edgy. Do you know if the Mplayer browser plugin works without all the 32bit stuff? I'm wondering if we're getting close to be able to use 64bit FF.. the nspluginwrapper sounds like it might take care of Flash 9 now.

Cheers ... Paul

---

### Post by kuja on 2006-10-22
The browser plugin will work, just, it won't play things that need support of 32-bit plugins. (That is, unless you're using it from SVN, which likely breaks from time to time) I've heard nspluginwrapper is still buggy, that is, after a few pages your browser will hang/crash,  or something along those lines. I guess it still needs some work, though I don't use FF so I guess it doesn't apply to me anyway.

---

### Post by Paulo Wageck on 2006-10-22
didnt work for me
i dont recomend...
backup...
fresh new install is always the way to go.

---

### Post by RAOF on 2006-10-23
> **Paulo Wageck said:**
> didnt work for me
i dont recomend...
backup...
fresh new install is always the way to go.

Updating to a development version is not (officially) supported.  You're meant to find bugs with the update, and report them :).

Once Edgy is released, it **should** be safe to upgrade to it (and I believe that the Update Manager will ask you if you want to update automatically, when Edgy is released.

---

### Post by bluenova on 2006-10-23
Yea, as long as you have /home in a separate partition then a fresh install is really the best way. It take the same amount of time as doing an upgrade and you end up with a much cleaner system whilst keeping all your settings as they are in /home.

---

### Post by ckempo on 2006-10-23
I maintain my sister's PC, which is currently running Dapper. As she has a 1GB monthly cap on her broadband, doing an upgrade via apt-get is out of the question as downloading that much, coupled with her normal use, will be over her limit.

Does anyone know if I can download the CD and burn it at my house, then take the CD to hers and use that to load the packages and do the upgrade? Or, being as I'd have a CD there, is it easier to just do a complete reinstall from that?

---

### Post by fabertawe on 2006-10-23
> **ckempo said:**
> Does anyone know if I can download the CD and burn it at my house, then take the CD to hers and use that to load the packages and do the upgrade? Or, being as I'd have a CD there, is it easier to just do a complete reinstall from that?

[Edgy upgrade info]("https://help.ubuntu.com/community/EdgyUpgrades").

Paul

---

### Post by ckempo on 2006-10-26
Cheers Paul, that'll do.

---

### Post by kuja on 2006-10-26
Edit: I misread something, oh well.

---

### Post by fabertawe on 2006-10-26
> **ckempo said:**
> Cheers Paul, that'll do.

Upgraded myself today, from CD. Amazed how smooth it was really.. everything seems to be working so far, like there was no change!

Paul

---

