---
title: "cannot instal build-essential"
date: 2008-03-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by binsiram on 2008-03-23
Hi
I recently built a desktop (first time assembly) and am facing issues with sound card and video display with my nvdia chipset (MSI P6NGM mobo)

I was trying to install the nvidia latyest drivers and through some forums I have understood that I need to get basic build-install package for installing new drivers.

But strangely I ended up in issues when it was asked to insert CD. I created another CD from image  (64 bit - ubuntu 7.10) and still the same issue

 > sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev patch
Suggested packages:
  debian-keyring g++-multilib g++-4.1-multilib gcc-4.1-doc glibc-doc manpages-dev
  libstdc++6-4.1-doc diff-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev patch
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7417kB of archives.
After unpacking 31.3MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/pool/main/g/gcc-4.1/libstdc++6-4.1-dev_4.1.2-16ubuntu2_amd64.deb  Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/pool/main/g/gcc-4.1/g++-4.1_4.1.2-16ubuntu2_amd64.deb  Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/pool/main/p/patch/patch_2.5.9-4_amd64.deb  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


Any help is greatly appreciated. I am a newbie, please provide detailed suggestion...

rgds
S

---

### Post by Ehtetur on 2008-03-23
Hi binsiram... if you have a good broadband or dsl connection, you don't need to install apps/drivers from the ubuntu dvd.,, The main and restricted apps/drivers are on both the DVD and the server.

To install applications from the server (and not the DVD), you will need to edit your sources.list:
> sudo vim /etc/apt/sources.list
Add # to the line with the DVD and when done, it should look like this:
> # deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
Save the file and refresh the ubuntu repos:
> sudo apt-get update
Now try installing build-essential again... It should work :twisted:

---

### Post by binsiram on 2008-03-23
thanks a lot !!
it worked and now I could install by commenting the cdrom

---

