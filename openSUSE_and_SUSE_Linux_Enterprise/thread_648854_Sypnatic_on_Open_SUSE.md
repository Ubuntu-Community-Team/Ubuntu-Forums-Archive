---
title: "Sypnatic on Open SUSE?"
date: 2007-12-24
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Moonfrost on 2007-12-24
Hi, I'm using Ubuntu Gutsy but I was thinking on going back to SUSE to check something out specially since it's "back to normal" and doesn't have the problems 10.1 had...I also heard 10.2 and .3 are faster than 10.1...anyways, I heard that I can install Sypnatic on SUSE...is that true? if I can how? because the only thing I'm not too sure about yet is Yast which is the only thing I really didn't like that much about SUSE...

---

### Post by ~LoKe on 2007-12-24
To be honest, this isn't the Suse forums. ;)

Perhaps a solution could be found [here](http://forums.suselinuxsupport.de/index.php?showtopic=25860) in the second post.

---

### Post by Moonfrost on 2007-12-24
> **~LoKe said:**
> To be honest, this isn't the Suse forums. ;)

Perhaps a solution could be found [here](http://forums.suselinuxsupport.de/index.php?showtopic=25860) in the second post.

Yeah I know that but since Sypnatic is usually related to Ubuntu or Debian I posted it here...

---

### Post by Bachstelze on 2007-12-24
Moved to OpenSuse Discussions.

---

### Post by bigken on 2007-12-24
> **~LoKe said:**
> To be honest, this isn't the Suse forums. ;)




and its not a windows forum either but we get loads related questions relating to it 

at least suse is a linux OS :)

Im running open suse 10.3 on one of my machines and its fast

---

### Post by Moonfrost on 2007-12-24
> **bigken said:**
> and its not a windows forum either but we get loads related questions relating to it 

at least suse is a linux OS :)

Im running open suse 10.3 on one of my machines and its fast

Ok...some mod is gonna kill me if I talk anything not related to Ubuntu again but...is 10.3 fast like you said? because 10.1 was kinda slow (at least the 64bit version which I have and haven't tried 10.2).

---

### Post by Bachstelze on 2007-12-24
> **Moonfrost said:**
> Ok...some mod is gonna kill me if I talk anything not related to Ubuntu again but.

Now, now... I just moved your thread to the relevant section of the forums.

---

### Post by Incense on 2007-12-24
10.3 is really nice. YaST is a bit faster then it was in 10.2. You can install apt4rpm and run synaptic, but to be honest it's much more work then it's worth. I would recommend installing and useing the SMART package manager. It has the same look and feel as synaptic, and is just as fast (maybe even faster). You can even install from the command line with a quick 

```
smart install packagename
``` 

This page will help you get SMART up and running. 

[http://dev-loki.blogspot.com/2007/10/smart-on-opensuse-103.html]("http://dev-loki.blogspot.com/2007/10/smart-on-opensuse-103.html")

---

### Post by RedDwarf on 2007-12-24
If you read it in my previous post... I also said that to search for packages you should use [http://software.opensuse.org/search](http://software.opensuse.org/search)
It's available in home:rbos OBS repository.

Anyway I would also highly recommend Smart... also in Ubuntu!!!
Also looks like Synaptic for openSUSE is outdated. In Ubuntu Hardy and Debian Unstable I see Synaptic 0.61. But if you go to the Synaptic homepage ( [http://www.nongnu.org/synaptic/](http://www.nongnu.org/synaptic/) ) the last available version is 0.57.2... and 0.57.2 is the version available in openSUSE. If someone can explain to rbos how is the Synaptic development working right now he probably will update the packages for openSUSE.
Also apt-rpm homepage says tha last available *stable* version is from 18 months ago. And the stable version is the one packaged for openSUSE. I don't know how this version of apt-rpm compares to the last available *real* apt.

---

