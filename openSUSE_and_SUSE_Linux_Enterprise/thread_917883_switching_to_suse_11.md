---
title: "switching to suse 11"
date: 2008-09-12
forum: openSUSE and SUSE Linux Enterprise
---

### Post by 7raTEYdCql on 2008-09-12
I am at present running suse 11. Switched from ubuntu 8.04. Can someone please compare the commonly used commands on ubuntu with those of linux, like:
sudo apt-get install
sudp dpg -i *.deb

I know these commands wont run because the package manager on suse is yast ans not apt.

Does suse cache the downloaded and installed rpm's

I am having a problem witht playing video files on suse?
Can someone give me a link to a tutorial on suse? Havent found many/ Unlike ubuntu.

---

### Post by Vince4Amy on 2008-09-12
Instead of apt-get install package you'd do:

```
zypper in (package name)
```

Installing RPMs:

```
rpm -ivh (package name)
```

Upgrade RPMs:

```
rpm -uvh (package name)
```

There are one click installers for restricted formats on OpenSUSE, are you using Gnome, KDE 3.5 or KDE 4?

---

### Post by Antman on 2008-09-12
> **i.mehrzad said:**
> 
I am having a problem witht playing video files on suse?
Try this 1-Click solution: [openSUSE 11 Restriced Formats]("http://opensuse-community.org/Restricted_Formats/11.0")

---

### Post by 7raTEYdCql on 2008-09-13
I am using Gnome on Open Suse. Are there any beginning manuals when you migrate to suse. I hunted all over the net for some good documentation, didnt find anything substantial.

---

### Post by sosipator on 2008-09-13
Or if you don't like the zypper, you can still install apt-get on Suse as well. 
[http://linux01.gwdg.de/apt4rpm/](http://linux01.gwdg.de/apt4rpm/)
Suse repositories support the Debian apt-tool, so you will feel just like home. Everything is the same, only the packages are rpm instead of deb.

[img]http://i.linux-bg.org/g/b-373112199shot.png#800;600[/img]

---

### Post by RedDwarf on 2008-09-13
> **i.mehrzad said:**
> I know these commands wont run because the package manager on suse is yast ans not apt.
The equivalent of APT is ZYpp. There are two (GTK/QT) YaST modules that provide a GUI to ZYpp, but they are better compared to Synaptic.
> **i.mehrzad said:**
> Does suse cache the downloaded and installed rpm's
It can do so, it's configurable.
> **i.mehrzad said:**
> I am having a problem witht playing video files on suse?
Playing video files **coded with patented codecs**. 
> **i.mehrzad said:**
> Can someone give me a link to a tutorial on suse? Havent found many/ Unlike ubuntu.
I don't think openSUSE is so different from Ubuntu. But anyway, the medias include pretty, professional edited, PDFs -> [http://download.opensuse.org/distribution/11.0/repo/oss/docu/en/](http://download.opensuse.org/distribution/11.0/repo/oss/docu/en/)
Do you need anything else not available in those PDFs or the wiki from the official page?

---

### Post by Vince4Amy on 2008-09-14
I've found zypper to be really fast. Also I prefer the Download Package 1 >Install Package 1>Download Package 2>Install Package 2 and so on instead of:

Download Package 1>Download Package 2>Install Package 1>Install Package 2

---

