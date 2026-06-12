---
title: "rar"
date: 2006-03-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by maxdevis on 2006-03-15
what do i need to install so i can read rar files?

---

### Post by stoeptegel on 2006-03-15
unrar nonfree, i think they are in multiverse

---

### Post by maxdevis on 2006-03-15
but apt-get says its unavailable

---

### Post by stoeptegel on 2006-03-15
That's true, you either have to enable the multiverse line in /etc/apt/sources.list by removing the # comment out in the beginning, or if there's no multiverse in this file configured yet you have to add this manually.

Here's some overall information
[https://wiki.ubuntu.com/AddingRepositoriesHowto?action=show&redirect=HowToEnableTheMultiverseRepositoryInUbuntu](https://wiki.ubuntu.com/AddingRepositoriesHowto?action=show&redirect=HowToEnableTheMultiverseRepositoryInUbuntu)

If you have questions about that just ask away.

---

### Post by maxdevis on 2006-03-15
i thought it was enabled
this is my sources.list

[QUOTE=sources]
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012)]/ breezy main restricted


deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
[/QUOTE]

---

### Post by stoeptegel on 2006-03-15
I guess you're missing "multiverse" at the end of your 
deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy universe
line

after the modification do a 
# apt-get update 
first and then apt-get install unrar-nonfree

---

### Post by maxdevis on 2006-03-15
still doesn't work.
i presume you can read dutch so i don't need to translate this?

[QUOTE=terminal]
michiel@ibook:~$ sudo apt-get install unrar-nonfree
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
Pakket unrar-nonfree is niet beschikbaar, hoewel er naar verwezen wordt door
een ander pakket. Mogelijk betekent dit dat het pakket ontbreekt,
verouderd is, of enkel beschikbaar is van een andere bron
E: Pakket unrar-nonfree heeft geen installeerbare kandidaat
michiel@ibook:~$
[/QUOTE]

---

### Post by maxdevis on 2006-03-15
it's ok!
as you said something with the multiverse!

thanks!

---

### Post by stoeptegel on 2006-03-15
Yes i can read dutch ;)

What i would try in your situation is backup the sources.list
sudo cp /etc/apt/sources.list /etc/apt/sources.list.OLD.15.03.06.standard

get a fresh one from source-o-matic
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

repace that renegated file in /etc/apt/
sudo mv /whereyousavedthefile  etc/apt/sources.list

and do again a apt-get update & apt-get install unrar-nonfree


When this doesn't work you can trash you sources.list, revert to the old one without danger and wait for someone else with a better solution

---

### Post by stoeptegel on 2006-03-15
alrighdy :)

---

