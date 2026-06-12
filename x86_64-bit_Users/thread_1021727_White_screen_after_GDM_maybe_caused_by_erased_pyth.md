---
title: "White screen after GDM maybe caused by erased python 2.5?"
date: 2008-12-25
forum: x86 64-bit Users
---

### Post by emmanuel3333 on 2008-12-25
:KS Hi guys!!! I  just screw again my ubuntu 8.10 . Accidentally I removed python 2.5 and 2.4. :confused: using Synaptic Package Manager. In the middle of that I was very scared, so thinking in a solution I used force quit.(Nice decision :( )Later my Macbook Pro wasn't loading GDM. I installed GDM manually. After the login there's a white screen and nothing happens. I already tried to restart x with no success. Using Recovery mode and trying to fix with dpkg the following appears;
> rm:cannot remove '/var/lib/apt/lists/partial/*': No such file or directory
rm: cannot remove '/var/cache/apt/archives/partial/*': No such file or directory
Do you want to start the upgrade?
76 packages are going to be installed
alacarte  apport  apport-gtk  apturl  at-spi  bluez-cups bluez-gnome  brasero  brltty  brltty-x11  capplets-data  compiz-fusion-plugins  compiz-fusion-plugins-main  contact-lookup-applet  akiga  eog  evince  evolution  evolution-data-server evolution-exchange  evolution-plugins evolution-webcal f-spot fast-user-switch-applet file-roller firefox firefox-3.0-gnome-support firefox-gnome-support foomatic-db-hpijs gcalctool gconf-editor gdm-guest-session gedit gnome-applets gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduis gnome-power-manager gnome-session gnome-settings-daemon gnome-terminal gnome-terminal-data gnome-user-guide hal-cups-utils hpijs hplip libdeskbar-tracker nautilus nautilus cd-burner nautilus-share python-pyatspi ubuntu desktop ubuntu docs update-manager update-notifier vinagre vino yelp

For some reason seems that I removed all those packages because my system was up to date. After that, I tried to install manually each package, also tried to 
```
# sudo apt-get update
# sudo apt-get upgrade
``` No success. The system suggest to fix it by running ```
#sudo apt-get update
```
But I have missing the update manager so I can't install It.
So, guys out there....you are the Linux gurus help me please if you wish to. I dont want to start from scratch because I have several important data on my Linux Partition and is very messy to start from zero. Also, I'm sorry for my English it's not my main language. My specs are:> Macbook Pro Santa Rosa chip
5400hd
2Gb RAM
2.4Ghz Processor
Nvidia 8600gt 256vram
Ubuntu 8.10 64 bit
Now guys you can laugh because my problem is a big one :lolflag:

---

### Post by habitu on 2008-12-31
have a similar problem with 8.10
after accidentally removing python 2.5 ubuntu starts in "terminal mode"
now I reinstalled python, but I don't know how get back to start from "desktop mode"

thx for help

---

### Post by soxs on 2008-12-31
```
sudo mkdir -p /var/lib/apt/lists/partial/
sudo mkdir -p /var/cache/apt/archives/partial
sudo apt-get upgrade
```Try this, this should fix at least the errors apout missing dirs

---

### Post by soxs on 2008-12-31
> **habitu said:**
> have a similar problem with 8.10
after accidentally removing python 2.5 ubuntu starts in "terminal mode"
now I reinstalled python, but I don't know how get back to start from "desktop mode"

thx for help

try ```
gdm start
``` from terminal

---

### Post by habitu on 2008-12-31
thanks for quick reply:)

unfortunately........

-bash: gdm command not found

and "ctrl+alt+F7" doesn't work either

---

### Post by soxs on 2008-12-31
try ```
sudo apt-get install ubuntu-desktop
```

---

### Post by habitu on 2008-12-31
Thanks...

```
sudo apt-get install ubuntu-desktop
sudo gdm install
```

..worked perfectly:D!

---

### Post by emmanuel3333 on 2009-01-02
:popcorn:Hi guys I'm gonna try your suggestions on a few days!!!:D

---

