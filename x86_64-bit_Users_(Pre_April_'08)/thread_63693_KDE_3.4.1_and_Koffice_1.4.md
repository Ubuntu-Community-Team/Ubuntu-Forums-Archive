---
title: "KDE 3.4.1 and Koffice 1.4"
date: 2005-09-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by mlomker on 2005-09-08
I ran across these repositories today.

KDE:

deb [ftp://ftp.kde.org/pub/kde/stable/3.4.1/kubuntu/](ftp://ftp.kde.org/pub/kde/stable/3.4.1/kubuntu/) hoary-updates main

Koffice:

deb [ftp://ftp.kde.org/pub/kde/stable/koffice-1.4/kubuntu/](ftp://ftp.kde.org/pub/kde/stable/koffice-1.4/kubuntu/) hoary-updates main

---

### Post by GreatBunzinni on 2005-09-16
[QUOTE=mlomker]I ran across these repositories today.

KDE:

deb [ftp://ftp.kde.org/pub/kde/stable/3.4.1/kubuntu/](ftp://ftp.kde.org/pub/kde/stable/3.4.1/kubuntu/) hoary-updates main

Koffice:

deb [ftp://ftp.kde.org/pub/kde/stable/koffice-1.4/kubuntu/](ftp://ftp.kde.org/pub/kde/stable/koffice-1.4/kubuntu/) hoary-updates main[/QUOTE]
KDE 3.4.2 and KOffice 1.4.1 is available. 

for KDE: 
(Check other posts)

for KOffice
deb [ftp://ftp.kde.org/pub/kde/stable/koffice-1.4.1/kubuntu/](ftp://ftp.kde.org/pub/kde/stable/koffice-1.4.1/kubuntu/) hoary-updates main

---

### Post by mlomker on 2005-09-16
[QUOTE=GreatBunzinni]KDE 3.4.2 and KOffice 1.4.1 is available. 
[/QUOTE]

Only for 32-bit ... hence my excitement when finding an upgrade for amd64.

---

### Post by Terracotta on 2005-09-18
When I update, he doesn't change anything, after adding these repos. How can I get the lastest newest (well ok, one behind the latest newest) of kde and koffice?

---

### Post by mlomker on 2005-09-18
[QUOTE=Terracotta]When I update, he doesn't change anything, after adding these repos. How can I get the lastest newest (well ok, one behind the latest newest) of kde and koffice?[/QUOTE]

I just double-checked and the sources that I posted will work with all platforms.  I assume you added those lines to /etc/apt/sources.list already (or plugged them in using Synaptic/Kynaptic).

```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by Terracotta on 2005-09-18
[QUOTE=mlomker]I just double-checked and the sources that I posted will work with all platforms.  I assume you added those lines to /etc/apt/sources.list already (or plugged them in using Synaptic/Kynaptic).

```

sudo apt-get update
sudo apt-get upgrade

```[/QUOTE]

Yup, that's what I've done, but no result whatsoever :s. But Kubuntu is behaving strange anyway these days :s.

---

### Post by mlomker on 2005-09-18
[QUOTE=Terracotta]Yup, that's what I've done, but no result whatsoever :s. But Kubuntu is behaving strange anyway these days :s.[/QUOTE]

Have Synaptic installed?  It should list the installed and latest versions that it can see in the repositories.  

I've attached my sources.list for you to take a look at.

---

### Post by Terracotta on 2005-09-19
I have the same repos for kde and koffice, and the others are the ones from the kudos faq.

---

