---
title: "PlayOnLinux Wine versions manager not showing the latest wines"
date: 2018-05-31
forum: Wine
---

### Post by ardouronerous on 2018-05-31
I'm running Lubuntu 16.04 and PlayOnLinux version is 4.2.12.

I've been experiencing this for 2 days now, the PlayOnLinux Wine versions manager not showing the latest wines, up until two days ago, it was showing latest wine versions 3.0 to 3.8, but now it's only showing 1.7.33 and down.

[ATTACH=CONFIG]279931[/ATTACH]

How do I fix this or is it a problem with PlayOnLinux itself?

---

### Post by schtufbox on 2018-05-31
The repository is down, unsure why or for how long.  It's usually slow in updating anyway so I've taken to just using wine builds from Lutris in PlayOnLinux as usually more up to date :D
As for how...
FGind the wine version you want here:

[https://lutris.net/files/runners/](https://lutris.net/files/runners/)

unarchive and then copy the resulting folder to your .PlayOnLinux/wine/linux-amd64(or linux-x86 depending on architecture)  folder

It should then show as an available wine version to use in PoL.   Hope this helps :D

---

### Post by ardouronerous on 2018-05-31
Thanks for the info. I figured it was down. Just have to wait til it's up and running again.

where did you get the information that the repository is down? I've been searching PlayOnLinux forum and no one seems to be discussing it.

---

### Post by schtufbox on 2018-05-31
Can't remember offhand, but I saw a link on reddit that went to either the pol4 github or pol5 and it was mentioned there

---

### Post by ardouronerous on 2018-05-31
Thanks, I hope PlayOnLinux team fixes this.

---

