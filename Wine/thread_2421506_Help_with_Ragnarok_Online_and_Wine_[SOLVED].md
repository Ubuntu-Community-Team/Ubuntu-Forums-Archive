---
title: "Help with Ragnarok Online and Wine [SOLVED]"
date: 2019-06-22
forum: Wine
---

### Post by jitterssnowpaw on 2019-06-22
I was told to run this in the Linux guide for installing RO but here's what is going on:

I run these commands:

```
wget -qO - https://dl.winehq.org/wine-builds/Release.key | \
                        sudo apt-key add - && \
                        sudo apt-add-repository https://dl.winehq.org/wine-builds/ubuntu/ && \
                        sudo apt-get update && \
                        sudo apt-get install winehq-stable ttf-mscorefonts-installer                     
```

I'm getting this:

```
taiku@kitsuneon:~$ wget -qO - https://dl.winehq.org/wine-builds/Release.key | \
> sudo apt-key add - && \
> sudo apt-add-repository https://dl.winehq.org/wine-builds/ubuntu/ && \
> sudo apt-get update && \
> sudo apt-get install winehq-stable ttf-mscorefonts-installer 
[sudo] password for taiku: 
OK
Get:1 https://dl.winehq.org/wine-builds/ubuntu disco InRelease [6,255 B]
Hit:2 http://us.archive.ubuntu.com/ubuntu disco InRelease                      
Hit:3 http://security.ubuntu.com/ubuntu disco-security InRelease               
Err:1 https://dl.winehq.org/wine-builds/ubuntu disco InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F
Hit:4 http://us.archive.ubuntu.com/ubuntu disco-updates InRelease
Hit:5 http://us.archive.ubuntu.com/ubuntu disco-backports InRelease
Reading package lists... Done
W: GPG error: https://dl.winehq.org/wine-builds/ubuntu disco InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F
E: The repository 'https://dl.winehq.org/wine-builds/ubuntu disco InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
taiku@kitsuneon:~$ 

```

Please help. XD

---

### Post by oldos2er on 2019-06-23
> the public key is not available: NO_PUBKEY 76F1A20FF987672F

Install the key. ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 76F1A20FF987672F

sudo apt update
```

---

### Post by jitterssnowpaw on 2019-06-23
Thank you guy, it works it all works now. Yay!

---

### Post by jitterssnowpaw on 2019-06-23
Ok I'm having one last problem with this. I'm running the game in a 1024x768 and I get a black window with sound, the sound works. But if I run it in 800x600 it works. Is there anyway you can help me with this XD

---

### Post by howefield on 2019-06-23
Moved to the "*Wine*" forum.

---

### Post by jitterssnowpaw on 2019-06-24
Ok bumping. I'm also having graphics lag. It's Ragnarok Online I know I could go to wine forums but I can't log in their system is being stupid saying I logged in the max number of atemps and I waited 2 weeks tried again and it's saying that so, I mean if anyone has any head knowledge or can help with a quick fix please help mah

---

### Post by wildmanne39 on 2019-06-24
As this is another issue please start a new thread for this topic.

Thanks

---

