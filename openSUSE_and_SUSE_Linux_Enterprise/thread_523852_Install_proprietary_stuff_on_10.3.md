---
title: "Install proprietary stuff on 10.3?"
date: 2007-08-12
forum: openSUSE and SUSE Linux Enterprise
---

### Post by 67GTA on 2007-08-12
I have tried the last four Open Suse releases and have liked the looks and feel, but hated Yast. I could never figure out how to install anything. With Debian based distros you have preconfigured repos with the ability to install non-open source apps from them. With Suse, I couldn't find any repos. It always wanted one of the cd's to install anything. Can someone help me understand how Suse works? How do you install something similar to Ubuntu's restricted extras for mp3,dvd,etc?

---

### Post by pbcartwright on 2007-08-12
what I did with suse was install mplayer. It installed most of the other things to make DVDs etc work.. To insall mplayer I installed smartpm, using apt-get install smartpm.
run smart update the first time and it asks you if you want to add all the repositories. If you say YES to all, then when you run smart install mplayer it will work.
I run openSUSE 10.2 on my desktop and kubuntu on my laptop.

---

### Post by 67GTA on 2007-08-12
I actually found an extra cd on the download page containing proprietary drivers, but I guess I need the proprietary repos to stay updated. This website lists the repos for 10.2. [http://www.softwareinreview.com/cms/content/view/60/](http://www.softwareinreview.com/cms/content/view/60/) Could I change them to 10.3 and still work?

---

### Post by 67GTA on 2007-08-12
So the Smart package manager will add all of the available repos? I've never used it. There is supposed to be some kind of 1-click installation for 10.3. This kind of thing is why I never stayed with Suse. Ubuntu has spoiled me:)

---

### Post by igknighted on 2007-08-13
You can try changing the 10.2 to 10.3, it depends on each repo whether or not they have upgraded yet.  SMART isn't bad, although being GTK based it looks like crap if you use KDE.  I think it might have a setup wizard that walks you through adding more repos, but I don't know if it works for 10.3 yet.  Honestly, I would use 10.2 if I were you.  I used it for several months and never had an issue.  Just (during install) choose to customize your package selection and un-check the zen linux management system, after this you should be fine.  Yast may indeed be slow at times, but it is reliable.  Adding the repo's listed on the opensuse.org pages should let you install any package available, and also keep any package available up to date if you wish (mozilla products have a repo to keep them up to date, for example).

---

### Post by 67GTA on 2007-08-13
I wound up deleting the partition. I tried adding the non-oss community repo with Yast and kept getting errors. They might not be up yet. I have 10.2 on disc. I might try it again. Suse is without a doubt the most polished and best looking distro I've tried. I really love the installer. The package management always pisses me off. After using Debian based distros for so long, every other package management system just seems ridiculously complicated. If Suse used apt/synaptic, it would be the perfect distro:)

---

### Post by dca on 2007-08-13
The only thing that bugged me was the time it takes to do a simple update that consists of three files in 10.2...   It goes to 99% completed and just sits there.  Like it's contemplating the meaning of life or something.  The polish of SuSE is incredible, though.

---

### Post by igknighted on 2007-08-13
> **67GTA said:**
> I wound up deleting the partition. I tried adding the non-oss community repo with Yast and kept getting errors. They might not be up yet. I have 10.2 on disc. I might try it again. Suse is without a doubt the most polished and best looking distro I've tried. I really love the installer. The package management always pisses me off. After using Debian based distros for so long, every other package management system just seems ridiculously complicated. If Suse used apt/synaptic, it would be the perfect distro:)

It does have apt/synaptic if you want... it might be on the DVD, otherwise after install choose "zypper install apt4rpm synaptic" or whatever suse named the packages.  Works OK.  I think SMART is a better package manager, but both work well.

---

### Post by 67GTA on 2007-08-13
Just got 10.2 installed and figured out how to add the extra repos.  I'll try to find synaptic. Right now I need to fix my xserver config. I added the ATI repo and the fglrx driver installed. I used sax to set my normal resolution and sync/refresh rates and the screen is saying out of range. Not sure what happened. Is there a dpkg-reconfigure xserver-xorg equivalent for opensuse?

---

### Post by 67GTA on 2007-08-13
Never mind, I deleted it again. I could not get booted back into a terminal to change anything. I guess I will wait a few more releases. Maybe they will simplify some of this stuff.

---

### Post by igknighted on 2007-08-14
> **67GTA said:**
> Never mind, I deleted it again. I could not get booted back into a terminal to change anything. I guess I will wait a few more releases. Maybe they will simplify some of this stuff.

The tool is sax.  You can run it graphically from Yast or you can run it as root on the CLI.  Thats a weird issue, maybe a bug with the latest ATI driver?

---

### Post by 67GTA on 2007-08-14
Well, It wasn't Suse. It is my hard drive. I got a couple of file system errors on my Kubuntu partition at boot yesterday. I ran fsck and it said it corrected some errors. When I got home today the PC was locked up, and fsck will not read any of my partitions. The hard drive light stays on constantly. I tried several live cd's and finally good old Knoppix decided to boot. I ran fsck from Knoppix with the same results.

---

