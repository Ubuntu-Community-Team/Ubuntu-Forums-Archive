---
title: "Pacman/Opensuse repo conflicts"
date: 2008-05-16
forum: openSUSE and SUSE Linux Enterprise
---

### Post by 67GTA on 2008-05-16
I have installed 10.3 five times. Each time I run into problems after adding the pacman repo. The opensuse repos are not quite enough. After trying to install a few things, it starts complaining about missing dependencies/libs because one repo doesn't have the right lib or dependency. I noticed the pacman repo has newer versions than opensuse. I assume this is where it's starting to go down hill. Do these repos have the same things in them? Would I be able to disable the opensuse repo, and just use the pacman repo without missing any apps from the opensuse repo? Am I missing something? This is driving me crazy!

---

### Post by Erunno on 2008-05-17
I know this problem but I'm not sure how to help. I never really use repositories outside the build service and the few things I need and which are not found there I either compile myself (e.g. xine-lib, libdvdcss) or put in a local repository (w32codecs, Microsoft TrueType fonts).


Smart supports giving priorities to repositories so that it'll prefer a specific repository for its dependency needs. This feature also found its way into openSUSE 11.0 so hopefully handling of multiple repositories will improve in the feature.

---

### Post by 67GTA on 2008-05-17
That sounds nice. Maybe this will get better. I always wind up getting in to a gridlock with installing apps(very frustrating). I have never tried Smart. I might give it a look.

---

### Post by Incense on 2008-05-17
I am running 11 beta 3 right now, and have had no dep problems. Zypper is super fast, and everything has been very stable for me. If you don't want to take the dive quite yet, then I would really take a look at the SMART PM. It's very fast and easy to use. Just plug the following into konsole as SU to install.

```
zypper sa -r http://download.opensuse.org/repositories/smart/openSUSE_10.3/smart.repo
zypper ref smart
zypper install smart
smart channel --add http://linux01.gwdg.de/~pbleser/files/smart/opensuse-10.3.txt
smart mirror --add http://linux01.gwdg.de/~pbleser/files/smart/mirrors-eu.txt
smart update
smaart install smart-gui
```

---

### Post by 67GTA on 2008-05-18
[quote=Incense;4983949]I am running 11 beta 3 right now, and have had no dep problems.

Did you experience the dependency problems I am mentioning in 10.3?

---

### Post by Incense on 2008-05-18
> **67GTA said:**
> [quote=Incense;4983949]I am running 11 beta 3 right now, and have had no dep problems.

Did you experience the dependency problems I am mentioning in 10.3?

Oh yeah, all the time. I would have dependency issues before I added the pacman repo. Just trying to install Gnome from the repo after a fresh KDE install almost drove me to windows. SMART does a **much** better job then YaST at handling dependencies.

EDIT: You can also search the build service for the software you're looking for. [http://software.opensuse.org/search]("http://software.opensuse.org/search"). That seems to work fairly well.

---

### Post by 67GTA on 2008-05-18
Just downloaded and booted the beta 3 KDE4 CD. I have to say I am impressed with what they have done with KDE4. I'm still not sure about the plasma/widget thing. I like the traditional desktop. I will have to buy the DVD when it goes final and check out all the DE's. I saw where they planned to have KDE 3.5.9 as an install option. Man this is exciting! I have always preferred KDE until now. I am using Mint 5, and Gnome is almost as functional as KDE now. It isn't half bad.

---

### Post by 67GTA on 2008-05-21
Dang it all! The sixth time went down in flames. I was doing good with Smart until I tried to install a kernel security patch from the Yast online update. It didn't tell me that it was going to go from .17 to .13. So I wound up with a three way conflict between ndiswrapper, nvidia, and the kernel. I need all three of these, but they wouldn't coincide together, so Opensuse was rendered useless again. I would probably been fine if I had just stuck with Smart. I really hope version 11 fixes this, because aside from this, I really like Opensuse. It shouldn't be this hard.

---

### Post by 67GTA on 2008-05-30
I just tried 11 RC1. There is a new feature in Yast>Software Repositories. You have a priority button for each repo. This will greatly help the situation. You can now give priority to any desired repo from 0-99. With 10.3, the multimedia packages were crippled so you couldn't add restricted packages with the opensuse repos(gstreamer-ugly for one). The factory opensuse repo actually has gstreamer-ugly. I'm not sure if this will change in GM, but it looks a lot better so far. If they still have the KDE 3.5.9 install option on the DVD like they mentioned earlier in the release, I will try it again when it goes gold.

---

