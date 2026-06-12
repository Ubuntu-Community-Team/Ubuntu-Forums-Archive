---
title: "Taking the plunge"
date: 2007-05-04
forum: openSUSE and SUSE Linux Enterprise
---

### Post by ThinkBuntu on 2007-05-04
Well, I've tried just about every major desktop-oriented Linux OS to this point but have held out against openSUSE because of misgivings about the Microsoft-Novell deal, but I'm going to take the plunge just to see about the hype. Or, call it shaking hands with the Devil :^)

I thought about it, and with Ubuntu coming into Dell, Microsoft really can't do anything to slow down Linux, let alone stop it. Also, a distribution as popular and developed as openSUSE can't possible just close up shop or start charging its users any time soon. If it does, I imagine the project's source code would just be adapted and absorbed by another distribution, and a migration method would be quickly possible.

Anyhow, I've been looking for a thought-out KDE distro, and I've exlcuded PCLOS (too much like Windows overall), MEPIS (old packages, slow), Sabayon (Install DVD kept failing. Mini CD too), and the others that I could install KDE over. I'll post my impressions....

---

### Post by igknighted on 2007-05-05
> **ThinkBuntu said:**
> Well, I've tried just about every major desktop-oriented Linux OS to this point but have held out against openSUSE because of misgivings about the Microsoft-Novell deal, but I'm going to take the plunge just to see about the hype. Or, call it shaking hands with the Devil :^)

I thought about it, and with Ubuntu coming into Dell, Microsoft really can't do anything to slow down Linux, let alone stop it. Also, a distribution as popular and developed as openSUSE can't possible just close up shop or start charging its users any time soon. If it does, I imagine the project's source code would just be adapted and absorbed by another distribution, and a migration method would be quickly possible.

Anyhow, I've been looking for a thought-out KDE distro, and I've exlcuded PCLOS (too much like Windows overall), MEPIS (old packages, slow), Sabayon (Install DVD kept failing. Mini CD too), and the others that I could install KDE over. I'll post my impressions....

Try Mandriva 2007.1 for a KDE distro.  Also try the newer PCLOS 2007, they dropped the "I want to be windows" logo and theme.

EDIT: Was that a serious concern you had about OPENsuse?  It's a community project, just like Ubuntu or Debian.  In fact I think they are more strict about "free as in speech" only stuff in the distro by default than Ubuntu.  So while Novell might be covering their *** from a corporate standpoint, the deal means nothing to desktop users and is just the never-ending posturing of big business.  Look at the deeds Novell has done for the linux/OSS community and you will clearly see that they are one of our biggest supporters.

---

### Post by ThinkBuntu on 2007-05-05
I tried Mandriva a week ago (latest release) and, while I thought that Metisse was pretty neat, was largely unimpressed. Performance was poor and fonts were so anti-aliased as to be blurry and tough to read.

Anyway, I went ahead with Discs 1-3 with openSUSE and also was pretty unimpressed. The installer is great, the look and feel is very nice, but many things that I expect with a "just works" OS were lacking. Wireless didn't work, no codecs worked, and (this one bothered me) when I plugged in my iPod to move over my Home directory, which weighs about 1GB, it opened up some odd customized folder system that I've never seen before showing artists, etc. instead of my files. I went to the terminal, entered "cp /media/IPOD/Home ~/Desktop" and got back errors that it couldn't move the directories.

SO anyway, I finally got Sabayon to install properly, and I must say this blows away everything I've tried to date. I'll have a very mini review in the Gentoo forum, as I don't want to waste space here on an unrelated topic.

---

### Post by igknighted on 2007-05-05
> **ThinkBuntu said:**
> I tried Mandriva a week ago (latest release) and, while I thought that Metisse was pretty neat, was largely unimpressed. Performance was poor and fonts were so anti-aliased as to be blurry and tough to read.

Anyway, I went ahead with Discs 1-3 with openSUSE and also was pretty unimpressed. The installer is great, the look and feel is very nice, but many things that I expect with a "just works" OS were lacking. Wireless didn't work, no codecs worked, and (this one bothered me) when I plugged in my iPod to move over my Home directory, which weighs about 1GB, it opened up some odd customized folder system that I've never seen before showing artists, etc. instead of my files. I went to the terminal, entered "cp /media/IPOD/Home ~/Desktop" and got back errors that it couldn't move the directories.

