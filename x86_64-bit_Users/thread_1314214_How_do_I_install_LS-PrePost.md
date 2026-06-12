---
title: "How do I install LS-PrePost"
date: 2009-11-04
forum: x86 64-bit Users
---

### Post by bondmatt on 2009-11-04
I am currently running CAELinux 2009 which is Ubuntu 8.04LTS (64 bit) with a ton of open source engineering software installed and configured. There is a program called LS PRE-POST I am interested in installing but it is not in the repositories. This program is used to create 3D models for simulations of impacts (ie. car crashes). There are all kinds of linux installation files available on the developers website but I dont see Ubuntu. I also looked for debian figuring that might work (would it?) but I did not recognize any of the names. I have added the list of files below. Will any of these work? Any thoughts on using Wine for such a program?

Thanks in advance,
- Matt Bondy

File:lsprepost2_4_amd64_suse91.gz      7600 KB      
File:lsprepost2_4_amd64_suse92.gz     8360 KB     
File:lsprepost2_4_amd64_suse93.gz     8430 KB     
File:lsprepost2_4_amd64_suse93_mesa.gz     14409 KB     
File:lsprepost2_4_linux64_centos39.gz     13473 KB     
File:lsprepost2_4_linux64_centos4.gz     9010 KB     
File:lsprepost2_4_linux64_centos4_mesa.gz     14905 KB     
File:lsprepost2_4_linux64_centos5.gz     8667 KB     
File:lsprepost2_4_linux64_centos5_mesa.gz     15426 KB     
File:lsprepost2_4_linux64_rhe3.gz     9026 KB     
File:lsprepost2_4_linux64_sles10.gz     14704 KB     
File:lsprepost2_4_linux64_suse101.gz     8962 KB     
File:lsprepost2_4_linux64_suse102.gz     9145 KB     
File:lsprepost2_4_linux64_suse103.gz     8794 KB     
File:lsprepost2_4_linux64_suse110.gz     9109 KB     
File:lsprepost2_4_linux64_suse93.gz     8430 KB     
File:lsprepost2_4_linux64_suse93_mesa.gz     14409 KB     
File:lsprepost2_4_wxlinux64_centos5.gz     21648 KB     
File:lsprepost2_4_wxlinux64_suse102.gz     11526 KB

---

### Post by bford16 on 2009-11-04
It looks lke there is a version available for openSUSE 11, in RPM format.  You can convert RPMs to Debian-style 'deb' packages with the 'alien' program.  You may be able to use this software to install the program on your Ubuntu system.  Here is the path to the openSuSe 11 file: <ftp://ftp.lstc.com/outgoing/lsprepost/3.0/linux64/lsprepost-3.0-opensuse11.x86_64.rpm>  There is a README file on the download parent page, with installation advice.

---

### Post by aysiu on 2009-11-04
I'm not sure with RPM "aliens" better than the others. bford16 suggested using the OpenSuSE one. If that doesn't work well, you can try "aliening" the Fedora one.

You would paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
wget -c ftp://ftp.lstc.com/outgoing/lsprepost/3.0/linux64/lsprepost-3.0-opensuse11.x86_64.rpm
sudo apt-get update
sudo apt-get install alien
sudo alien -i lsprepost-3.0-opensuse11.x86_64.rpm
```

---

### Post by bondmatt on 2009-11-04
Thank you for the suggestions. I really appreciate it.

The suggestions above are for version 3.0 of LS Pre-Post but I would prefer version 2.4. Version 3.0 is quite different and following the tutorials on the lstc website becomes difficult. I am going to install it anyways because I want to learn to use it but is there any way I can install 2.4? I downloaded the version 2.4 suse110 gz archive but it seemed to contain a .exe file. What is going on?

---

### Post by aysiu on 2009-11-04
I couldn't make head or tails of the .gz files for Linux.

In this particular case, if you need version 2.4, I'd advise using the Windows version in Wine.

**Step 1**
Download the Windows .zip file

**Step 2**
After it's downloaded, right-click it and select *Extract here* to reveal the *lsprepost2_4_xp64.exe* file.

**Step 3**
Use Synaptic Package Manager to install Wine:
[http://www.psychocats.net/ubuntu/installingsoftware#synaptic](http://www.psychocats.net/ubuntu/installingsoftware#synaptic)

**Step 4**
Right-click the *lsprepost2_4_xp64.exe* file and select *Open with Wine Windows program loader*

---

### Post by bondmatt on 2009-11-05
I installed version 3.0 using alien and the Fedora RPM package. The OpenSuse RPM package would not convert. Im not sure if the Fedora RPM installed correctly. I cant find any folders or files. The package is listed as being installed in the synaptic package manager.

I have Wine installed already and am somewhat familiar with it but I figure emulation is to be avoided if possible.

Thanks for all the help,
- Matt Bondy

---

### Post by bondmatt on 2009-11-05
I found a few files and tried to launch LS Pre Post. I get a message that a library related to TIFF files cannot be found. I went into the Synaptic package manager to see if there were any related libraries available or installed and it looked like the one I needed was already installed. I installed 2-3 others that were similar but it still does not work. It looks like time for some WINE.

---

