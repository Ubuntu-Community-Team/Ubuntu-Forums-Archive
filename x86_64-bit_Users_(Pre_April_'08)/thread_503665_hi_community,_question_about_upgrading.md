---
title: "hi community, question about upgrading"
date: 2007-07-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by gunnerman on 2007-07-18
I first want to say hi and thanks to this wonderful community, the info given about how to generally make ubuntu work properly is amazing and well documented. I have been a windows user for the past 10 years or so and have always heard about linux but could either never find a copy of it or really understood about all the distros out there. Finally I have been using x64 ubuntu, kubuntu for the past month and a half and have not even touched the other OS, this is simply amazing everthing works correctly with the exception of a few little pieces here and there, which I found work arounds for. 

My question is when there is a new version released every six months, do I need to do a fresh format install or is there an upgrade via terminal?

---

### Post by benjaminwr on 2007-07-18
Hi,

You can always upgrade your system to the new one by changing your repos to the new version, eg.:

```
deb http://archive.ubuntu.com/ubuntu/ feisty main restricted
```

to

```
deb http://archive.ubuntu.com/ubuntu/ gusty main restricted
```

and then typing

```
sudo aptitude update
```

```
sudo aptitude dist-upgrade
```

I recommend using aptitude instead of apt-get because it is better at resolving dependancies.

Always have a backup of your system and if you have trouble with the upgrade just make a fresh install.
Cheers

---

### Post by Kilz on 2007-07-18
> **gunnerman said:**
> I first want to say hi and thanks to this wonderful community, the info given about how to generally make ubuntu work properly is amazing and well documented. I have been a windows user for the past 10 years or so and have always heard about linux but could either never find a copy of it or really understood about all the distros out there. Finally I have been using x64 ubuntu, kubuntu for the past month and a half and have not even touched the other OS, this is simply amazing everthing works correctly with the exception of a few little pieces here and there, which I found work arounds for. 

My question is when there is a new version released every six months, do I need to do a fresh format install or is there an upgrade via terminal?

One important thing to remember , if you are new to linux. Until something is released, ask yourself this question" Do I have the skills to fix the problems when it breaks?"
When a new version is released you will get an upgrade notification, something like what happens now when an update is released. I would wait for it. Upgrading th Gutsy (now in Alpha testing) could be a big mistake. Things break during development, if you dont have the skills to fix them, you face a reinstall. 
I would even suggest waiting a few weeks after release, that way any serious bugs that may have slipped by the release testing will be fixed.

---

### Post by gunnerman on 2007-07-18
I wouldn't think about upgrading now, only when the next stable version is released.  I dont worry if somthing is broke, or I need to research it to fix the issue, that is where the fun is. I am not to sure If I have the skills now to fix issues on my own but in time I am sure I will.

---

### Post by tgalati4 on 2007-07-18
If you have a working system, I would leave it for now.  Find another machine or help someone else and then install a later version of Ubuntu.

Alternatively, burn a Live disk and test out the new features.  That way you won't bork your working system, and you can see what's new.

---

