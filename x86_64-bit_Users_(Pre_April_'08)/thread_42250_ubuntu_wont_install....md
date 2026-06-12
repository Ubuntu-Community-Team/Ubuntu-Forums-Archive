---
title: "ubuntu wont install..."
date: 2005-06-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by lukus001 on 2005-06-16
Just built up my new pc today, trying to install ubuntu AMD 64 build version and i keep getting a error, basically saying 'boot error, insert boot cd and press enter to continue'

I've whacked in my brother's windows XP cd and that booted fine, so i can't see it being the CD drive... also tried booting it on my brother's computer and it just went "boot cd:" twice and started windows (i guess once per every cd drive) but he hasn't got AMD 64 if that would affect anything.. but it looks like i can't even use his computer to install it onto my HDD...

I was gonna try the floopy drive for 'flaky or non-registered CD drives' but as it was all built up with water cooling with no floppy drive installed with the wrost motherboard configuration i've ever had concerning sockets... a couple of the pins have got bent ... dunno if i did that trying to put the cable in but floppy is out of the question now.

help.... i don't want to go back to windows xp  :roll:

---

### Post by ::DoGG:: on 2005-06-16
Maybe You burne dthe cd image wrong ?
Did You used BURN IMAGE option in your software ? Probably cd is badly burned - the files are in, but tehre is no boot sectors on it. You have to burn all the image - not files. What software do You use to burn cd ?

---

### Post by lukus001 on 2005-06-16
just sent the file directly to burn on cd with... uh window XP... or should i say my brothers... i told them to insure it stayed .iso... im guesing i need to download  better burning software?

---

### Post by Griffology on 2005-06-16
I used Nero but had to make sure you burned it as an ISO image, not a regular burn like you would with music or other data.  I've heard good things about Alcohol 120% too.

---

### Post by lukus001 on 2005-06-17
i think it might be my cd rom drive becuase i've now downloaded some software and burnt the iso image properly... and it still came up with boot disk error...  but now my cd rom is refusing to power up so i think it just my cd rom thats screwed... gonna have to buy a new one i think

---

### Post by ::DoGG:: on 2005-06-17
I`m using Nero, download it, ru it and then "recorder" - "Burn Image". navigate to your iso image file and click ok, that`s it, oh, and another thing - don`t burn it on rw disc, sometimes burning boot sectors on rw discs fall even when it shows no errors, but on standard blank cd-r it should be ok.
You can get nero from here:
[http://www.nero.com/eng/nero-prog.php](http://www.nero.com/eng/nero-prog.php)

---

### Post by FluffyElmo on 2005-06-17
Before burning, you should also be sure that the MD5 sums match in case your image was corrupted while downloading. If the MD5 doesn't match you'll have to try downloading it again.

Get a utility for Windows to generate the MD5 sum for the ISO you downloaded and make sure it matches with the list below (taken from the download site this morning).

```
539a25fd0c5e1e6bb5d1f968ec25b759  ubuntu-5.04-dvd-amd64.iso
765dc370887735af71bc2cf6fcc9fafd  ubuntu-5.04-dvd-i386.iso
73d38d21bd14b902252bca0f39e7eb54  ubuntu-5.04-dvd-powerpc.iso
**46135038af6dd2ef36fd8d521afe7de4  ubuntu-5.04-install-amd64.iso**
f6b3f164c99761234858a4d2c12d0840  ubuntu-5.04-install-i386.iso
bf3fe18eb2fbc450769237dec189405b  ubuntu-5.04-install-powerpc.iso
664e3d7864c0f4f2d2efc09ec230fb2e  ubuntu-5.04-live-amd64.iso
77a1a8be45e0cc93a14c9b9bf00f6648  ubuntu-5.04-live-i386.iso
811a1aec315dae0ceef5d8e626584874  ubuntu-5.04-live-powerpc.iso
```

---

### Post by lukus001 on 2005-06-17
it's all working now guys...

after finding out the download on my brother tom's computer was corrupt, i downloaded it again and was still corrupt... i then got the iso image burner installed on m other brother's comp who doqnloaded the iso last night... installed it and worked, although i has to burn it back down to 4X so it worked properly.

---

### Post by bored2k on 2005-06-17
[QUOTE=lukus001]it's all working now guys...

after finding out the download on my brother tom's computer was corrupt, i downloaded it again and was still corrupt... i then got the iso image burner installed on m other brother's comp who doqnloaded the iso last night... installed it and worked, although i has to burn it back down to 4X so it worked properly.[/QUOTE]
 Glad it worked. Hope to see you soon on the forums ;).. or.. hope we don't see you because everything ran fine :D ;)

---

