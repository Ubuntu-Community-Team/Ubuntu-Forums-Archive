---
title: "google earth help"
date: 2009-08-27
forum: x86 64-bit Users
---

### Post by Tadcrazio on 2009-08-27
I'm new to ubuntu..and i'm trying to get google earth.. I've done so much i dont even know what i did. I got both google earth things off the repository and i get this error message..Error: Dependency is not satisfiable: googleearth-4.3-data (= 4.3.7284.3916-0medibuntu3)

---

### Post by oldos2er on 2009-08-27
Which version of Ubuntu are you running? Do you have the Medibuntu repository enabled? [http://medibuntu.org](http://medibuntu.org)

---

### Post by Tadcrazio on 2009-08-27
I believe i do, I dont know how to check. I am running 9.04 jaunty

---

### Post by tuxxy on 2009-08-27
> **Tadcrazio said:**
> I believe i do, I dont know how to check. I am running 9.04 jaunty

To check which version you have installed open a terminal and enter this command;

```
uname -m
```

If the output is x86_64 then congratulations your running 64-bit Ubuntu :D for more OS information you can run this;

```
uname -a
```

---

### Post by Tadcrazio on 2009-08-27
yes its 64 bit

---

### Post by oldos2er on 2009-08-28
If you have Medibuntu enabled, you can run ```
sudo apt-get update && sudo apt-get install googleearth
``` in a terminal. You can install also install GE by downloading its *bin file from Google; that is slightly more complicated.

---

### Post by Tadcrazio on 2009-08-28
i'm almost positive i have medibuntu enabled but when i type in the command you gave me i get this.. E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)

---

### Post by Tadcrazio on 2009-08-28
ok, well i tried getting it from the .bin file it installed and started but when it starts i get this message.

---

### Post by Tadcrazio on 2009-08-28
okay i tried adding an attachment..It says it finds and error with the authentication it says it could be my firewall or internet connection.. as far as i know i dont have a firewall and well i am online..

---

### Post by oldos2er on 2009-08-28
Let's see if we can fix your sources.list. Can you please post the output of this command?
```
cat /etc/apt/sources.list
```

---

### Post by Tadcrazio on 2009-08-28
heres the deal, i fooled around i needed to install a file that didnt install correctly, But everytime i open googleearth it just flashes and wont display the globe and eventually crashes.

Here is what i got anyways
anthony@anthony-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) jaunty main restricted
deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) jaunty-updates main restricted
deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) jaunty universe
deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) jaunty universe
deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) jaunty-updates universe
deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) jaunty multiverse
deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) jaunty multiverse
deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) jaunty-updates multiverse
deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) jaunty-security main restricted
deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) jaunty-security main restricted
deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) jaunty-security universe
deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) jaunty-security universe
deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) jaunty-security multiverse
deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) jaunty-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main
#deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty

---

### Post by oldos2er on 2009-08-28
Run this command
```
gksu gedit /etc/apt/sources.list
```
and on the last line, add a space between # and deb-src so that it looks like
# deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty
 then save and exit. Run
```
sudo apt-get update
```
and it should work without errors.

 Googleearth requires video drivers with 3d hardware acceleration; what you're describing sounds like a video driver problem.

---

### Post by Tadcrazio on 2009-08-28
after the last command i got this after it read everything..
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5
W: You may want to run apt-get update to correct these problems

It still flashes..Google Earth worked fine when i used it on this computer with windows..How do i know if something is wrong with my video driver..

---

### Post by theZoid on 2009-08-29
> **Tadcrazio said:**
> after the last command i got this after it read everything..
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5
W: You may want to run apt-get update to correct these problems

It still flashes..Google Earth worked fine when i used it on this computer with windows..How do i know if something is wrong with my video driver..

You got the repo entered in sources.list for Chromium but haven't installed the public key...that's the error.

If you enable Medibuntu...and install GE 4.3 from Synaptic, you shouldn't have any problems...I don't.

What vid card do you have?  Have you installed the proprietary drivers for say, Nvidia or ATI?

---

### Post by Tadcrazio on 2009-08-29
its an ati radeon, i may not have installed them correctly because i have honestly no idea what to do on this.. First time on linux just trying to work with it..

---

### Post by luke0927 on 2009-08-30
Bump....
wit
I have a problem too...I can't get it to work on my desk top or laptop both with integrated intal/ATI cards....GE will launch but the globe never displays and freezes up....I installed it from the repostitory...with the command
sudo apt-get update && sudo apt-get install googleearth

---

### Post by oldos2er on 2009-08-30
> **Tadcrazio said:**
> its an ati radeon, i may not have installed them correctly because i have honestly no idea what to do on this.. First time on linux just trying to work with it..

 Some older ATI video cards no longer are supported in 9.04; only the slower 2D drivers are available for them. Check System, Administration, Hardware Drivers; if nothing is there, you may be out of luck.

---

