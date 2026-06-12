---
title: "Multiple problems installing K3b 1.0 on Kubuntu 6.10 64bit"
date: 2007-03-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by derGhostrider on 2007-03-24
Hello!

I downloaded K3b 1.0 from [www.k3b.org](www.k3b.org) and followed the instructions to install it: [http://k3b.plainblack.com/installation](http://k3b.plainblack.com/installation)

After several tries and installation of some missing packages ./configure still stops with an error. It can't find the KDEheaders and requires the --prefix=/... option that has to contain the path to the KDEheaders.

The problem: I **cannot** install the kdebase-dev package. :(

> 
ghostrider@Opteron:~$ sudo apt-get install kdebase-dev
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut
Reading state information... Fertig
Einige Pakete konnten nicht installiert werden. Das kann bedeuten, dass Sie eine unmögliche Situation angefordert haben oder dass, wenn Sie die instabile Distribution verwenden, einige erforderliche Pakete noch nicht kreiert oder aus Incoming herausbewegt wurden.

Da Sie nur eine einzige Operation angefordert haben ist es sehr wahrscheinlich, dass das Paket einfach nicht installierbar ist und eine Fehlermeldung über dieses Paket erfolgen sollte.
Die folgenden Informationen helfen Ihnen vielleicht, die Situation zu lösen:

Die folgenden Pakete haben nichterfüllte Abhängigkeiten:
  kdebase-dev: Hängt ab: kdelibs4-dev (>= 4:3.5.3) soll aber nicht installiert werden
E: Kaputte Pakete


If I try spt-get install kdelibs4-dev it shows almost the same but hints to a problem with libasound2-dev.

apt-get install libasound2 tells me that I already have the newest version.
When I try to use "apt get install libasound2-dev" the following message occurs:
> 
...
Die folgenden Pakete haben nichterfüllte Abhängigkeiten:
  libasound2-dev: Hängt ab: libasound2 (= 1.0.11-7ubuntu3) aber
1.0.13-1 soll installiert werden
E: Kaputte Pakete 
depends on libasound2 (=1.0.11-7ubuntu3) but 1.0.12-1 shall be installed.

Here is a screenshot of the adept-error if I try to install kdebase-dev:
[http://www.derghostrider.de/photos/ZERSTOEREN.png](http://www.derghostrider.de/photos/ZERSTOEREN.png)

I have all software at the latest version. apt-get update and apt-get upgrade can't find anything to update/upgrade at the moment.


To sum it up:
- I need the KDEheaders to compile k3b.
- I can't install kdebase-dev.
- I can't install libasound2-dev because there seems to be some strange conflict between the versions of libasound2 and libasound2-dev.



HELP, please! ... If you need further information then let me know.

---

### Post by Kilz on 2007-03-24
> **derGhostrider said:**
> Hello!

I downloaded K3b 1.0 from [www.k3b.org](www.k3b.org) and followed the instructions to install it: [http://k3b.plainblack.com/installation](http://k3b.plainblack.com/installation)

After several tries and installation of some missing packages ./configure still stops with an error. It can't find the KDEheaders and requires the --prefix=/... option that has to contain the path to the KDEheaders.

The problem: I **cannot** install the kdebase-dev package. :(



If I try spt-get install kdelibs4-dev it shows almost the same but hints to a problem with libasound2-dev.

apt-get install libasound2 tells me that I already have the newest version.
When I try to use "apt get install libasound2-dev" the following message occurs:

depends on libasound2 (=1.0.11-7ubuntu3) but 1.0.12-1 shall be installed.

Here is a screenshot of the adept-error if I try to install kdebase-dev:
[http://www.derghostrider.de/photos/ZERSTOEREN.png](http://www.derghostrider.de/photos/ZERSTOEREN.png)

I have all software at the latest version. apt-get update and apt-get upgrade can't find anything to update/upgrade at the moment.


To sum it up:
- I need the KDEheaders to compile k3b.
- I can't install kdebase-dev.
- I can't install libasound2-dev because there seems to be some strange conflict between the versions of libasound2 and libasound2-dev.



HELP, please! ... If you need further information then let me know.

[You may want to look at this repository,]("http://packages.czessi.org/en/edgy/kde/") it has a k3b 1.0 deb file

---

### Post by derGhostrider on 2007-03-25
Thanks for the link but I'll try to fix my problem manually at first before I give up and get a package.
I already downloaded the packages (packages.ubuntu.com) that were listed to make trouble. Next to do: I will unpack them into their corresponding folders and try again. Maybe this will do the job already. If this won't work I may try that k3b package.

If there is someone else who knows how to solve my problem in a more elegant way: Please post!

---

### Post by Kilz on 2007-03-25
> **derGhostrider said:**
> Thanks for the link but I'll try to fix my problem manually at first before I give up and get a package.
I already downloaded the packages (packages.ubuntu.com) that were listed to make trouble. Next to do: I will unpack them into their corresponding folders and try again. Maybe this will do the job already. If this won't work I may try that k3b package.

If there is someone else who knows how to solve my problem in a more elegant way: Please post!

If you manually unpack and copy in files that refuse to install because of requirements you may make your system unstable.

---

### Post by derGhostrider on 2007-03-25
> **Kilz said:**
> If you manually unpack and copy in files that refuse to install because of requirements you may make your system unstable.

OK... How can I solve the problem that I can't install KDEbase-dev, kdelibs4-dev, libasound2-dev?

---

### Post by patrickfromspain on 2007-03-25
make sure you have the deb-src repos uncommented in your /etc/apt/sources.list file. If they are commented out, uncomment them, save the file and then, in a terminal:

sudo apt-get update
sudo apt-get build-dep k3b and then try to compile k3b 1.0. Worked fine for me in feisty, should be the same in edgy/dapper

---

### Post by derGhostrider on 2007-03-25
> **patrickfromspain said:**
> make sure you have the deb-src repos uncommented in your /etc/apt/sources.list file. If they are commented out, uncomment them, save the file and then, in a terminal:

sudo apt-get update
sudo apt-get build-dep k3b and then try to compile k3b 1.0. Worked fine for me in feisty, should be the same in edgy/dapper

That's somehow compareable to the solution that was suggested before. When I started my journey to install k3b there was no deb package available... I think that I already uncommented most of the sources but I'll check that and try this way first. MAYBE it will show a dependency that has not been solved until now. Thanks for the reply. I'll report back in a few hours if it helped or not...

-------------------- 
UPDATE:

My sources.list looks like this:
> 
*:/etc/apt$ cat sources.list

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy-backports main restricted univese multiverse
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy-backports main restricted uiverse multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
# deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
# deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main


I did what you suggested above but it finished with the following error:
> 
:~$ sudo apt-get build-dep k3b
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut
Reading state information... Fertig
E: Build-Abhängigkeit für k3b konnte nicht erfüllt werden.

"Could not fullfill the depencies for k3b."

Do I have to add other sources?

---

### Post by patrickfromspain on 2007-03-26
I'd try uncommenting the edgy-security repos, both deb and deb-src.

---

### Post by derGhostrider on 2007-03-26
I SOLVED IT!!! \\:D/

The additional sources did not solve the problem.

Looking back from now it was simple...

After I tried to unpack the files (yes I remember your comment about the stability issues but after I tried EVERYTHING else it was the last chance...) the configure stopped a little bit later with a new error message that the important program "mcopil" (or something like that) was still missing.

I tried to find the file on packages.ubuntu.com and packages.debian.org. => I found it! (It's part of libarts-dev)
The "apt-get install libarts-dev" installed it without problems but did also detect the not correct installed kdebase-dev and removed the files that I unpacked before. :-/ *sigh*

But then I had an idea: "When I found this missing mcopil file I should be able to find another libasound2-version that fits to the libasound2-dev package. It's just another revision than the already installed one."
I searched for it and found it in the required version. Downloaded the file, dpkg --install libasound2_1.0.13-2_amd64.deb
=> the upgrade finished successfully! :grin:

Just 4 commands later...
apt-get build-dep kde4lib-dev
apt-get install kde4lib-dev
apt-get build-dep kdebase-dev
apt-get install kdebase-dev
... my system was bloated with about 500MB of new stuff.

But now the ./configure finished successfully!

I just started the compilation with make... takes astonishing long to finish... :-\"
Maybe a dual Opteron 246 with 4GB memory is not enough.

Thanks for your help...

------------
Edit: The compilation and "make install" finished successfully and I can start k3b. It displays 1.0 as version. Success!

BTW: Is there a way to close this thread or mark it as "solved"?

---

