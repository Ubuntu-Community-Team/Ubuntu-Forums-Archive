---
title: "ubuntu server 7.10 Gui install"
date: 2008-03-19
forum: Za Team - South Africa
---

### Post by xooku on 2008-03-19
Hello there - 
I installed ubuntu server 7.10 and would now like to install kubuntu 7.10 for the gui. I have the kubuntu on CD (do not want to install from network) and (do not want webmin for now) or (other light gnome)
I tried the following command and several other

```
sudo apt-get install kubuntu-desktop
```

I"m getting a message that says 

Reading package lists...Done
Building dependency tree
Reading state information...Done
E: Couldn't find package kubuntu-desktop

is it necessary to enable the universe\multiverse repos, how do I do this?
taking out the comments "#" in

```
nano /etc/apt/sources.list
```

thanks

---

### Post by Jimmey on 2008-03-19
multiverse/universe repositories are repositories on the internet. 

Try editing the CDROM line in the sources.list.

---

### Post by stefanor on 2008-03-19
> **xooku said:**
> Hello there - 
Reading package lists...Done
Building dependency tree
Reading state information...Done
E: Couldn't find package kubuntu-desktop

is it necessary to enable the universe\multiverse repos, how do I do this?
thanks

It sounds like you just need to enable the *main* repository. Although I'd obviously recommend universe and multiverse too.

Here is a good, simple sources.list (I'd remove the CD entry unless you are going to be wanting to install packages from the CD rather than the internet):
```

deb http://za.archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
deb http://za.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb http://za.archive.ubuntu.com/ubuntu/ gutsy-security main restricted universe multiverse

```

---

### Post by Circus-Killer on 2008-03-20
if you planning to install kubuntu-desktop from the cd (which im not sure if its even possible), then ignore all the entries in /etc/apt/sources.list except the cdrom lines.

those are the two most important lines. make sure they are not commented out, and read correctly. once you have done that, first run:

```
sudo apt-get update
```

then:

```
sudo apt-get install kubuntu-desktop
```

the cdrom line in sources.list should read something like:

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
```

but would be slightly different for kubuntu. you need someone with a full kubuntu install of 7.10 to help give you the correct line. if no one has replied by tonight, then when i get home i will get the correct line and post it up here.

---

### Post by xooku on 2008-03-25
Hello there,

Allright got it - 

First of all I read up on the 'alternate' iso images available for download on ubuntu - live desktop images does not work - for me at least..

secondly all the commands posted in gui installation works just fine.

```
sudo apt-cdrom add

sudo apt-get update 

sudo apt-get install kubuntu-desktop
```

the sudo apt-get update updates the sources.list automatically.

wow such a simple installation..at least now I have every available image ubuntu has to offer!

Now I need to know more about common services such as domain, users, file server, mail server setup and howto, any suggestions????

thanks for the posts

---

