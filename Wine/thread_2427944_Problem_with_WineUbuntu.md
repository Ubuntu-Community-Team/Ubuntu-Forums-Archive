---
title: "Problem with Wine/Ubuntu"
date: 2019-09-27
forum: Wine
---

### Post by jitterssnowpaw on 2019-09-27
Hello last time I got help for this but can't find the topic. It's been about 7 months since i asked this question got help and it worked but here's the problem I'm having:

It's not recognizing the GPG key or something here's the output:

```
:~$ wget -qO - https://dl.winehq.org/wine-builds/Release.key | \
> sudo apt-key add - && \
> sudo apt-add-repository https://dl.winehq.org/wine-builds/ubuntu/ && \
> sudo apt-get update && \
> sudo apt-get install winehq-stable ttf-mscorefonts-installer 
[sudo] password for taiku: 
OK
Get:1 https://dl.winehq.org/wine-builds/ubuntu disco InRelease [6,257 B]
Hit:2 http://us.archive.ubuntu.com/ubuntu disco InRelease                      
Err:1 https://dl.winehq.org/wine-builds/ubuntu disco InRelease                 
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F
Get:3 http://us.archive.ubuntu.com/ubuntu disco-updates InRelease [97.5 kB]
Get:4 http://security.ubuntu.com/ubuntu disco-security InRelease [97.5 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu disco-backports InRelease [88.8 kB]
Reading package lists... Done                                         
W: GPG error: https://dl.winehq.org/wine-builds/ubuntu disco InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F
E: The repository 'https://dl.winehq.org/wine-builds/ubuntu disco InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

Thanks

---

### Post by dragonfly41 on 2019-09-27
I don't use wine .. but to find your past threads use advanced search (search "wine" by username "jitterssnowpaw") at top of page ..

[https://ubuntuforums.org/search.php?searchid=20975941](https://ubuntuforums.org/search.php?searchid=20975941)

---

### Post by jitterssnowpaw on 2019-09-27
Oh geeze, thank you!!!

---

### Post by Frogs Hair on 2019-09-27
*Moved to **wine***.

---