SO anyway, I finally got Sabayon to install properly, and I must say this blows away everything I've tried to date. I'll have a very mini review in the Gentoo forum, as I don't want to waste space here on an unrelated topic.

As I mentioned above, Suse is more strict about non-free stuff than Ubuntu is.  No codecs, no wireless, etc. (If you had the DVD, or if you downloaded the non-free CD, you could have chosen to add support to your install for some wireless cards and flash and a few others).  There's a good guide "Hacking Suse 10.2" I think that explains how to do video drivers and codecs and other popular tweaks: [http://www.softwareinreview.com/cms/content/view/60/](http://www.softwareinreview.com/cms/content/view/60/)

---

### Post by Pobega on 2007-05-05
I don't see why you can't just set things up yourself; A little work never hurt anyone.

If everyone wanted everything to work "Out of the box" the world would be using Ubuntu. But to make everything work out of the box that would mean a lot more packages would have to be put on the install CDs, and deciding which ones are more important than others would be a lot of work for the devs, so most devs just leave the decision up to the end user. I personally prefer that approach to "Okay, everyone needs this and that, so let's put it in by default".

---

### Post by Adamant1988 on 2007-05-05
> **Pobega said:**
> I don't see why you can't just set things up yourself; A little work never hurt anyone.

**If everyone wanted everything to work "Out of the box" the world would be using Ubuntu.** But to make everything work out of the box that would mean a lot more packages would have to be put on the install CDs, and deciding which ones are more important than others would be a lot of work for the devs, so most devs just leave the decision up to the end user. I personally prefer that approach to "Okay, everyone needs this and that, so let's put it in by default".

Actually, they'd probably be using Windows, Mac OS X, Linspire, or Xandros.

---

### Post by RedDwarf on 2007-05-05
> **ThinkBuntu said:**
> I went to the terminal, entered "cp /media/IPOD/Home ~/Desktop" and got back errors that it couldn't move the directories.
You mean...
[QUOTE=man cp]-R, -r, --recursive
 copy directories recursively[/QUOTE]
??

---

### Post by ThinkBuntu on 2007-05-05
> **Adamant1988 said:**
> Actually, they'd probably be using Windows, Mac OS X, Linspire, or Xandros.

I've been searching for the Linux equivalent of OSX for a while, and I feel that Sabayon is it for me. I've been using Macs my whole computing life (I'm typing this from a Mac) and so I have a very high standard for distributions. And I'm not unwilling to work. I did once spend a ton of time getting Zenwalk "just right," but in the end many common tasks like suspending to RAM were too involved, and I started to run into odd bugs here and there. The same goes for Arch, only I was too lazy to take it to the next level.

Anyway, you guys should really give Sabayon a try. I'm loving it!

---

### Post by Adamant1988 on 2007-05-06
> **ThinkBuntu said:**
> I've been searching for the Linux equivalent of OSX for a while, and I feel that Sabayon is it for me. I've been using Macs my whole computing life (I'm typing this from a Mac) and so I have a very high standard for distributions. And I'm not unwilling to work. I did once spend a ton of time getting Zenwalk "just right," but in the end many common tasks like suspending to RAM were too involved, and I started to run into odd bugs here and there. The same goes for Arch, only I was too lazy to take it to the next level.

Anyway, you guys should really give Sabayon a try. I'm loving it!

If you're searching for brain-dead easy, Linspire is probably right up your alley.  CNR is about the most point-n-click installer I've ever seen, and they include everything you'd ever want to install OOTB.

---

### Post by ThinkBuntu on 2007-05-06
What I love most about it is the comprehensive installed application suite. I use a wide range of apps for a wide variety of tasks (off the top of my head, Web Design, programming, image editing, typical office work, browsing, P2P, and just about everything else except for video editing and gaming). I loved how it came with Wireshark, which is exactly the sort of thing I've been looking for.

---

