---
title: "Install WINE via terminal wants to remove packages"
date: 2019-08-03
forum: Wine
---

### Post by DougieFresh4U on 2019-08-03
Have been trying to install WINE but it wants to remove packages that
I think are vital to system. This is using terminal.
When I try installing via Synaptic it wants to remove many many many packages.
Could use a little direction please.

```
The following additional packages will be installed:
  fonts-wine libwine wine64
Suggested packages:
  ttf-mscorefonts-installer q4wine winbind winetricks playonlinux wine-binfmt
  dosbox exe-thumbnailer | kio-extras wine64-preloader
Recommended packages:
  wine32
The following packages will be REMOVED:
  libsasl2-modules ubuntu-budgie-desktop ubuntu-desktop ubuntu-desktop-minimal
The following NEW packages will be installed:
  fonts-wine libwine wine wine64
0 upgraded, 4 newly installed, 4 to remove and 0 not upgraded.
Need to get 24.0 MB of archives.
After this operation, 229 MB of additional disk space will be used.
Do you want to continue? [Y/n] 


```

---

### Post by mastablasta on 2019-08-05
that is very odd. why would it need to remove Ubuntu -desktop?!?

what happens if you do try to install it via software center?

---

### Post by Holger_Gehrke on 2019-08-07
The three *-desktop files are empty except for a few documentation files. Everything that's installed through them gets pulled in as dependencies. 'libsasl2-modules' is one of the dependencies of all three of them. Check the output of 'apt show' for wine and the packages wine pulls in as dependencies, especially the fields 'Conflicts: ...' and 'Breaks:...'. There's probably a conflict between one of them and 'libsasl2-modules'. So removing that package breaks the *-desktop packages and they get removed. Synaptic probably does the equivalent of 'apt autoremove' and cleans out the dependencies of the *-desktop packages - unless these dependencies are marked as manually installed. 
The big question is: Why is there a conflict between wine and the modules of cyrus sasl (Simple Authentication and Security Layer). On my system (Xubuntu 18.04, wine from the standard repos) there's no such conflict, but then there's no real package named 'wine' on 18.04, that's a virtual package provided by either 'wine-stable' or 'wine-development'.
So we could use a bit of additional information: what Ubuntu version and flavour are you running, what repositories and PPAs are set up in your /etc/apt/sources.list and /etc/apt/sources.list.d/* ?

Holger

---

