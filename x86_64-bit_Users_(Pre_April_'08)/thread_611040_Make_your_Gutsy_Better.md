---
title: "Make your Gutsy Better"
date: 2007-11-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by damvcoool on 2007-11-12
I have created this little script to add some Repositories to Gutsy.
this will make gutsy much more fun, you will have tons of new applications to choose.

please comment on it.


```

#!/bin/sh
# Seveas’ packages

wget http://mirror.ubuntulinux.nl/1135D466.gpg
sudo apt-key add 1135D466.gpg
rm -fr 1135D466.gpg

sudo echo deb http://mirror.ubuntulinux.nl gutsy-seveas all >> seveas.list
sudo echo deb-src http://mirror.ubuntulinux.nl gutsy-seveas all >> seveas.list
sudo cp seveas.list /etc/apt/sources.list.d/seveas.list
rm seveas.list 1135D466.gpg

# Bleeding edge wine packages
wget http://wine.budgetdedicated.com/apt/387EE263.gpg
sudo apt-key add 387EE263.gpg
rm 387EE263.gpg
sudo wget http://wine.budgetdedicated.com/apt/...t.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list

# Penguin Liberation Front

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list

# Skype packages

#echo deb http://download.skype.com/linux/repos/debian/ stable non-free >> /etc/apt/sources.list.d/skype.list
#sudo cp skype.list /etc/apt/sources.list.d/skype.list
#rm skype.list

# Debuntu Ubuntu edgy packages

# GPG Key: http://repository.debuntu.org/GPG-Key-chantra.txt

wget http://repository.debuntu.org/GPG-Key-chantra.txt
sudo apt-key add GPG-Key-chantra.txt
rm GPG-Key-chantra.txt
echo deb http://repository.debuntu.org/ gutsy multiverse >> debuntu.list
echo deb-src http://repository.debuntu.org/ gutsy multiverse >> debuntu.list
sudo cp debuntu.list /etc/apt/sources.list.d/debuntu.list
rm debuntu.list


# Geole Repositories
wget http://ubuntu.geole.info/dists/feisty/Release.gpg
sudo apt-key add Release.gpg
rm Release.gpg
echo deb http://ubuntu.geole.info/ gutsy universe multiverse >> geolebuntu.list
echo deb-src http://ubuntu.geole.info/ gutsy universe multiverse >> geolebuntu.list
echo deb http://ubuntu.geole.info/ gutsy-backports main restricted universe multiverse >> geolebuntu.list
echo deb-src http://ubuntu.geole.info/ gutsy-backports main restricted universe multiverse >> geolebuntu.list
sudo cp geolebuntu.list /etc/apt/sources.list.d/geolebuntu.list
rm geolebuntu.list



# iced-tea updates
wget http://apt.mediatomb.cc/key.asc -O- -q | sudo apt-key add -
echo deb http://people.ubuntu.com/~doko/ubuntu/ gutsy/ >> people_ubuntu.list
echo deb-src http://people.ubuntu.com/~doko/ubuntu/ gutsy/ >> people_ubuntu.list
sudo cp people_ubuntu.list /etc/apt/sources.list.d/people_ubuntu.list
rm people_ubuntu.list


# Mediatomb
echo deb http://apt.mediatomb.cc/ feisty main >> mediatomb.list
echo deb-src http://apt.mediatomb.cc/ feisty main >> mediatomb.list
sudo cp mediatomb.list /etc/apt/sources.list.d/mediatomb.list
rm mediatomb.list


# Automatix Reporitory

wget http://www.getautomatix.com/keys/automatix2.key
gpg --import automatix2.key
gpg --export --armor E23C5FC3 | sudo apt-key add -
rm automatix2.key
echo deb http://www.getautomatix.com/apt gutsy main >> automatix.list
sudo cp automatix.list /etc/apt/sources.list.d/automatix.list
rm automatix.list


## Avant Window Navigator and Exaile
wget http://download.tuxfamily.org/syzygy42/reacocard.asc
sudo apt-key add reacocard.asc
rm reacocard.asc
echo deb http://download.tuxfamily.org/syzygy42 gutsy all >> syz.list
echo deb-src http://download.tuxfamily.org/syzygy42 gutsy all >> syz.list
sudo cp syz.list /etc/apt/sources.list.d/syz.list
rm syz.list

```

[COLOR="Red"][SIZE="5"]NOTE: If you use this don't expect a smooth upgrade to Hardy[/SIZE][/COLOR]

---

### Post by uaeB on 2007-11-12
Hello,

The wget command to fetch the sources list for Wine is truncated.

Just a suggestion but you may want to provide a brief summary as to what each of the repo's are provided and / or what they provided or how they add value to the users experience.

---

