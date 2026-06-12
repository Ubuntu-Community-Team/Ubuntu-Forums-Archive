---
title: "OpenSUSE KDE 4 Repo Change"
date: 2008-02-08
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Incense on 2008-02-08
I just wanted to send this down to anyway who has KDE 4 installed on openSUSE. The KDE 4 repos have changed. See below for more info.

[http://lists.opensuse.org/opensuse-kde/2008-01/msg00079.html]("http://lists.opensuse.org/opensuse-kde/2008-01/msg00079.html")

> Hi,

given that we have finally decided on a new repository layout, this is how it
looks like:

KDE:KDE4:STABLE:Desktop
- only the bare desktop. it is also the repository to build against in your
home project if you want to build your own apps. so it replaces the PLATFORM
repository.

KDE:KDE4:STABLE:Extra-Apps
- addons that are released independently from KDE (amarok, koffice, etc)
and maintained by Novell employees (via e.g. openSUSE Factory)

KDE:KDE4:STABLE:Community
- anything else

the same layout exists for UNSTABLE (e.g. KDE 4.1 snapshots):

KDE:KDE4:UNSTABLE:Desktop
KDE:KDE4:UNSTABLE:Extra-Apps
KDE:KDE4:UNSTABLE:Community


the 3 repositories are also duplicated as backports, which will contain the
some of the applications, if they compile against the distro version of Qt,
kdelibs and kdebase-runtime. This way you don't have to update your whole KDE
just to get a new e.g. amarok or digikam.

KDE:KDE4:Backports:Desktop
KDE:KDE4:Backports:Extra-Apps
KDE:KDE4:Backports:Community


The other previously existing KDE4 related repositories under KDE: prefix have
already vanished or will disappear in the near future.


Greetings,
Dirk

---

### Post by snakeeyes on 2008-02-08
thanks

---

### Post by snakeeyes on 2008-02-08
hey can I just go into community repos and add these?

---

### Post by Incense on 2008-02-08
I don't think the community repos has a KDE 4 entry. If you don't already have KDE 4 installed, I think the one click install is the way to go. You get the new repo's plus all the packages you need to run KDE 4. 

 [[IMG]http://files.opensuse.org/opensuse/en/d/dd/Kde4-ymp.png[/IMG]]("http://download.opensuse.org/repositories/KDE:/KDE4:/STABLE:/Extra-Apps/openSUSE_10.3/KDE4-DEFAULT.ymp")

If you already have KDE 4 installed, you can still use the one click to subscribe to the repos, and update your packages. You would then need to go into your Software Repos under YaST and remove the old ones. You can also just add them by selecting SPECIFY URL (under software repos) and typing in the following under URL

[http://download.opensuse.org/repositories/KDE:/KDE4:/STABLE:/Desktop/openSUSE_10.3/](http://download.opensuse.org/repositories/KDE:/KDE4:/STABLE:/Desktop/openSUSE_10.3/)

Repeat with this URL

[http://download.opensuse.org/repositories/KDE:/KDE4:/STABLE:/Extra-Apps/openSUSE_10.3/](http://download.opensuse.org/repositories/KDE:/KDE4:/STABLE:/Extra-Apps/openSUSE_10.3/)

Be sure to delete the old KDE 4 repo, then run an update and you'll be set. Cheers.

---

### Post by Antman on 2008-02-08
> **Incense said:**
> I don't think the community repos has a KDE 4 entry. If you don't already have KDE 4 installed, I think the one click install is the way to go. You get the new repo's plus all the packages you need to run KDE 4. 

 [[IMG]http://files.opensuse.org/opensuse/en/d/dd/Kde4-ymp.png[/IMG]]("http://download.opensuse.org/repositories/KDE:/KDE4:/STABLE:/Extra-Apps/openSUSE_10.3/KDE4-DEFAULT.ymp")

If you already have KDE 4 installed, you can still use the one click to subscribe to the repos, and update your packages. You would then need to go into your Software Repos under YaST and remove the old ones. You can also just add them by selecting SPECIFY URL (under software repos) and typing in the following under URL

[http://download.opensuse.org/repositories/KDE:/KDE4:/STABLE:/Desktop/openSUSE_10.3/](http://download.opensuse.org/repositories/KDE:/KDE4:/STABLE:/Desktop/openSUSE_10.3/)

Repeat with this URL

[http://download.opensuse.org/repositories/KDE:/KDE4:/STABLE:/Extra-Apps/openSUSE_10.3/](http://download.opensuse.org/repositories/KDE:/KDE4:/STABLE:/Extra-Apps/openSUSE_10.3/)

Be sure to delete the old KDE 4 repo, then run an update and you'll be set. Cheers.

I've tried that link on my 10.3 virtuakbox install and get dependency conflicts... I'll try to resolve them and continue on.

---

### Post by snakeeyes on 2008-02-08
emergency, how do u restart the kde4 panel, I don't have any idea where it went

---

### Post by Incense on 2008-02-08
> **snakeeyes said:**
> emergency, how do u restart the kde4 panel, I don't have any idea where it went

```
ALT + F2 + plasma
```

---

### Post by Incense on 2008-02-08
> **Antman said:**
> I've tried that link on my 10.3 virtuakbox install and get dependency conflicts... I'll try to resolve them and continue on.

That's no good mate. You may just want to update the repos manually if you don't resolve them properly. Good luck.

---

### Post by snakeeyes on 2008-02-08
Plasma is working its just the bar thats gone.

---

### Post by Incense on 2008-02-08
> **snakeeyes said:**
> Plasma is working its just the bar thats gone.

Well, the panel is a plasmoid, so if you do a killall plasma, then alt + F2 + plasma it should bring it back. Not too sure otherwise. You can always do an alt + f2 + kicker so you can at least get that going.

---

