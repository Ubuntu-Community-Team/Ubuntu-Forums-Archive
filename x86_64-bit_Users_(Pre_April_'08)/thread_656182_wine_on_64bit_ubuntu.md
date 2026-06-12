---
title: "wine on 64bit ubuntu"
date: 2008-01-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by slopis on 2008-01-02
well ppl, iam noob noob to linux stuff. But i wanted to try it out (and if like, learn it as pro :D).so i instaled linux on 2nd pc i had.

So the problem is, i cannt get wine on it. i did all upgrades up to version 7.10. i found instructions at wineHQ. and nothing helps to install it.
so   here is all terminal give me:

user@machine:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
        Depends: ia32-libs (>= 1.6) but it is not installable
E: Broken packages


any sugestions?

---

### Post by Yellow Pasque on 2008-01-02
The first thing I'd do is make sure the proper sources were enabled, so go to System -> Administration -> Software Sources and make sure everything on the first tab is checked. You can also double-check on the second tab that you have the proper links to WineHQ.

If all is kosher there, I'd look into getlibs. [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by Zafrusteria on 2008-01-02
looks like you missed off a few steps from the WineHQ page if all you did was the apt-get line. :-)

If you follow the instructions on the Wine for Ubuntu page ([http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb). It should work like a charm.

You need to do a few more things than just the install step though.
add the repository's key to your system's list of trusted APT keys
add the repository to your system's list of APT sources:
Update the apt list
and finally the install.

The other option is to simply install Wine with Synaptic, (System->Aministration->synaptic), search for 'wine'. It will be a slightly older version but will work.

You could also look at your settings in Software Sources. Not sure but you may need the universe and multiverse options ticked.  Remember to make a note of how they are set before playing around with them. :-)

---

### Post by slopis on 2008-01-02
> **Zafrusteria said:**
> looks like you missed off a few steps from the WineHQ page if all you did was the apt-get line. :-)

If you follow the instructions on the Wine for Ubuntu page ([http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb). It should work like a charm.


well i did all what was sad  in that web, and no result

but THX Temüjin. it helped.

---

### Post by Kilz on 2008-01-02
> **slopis said:**
> The following packages have unmet dependencies:
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
        Depends: ia32-libs (>= 1.6) but it is not installable
E: Broken packages


any sugestions?

Please open up Synaptic and search for ia32-libs. Tell me what version is available.

---

### Post by slopis on 2008-01-02
> **Kilz said:**
> Please open up Synaptic and search for ia32-libs. Tell me what version is available.
well all that you sad to do is like chines ABC for me :D. so please be kind and write the same like for total dummy :D

edit: well i found it :D in table under instaled  version is vriten 2.1ubuntu3

---

### Post by Kilz on 2008-01-02
> **slopis said:**
> well all that you sad to do is like chines ABC for me :D. so please be kind and write the same like for total dummy :D

edit: well i found it :D in table under instaled  version is vriten 2.1ubuntu3

Please open up a terminal, type in ```
sudo apt-get install -f
``` , lets see if we can get the broken packages fixed.

---

### Post by slopis on 2008-01-02
> **Kilz said:**
> Please open up a terminal, type in ```
sudo apt-get install -f
``` , lets see if we can get the broken packages fixed.

zabaks@meesls:~$ sudo apt-get install -f
[sudo] password for zabaks:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
zabaks@meesls:~$

---

### Post by Kilz on 2008-01-02
> **slopis said:**
> zabaks@meesls:~$ sudo apt-get install -f
[sudo] password for zabaks:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
zabaks@meesls:~$

Can you please post the contents of the /etc/apt/sources.list file. Right click on the file and open it with the text editor, then copy/paste it in.

---

### Post by slopis on 2008-01-03
deb [http://lv.archive.ubuntu.com/ubuntu/](http://lv.archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
deb-src [http://lv.archive.ubuntu.com/ubuntu/](http://lv.archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://lv.archive.ubuntu.com/ubuntu/](http://lv.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse
deb-src [http://lv.archive.ubuntu.com/ubuntu/](http://lv.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://lv.archive.ubuntu.com/ubuntu/](http://lv.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://lv.archive.ubuntu.com/ubuntu/](http://lv.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://lv.archive.ubuntu.com/ubuntu/](http://lv.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://lv.archive.ubuntu.com/ubuntu/](http://lv.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by Kilz on 2008-01-03
Open a terminal. Use ```
gksudo gedit /etc/apt/sources.list
``` to open the list in an editor that can save changes. Add these lines. You can do it at the bottom of the file.

```
deb [http://lv.archive.ubuntu.com/ubuntu/](http://lv.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://lv.archive.ubuntu.com/ubuntu/](http://lv.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://lv.archive.ubuntu.com/ubuntu/](http://lv.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://lv.archive.ubuntu.com/ubuntu/](http://lv.archive.ubuntu.com/ubuntu/) gutsy multiverse
```

Save the file, then ```
sudo apt-get update
```
then
```
sudo apt-get install wine
```

---

### Post by Yellow Pasque on 2008-01-03
It looks like he/she already has those enabled in the first two lines, or do they need to be listed individually?

---

### Post by Kilz on 2008-01-03
> **Temüjin said:**
> It looks like he/she already has those enabled in the first two lines, or do they need to be listed individually?

It cant hurt to try, the packages that he the error says have no candidate are in the universe.

---

