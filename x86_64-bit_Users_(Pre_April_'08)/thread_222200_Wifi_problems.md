---
title: "Wifi problems"
date: 2006-07-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by RevRogue on 2006-07-24
Alright, perhaps one of the very knowledgeable and nice forum members would plz plz plz giove me a hand in fixing a problem that I am having with my wifi problem. :D

I have a HP zv6209us 64b laptop and have installed kubuntu DD on a second partition. Now I am having a problem connecting to a wireless router, I go into the connections where it lists the hardware and it tells me it is disabled so I turn it on only for it to turn itself right back off. ? any solutions?

ps Also on a side note I connect using a wire and try to connect to the internet but it tells me that it cannot find the address. 

pss I also have a sound problem but its more of a second problem to the connectivity, I am unable to play my mp3's the built in players say they have loaded the song but they play for about second but do not give any sound. When I reboot to my xp part. I am able to play these files just fine. ( I have all my music an such backed-up on a xternal HD) :( plz someone help me I really really want to learn linux better.

---

### Post by Paerez on 2006-07-24
1) I recommend installing network-manager (I think there is a network-manager-kde) its very good at connecting.

2) Have you followed the restricted formats guide? That may give you some extra codecs for the mp3s.
[https://help.ubuntu.com/community/RestrictedFormats#head-1340337f2ca1d0c54900935468515ba7630fcc59](https://help.ubuntu.com/community/RestrictedFormats#head-1340337f2ca1d0c54900935468515ba7630fcc59)

---

### Post by RevRogue on 2006-08-01
Just to kinda give an update on this post, I am able to connect to the internet with a wired connection however the wireless is still giving me fits. I can go into the connection manager and click "enable" but it disables it self right after I click the button. its very odd. I've tried running the live cd again to hopefully see if it is a module problem but the live cd is unable to activate the wifi as well.

---

### Post by RevRogue on 2006-10-29
As an update I have installed ubuntu 6.10 and have attempted to get my wireless drivers to compile however when I go to finish up ( I believe) I get this after typing ```
sudo modprobe ndiswrapper
```

```
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper.ko): Invalid arguement
```

Hopefully this is a small glitch on my part and one of the great linux guru'smight help me get wifi for my lil 64bit lappy

PPPLLLZZZZZZ :D

---

### Post by alek66 on 2006-10-29
I used ndiswrapper and when I did a modprobe this came up
> FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument


any toughts¿?

---

### Post by RevRogue on 2006-11-03
No clue I still cant find the soultion to this error. Was hoping someone would post with an idea how to possibly fix it

---

