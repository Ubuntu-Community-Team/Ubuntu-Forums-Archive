---
title: "Added &quot;opera&quot; repository, cant find in Synaptic. 8.10 x64"
date: 2009-02-19
forum: x86 64-bit Users
---

### Post by Mugzilla on 2009-02-19
Added "opera" repository, cant find it to install it in Synaptic...
I just did a fresh install of 8.10 64 bit on an IBM x61s. I have had great success w/ 8.10 64 bit and opera on this machine in the past.

Here is the dilemma:

I added the repository Opera recommends to install their browser.

**deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner**

I also added this repository:
[B]
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) intrepid non-free[/B]

I added the Opera GPG key for the 1st repo.

When I search in Synaptic for OPERA, nothing shows up! I have installed opera using the shell

sudo apt-get update
sudo apt-get install opera

The conundrum: Opera is installed. It shows up under applications ->internet. However, OPERA won't connect to the internet! Firefox works just fine.

What I want to know:
[B][SIZE="2"]
#1 How can I get OPERA to show up in synaptic pkg manager?
#2 How can I get opera to connect to the internet?
#3 During install, opera recommended the following packages be installed also:[/SIZE][/B]

pdf-npapi-plugin
djvulibre-plugin
mozilla-acroread
sun-java6-jre

sun-java5-jre
java-gcj-compat
xine-plugin
gxineplugin
mplayerplug-in

kaffeine-mozilla
mozilla-mplayer
mozilla-helix-player
gecko-mediaplayer

mozplugger plugger mozilla-bonobo

Here is the output of [B]gksudo gedit /etc/apt/sources.list
[/B]

[INDENT]deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid restricted main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates restricted main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security restricted main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid universe multiverse
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) intrepid non-free[/INDENT]

---

### Post by Mugzilla on 2009-02-19
ADDITIONAL CLARIFICATION:

I am able to install opera by DLing straight from Opera's website.  However, after it installs, the browser is NOT able to connect to the internet, does not show up in ADD/REMOVE programs, and ALSO does not show up in Synaptic pkg mgr (So I am STILL unable to add all of the recommended packages.).

---

### Post by Moop on 2009-02-19
I've never bothered with adding a repository for Opera. Downloading the deb and installing from that works fine. [http://www.opera.com/download/](http://www.opera.com/download/)  

Are you installing the 64bit version?

---

### Post by vasilis34 on 2009-03-05
Moop, I have installed the latest opera from their website and install it on Ubuntu Intrepid 64bit but I have a problem with the totem plugin. The plugin is detected, when running opera from terminal like "opera -debugplugin" I see the plugin initiated and no error messages but no streaming video or audio is played. The totem-plugin doesn't even show up. Does it work on your machine?

---

