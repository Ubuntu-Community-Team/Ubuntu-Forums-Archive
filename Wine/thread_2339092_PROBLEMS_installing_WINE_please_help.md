---
title: "PROBLEMS installing WINE please help"
date: 2016-10-04
forum: Wine
---

### Post by larry41 on 2016-10-04
hello friends i'm frustated i'm trying to install wine on my laptop elitebook 8470p. i need wine because i want to try using ZXW ZILLION  on my ubuntu machine and start fixing some cellphones here is what i type on terminal ```
larry3d@larry3d:~$ sudo add-apt-repository ppa:ubuntu-wine/ppa
[sudo] password for larry3d: 
 Welcome to the Wine Team PPA.  Here you can get the latest available Wine betas for every supported version of Ubuntu.  This PPA is managed by Scott Ritchie and Maarten Lankhorst.
 More info: https://launchpad.net/~ubuntu-wine/+archive/ubuntu/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmp4cln_syf/secring.gpg' created
gpg: keyring `/tmp/tmp4cln_syf/pubring.gpg' created
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmp4cln_syf/trustdb.gpg: trustdb created
gpg: key F9CB8DB0: public key "Launchpad PPA for Ubuntu Wine Team" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
larry3d@larry3d:~$ sudo apt-get update
Hit:1 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu xenial InRelease
Hit:2 http://ppa.launchpad.net/wine/wine-builds/ubuntu xenial InRelease
Reading package lists... Done                      
larry3d@larry3d:~$ sudo apt-get install wine1.8 winetricks
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package winetricks is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'winetricks' has no installation candidate
larry3d@larry3d:~$ 

```

please help me and probably i will fix your cellphone for free when is broken :)

---

### Post by ian-weisser on 2016-10-04
> **larry41 said:**
> E: Package 'winetricks' has no installation candidate
The error means exactly what it says. The 'winetricks' package does not exist in any of your sources.
Go ahead and install wine1.8 from that PPA, but not winetricks.

---

### Post by larry41 on 2016-10-04
> **ian-weisser said:**
> The error means exactly what it says. The 'winetricks' package does not exist in any of your sources.
Go ahead and install wine1.8 from that PPA, but not winetricks.

how do i do that please on terminal

i just type this and still the problem 

```
larry3d@larry3d:~$ sudo add-apt-repository ppa:wine/wine-builds
[sudo] password for larry3d: 
 
 More info: https://launchpad.net/~wine/+archive/ubuntu/wine-builds
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpngtdsuyd/secring.gpg' created
gpg: keyring `/tmp/tmpngtdsuyd/pubring.gpg' created
gpg: requesting key 77C899CB from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpngtdsuyd/trustdb.gpg: trustdb created
gpg: key 77C899CB: public key "Launchpad PPA for Wine" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
larry3d@larry3d:~$ sudo apt-get update
Ign:1 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty InRelease
Ign:2 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty Release
Ign:3 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main amd64 Packages
Ign:4 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main i386 Packages
Ign:5 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main all Packages
Ign:6 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-en_US
Ign:7 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-en
Ign:8 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main amd64 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main DEP-11 64x64 Icons
Ign:10 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted amd64 Packages
Ign:11 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted i386 Packages
Ign:12 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted all Packages
Ign:13 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-en_US
Ign:14 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-en
Ign:15 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted amd64 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted DEP-11 64x64 Icons
Ign:3 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main amd64 Packages
Ign:4 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main i386 Packages
Ign:5 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main all Packages
Ign:6 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-en_US
Ign:7 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-en
Ign:8 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main amd64 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main DEP-11 64x64 Icons
Ign:10 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted amd64 Packages
Ign:11 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted i386 Packages
Ign:12 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted all Packages
Ign:13 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-en_US
Ign:14 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-en
Ign:15 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted amd64 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted DEP-11 64x64 Icons
Ign:3 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main amd64 Packages
Ign:4 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main i386 Packages
Ign:5 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main all Packages
Ign:6 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-en_US
Ign:7 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-en
Ign:8 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main amd64 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main DEP-11 64x64 Icons
Ign:10 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted amd64 Packages
Ign:11 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted i386 Packages
Ign:12 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted all Packages
Ign:13 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-en_US
Ign:14 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-en
Ign:15 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted amd64 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted DEP-11 64x64 Icons
Ign:3 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main amd64 Packages
Ign:4 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main i386 Packages
Ign:5 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main all Packages
Ign:6 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-en_US
Ign:7 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-en
Ign:8 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main amd64 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main DEP-11 64x64 Icons
Ign:10 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted amd64 Packages
Ign:11 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted i386 Packages
Ign:12 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted all Packages
Ign:13 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-en_US
Ign:14 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-en
Ign:15 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted amd64 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted DEP-11 64x64 Icons
Ign:3 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main amd64 Packages
Ign:4 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main i386 Packages
Ign:5 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main all Packages
Ign:6 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-en_US
Ign:7 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-en
Ign:8 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main amd64 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main DEP-11 64x64 Icons
Ign:10 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted amd64 Packages
Ign:11 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted i386 Packages
Ign:12 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted all Packages
Ign:13 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-en_US
Ign:14 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-en
Ign:15 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted amd64 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted DEP-11 64x64 Icons
Err:3 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign:4 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main i386 Packages
Ign:17 http://archive.canonical.com/ubuntu trusty InRelease
Hit:18 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu xenial InRelease
Hit:19 http://archive.canonical.com/ubuntu trusty Release                 
Hit:20 http://ppa.launchpad.net/wine/wine-builds/ubuntu xenial InRelease
Reading package lists... Done                      larry3d@larry3d:~$ sudo add-apt-repository ppa:wine/wine-builds
[sudo] password for larry3d: 
 
 More info: https://launchpad.net/~wine/+archive/ubuntu/wine-builds
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpngtdsuyd/secring.gpg' created
gpg: keyring `/tmp/tmpngtdsuyd/pubring.gpg' created
gpg: requesting key 77C899CB from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpngtdsuyd/trustdb.gpg: trustdb created
gpg: key 77C899CB: public key "Launchpad PPA for Wine" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
larry3d@larry3d:~$ sudo apt-get update
Ign:1 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty InRelease
Ign:2 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty Release
Ign:3 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main amd64 Packages
Ign:4 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main i386 Packages
Ign:5 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main all Packages
Ign:6 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-en_US
Ign:7 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-en
Ign:8 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main amd64 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main DEP-11 64x64 Icons
Ign:10 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted amd64 Packages
Ign:11 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted i386 Packages
Ign:12 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted all Packages
Ign:13 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-en_US
Ign:14 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-en
Ign:15 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted amd64 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted DEP-11 64x64 Icons
Ign:3 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main amd64 Packages
Ign:4 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main i386 Packages
Ign:5 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main all Packages
Ign:6 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-en_US
Ign:7 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-en
Ign:8 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main amd64 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main DEP-11 64x64 Icons
Ign:10 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted amd64 Packages
Ign:11 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted i386 Packages
Ign:12 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted all Packages
Ign:13 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-en_US
Ign:14 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-en
Ign:15 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted amd64 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted DEP-11 64x64 Icons
Ign:3 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main amd64 Packages
Ign:4 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main i386 Packages
Ign:5 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main all Packages
Ign:6 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-en_US
Ign:7 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-en
Ign:8 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main amd64 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main DEP-11 64x64 Icons
Ign:10 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted amd64 Packages
Ign:11 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted i386 Packages
Ign:12 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted all Packages
Ign:13 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-en_US
Ign:14 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-en
Ign:15 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted amd64 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted DEP-11 64x64 Icons
Ign:3 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main amd64 Packages
Ign:4 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main i386 Packages
Ign:5 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main all Packages
Ign:6 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-en_US
Ign:7 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-en
Ign:8 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main amd64 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main DEP-11 64x64 Icons
Ign:10 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted amd64 Packages
Ign:11 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted i386 Packages
Ign:12 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted all Packages
Ign:13 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-en_US
Ign:14 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-en
Ign:15 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted amd64 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted DEP-11 64x64 Icons
Ign:3 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main amd64 Packages
Ign:4 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main i386 Packages
Ign:5 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main all Packages
Ign:6 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-en_US
Ign:7 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-en
Ign:8 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main amd64 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main DEP-11 64x64 Icons
Ign:10 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted amd64 Packages
Ign:11 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted i386 Packages
Ign:12 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted all Packages
Ign:13 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-en_US
Ign:14 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-en
Ign:15 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted amd64 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted DEP-11 64x64 Icons
Err:3 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign:4 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main i386 Packages
Ign:17 http://archive.canonical.com/ubuntu trusty InRelease
Hit:18 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu xenial InRelease
Hit:19 http://archive.canonical.com/ubuntu trusty Release                 
Hit:20 http://ppa.launchpad.net/wine/wine-builds/ubuntu xenial InRelease
Reading package lists... Done                      
W: The repository 'cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1)/dists/trusty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
E: Some index files failed to download. They have been ignored, or old ones used instead.
larry3d@larry3d:~$ sudo apt-get install --install-recommends winehq-devel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 winehq-devel : Depends: wine-devel (= 1.9.20~ubuntu16.04.1)
E: Unable to correct problems, you have held broken packages.
larry3d@larry3d:~$ 

W: The repository 'cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1)/dists/trusty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
E: Some index files failed to download. They have been ignored, or old ones used instead.
larry3d@larry3d:~$ sudo apt-get install --install-recommends winehq-devel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 winehq-devel : Depends: wine-devel (= 1.9.20~ubuntu16.04.1)
E: Unable to correct problems, you have held broken packages.
larry3d@larry3d:~$ 

```

---

### Post by QIII on 2016-10-04
Hello!

Please use code tags, not html tags.

---

### Post by larry41 on 2016-10-04
oh sorry sorry i thought i was doing right

i tried again this time like this 

sudo add-apt-repository ppa:ricotz/unstable
sudo apt update
sudo apt install wine1.8

```
larry3d@larry3d:~$ sudo add-apt-repository ppa:ricotz/unstable
[sudo] password for larry3d: 
 
 More info: https://launchpad.net/~ricotz/+archive/ubuntu/unstable
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmp5f2sd14s/secring.gpg' created
gpg: keyring `/tmp/tmp5f2sd14s/pubring.gpg' created
gpg: requesting key 9E5DB0C8 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmp5f2sd14s/trustdb.gpg: trustdb created
gpg: key 9E5DB0C8: public key "Launchpad PPA for Rico" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
larry3d@larry3d:~$ sudo apt update
Ign:1 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty InRelease
Err:2 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty Release
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign:3 http://archive.canonical.com/ubuntu trusty InRelease
Get:4 http://ppa.launchpad.net/ricotz/unstable/ubuntu xenial InRelease [23.8 kB]
Hit:5 http://archive.canonical.com/ubuntu trusty Release 
Hit:7 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu xenial InRelease
Hit:8 http://ppa.launchpad.net/wine/wine-builds/ubuntu xenial InRelease
Get:9 http://ppa.launchpad.net/ricotz/unstable/ubuntu xenial/main amd64 Packages [33.8 kB]
Get:10 http://ppa.launchpad.net/ricotz/unstable/ubuntu xenial/main i386 Packages [36.4 kB]
Get:11 http://ppa.launchpad.net/ricotz/unstable/ubuntu xenial/main Translation-en [3,136 B]
Reading package lists... Done                                     
E: The repository 'cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
larry3d@larry3d:~$ sudo apt install wine1.8
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.8 : Depends: wine1.8-i386 (= 1:1.8.4-0ubuntu1~16.04~ricotz1)
           Recommends: gnome-exe-thumbnailer but it is not installable or
                       kde-runtime but it is not installable
           Recommends: fonts-horai-umefont but it is not installable
           Recommends: fonts-unfonts-core but it is not installable
           Recommends: winetricks but it is not installable
E: Unable to correct problems, you have held broken packages.
larry3d@larry3d:~$ 

```

still the problems :(

---

### Post by ian-weisser on 2016-10-04
Different problem, similar cause.
Are you really trying to install Wine 1.8 on Ubuntu 14.04? That won't work easily - you will need some really good package management skills to make that work.

Did you already try (and reject) the tested and supported version of Wine 1.6 in Ubuntu 14.04 and 16.04?

---

### Post by howefield on 2016-10-05
Thread moved to the "*Wine*" forum.

---

### Post by larry41 on 2016-10-05
i'm using ubuntu 16.04 i don't even know why appears 14.04 on terminal

---

### Post by kc1di on 2016-10-05
Hi Larry41,
You may want to install playonlinux - it will download and install wine up to version 1.9 for you in a virtual machine.  it really works well on my machine. 
you can install it from the terminal with this command.
```
sudo apt-get install playonlinux
```
after it's installed you find it in the games section of the menu. 

Good Luck :)

---

### Post by larry41 on 2016-10-05
i did that and i got this```
larry3d@larry3d:~$ sudo apt-get install playonlinux
[sudo] password for larry3d: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package playonlinux
larry3d@larry3d:~$ 

```

---

### Post by kc1di on 2016-10-05
your sure your using 16.04 -- playonlinux is in the repository.  
have your done a```
sudo apt-get update
```?

if you have can you go to your apt sources list and copy and past it here.
also go to the terminal and type this command and past the output here.
```
lsb_release -a
```

---

### Post by larry41 on 2016-10-06
i just did it and i got this
```
larry3d@larry3d:~$ sudo apt-get update
[sudo] password for larry3d: 
Ign:1 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty InRelease
Ign:2 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty Release
Ign:3 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main amd64 Packages
Ign:4 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main i386 Packages
Ign:5 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main all Packages
Ign:6 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-en_US
Ign:7 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-en
Ign:8 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main amd64 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main DEP-11 64x64 Icons
Ign:10 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted amd64 Packages
Ign:11 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted i386 Packages
Ign:12 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted all Packages
Ign:13 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-en_US
Ign:14 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-en
Ign:15 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted amd64 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted DEP-11 64x64 Icons
Ign:3 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main amd64 Packages
Ign:4 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main i386 Packages
Ign:5 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main all Packages
Ign:6 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-en_US
Ign:7 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-en
Ign:8 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main amd64 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main DEP-11 64x64 Icons
Ign:10 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted amd64 Packages
Ign:11 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted i386 Packages
Ign:12 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted all Packages
Ign:13 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-en_US
Ign:14 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-en
Ign:15 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted amd64 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted DEP-11 64x64 Icons
Ign:3 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main amd64 Packages
Ign:4 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main i386 Packages
Ign:5 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main all Packages
Ign:6 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-en_US
Ign:7 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-en
Ign:8 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main amd64 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main DEP-11 64x64 Icons
Ign:10 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted amd64 Packages
Ign:11 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted i386 Packages
Ign:12 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted all Packages
Ign:13 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-en_US
Ign:14 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-en
Ign:15 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted amd64 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted DEP-11 64x64 Icons
Ign:3 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main amd64 Packages
Ign:4 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main i386 Packages
Ign:5 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main all Packages
Ign:6 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-en_US
Ign:7 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-en
Ign:8 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main amd64 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main DEP-11 64x64 Icons
Ign:10 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted amd64 Packages
Ign:11 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted i386 Packages
Ign:12 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted all Packages
Ign:13 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-en_US
Ign:14 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-en
Ign:15 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted amd64 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted DEP-11 64x64 Icons
Ign:3 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main amd64 Packages
Ign:4 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main i386 Packages
Ign:5 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main all Packages
Ign:6 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-en_US
Ign:7 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-en
Ign:8 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main amd64 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main DEP-11 64x64 Icons
Ign:10 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted amd64 Packages
Ign:11 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted i386 Packages
Ign:12 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted all Packages
Ign:13 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-en_US
Ign:14 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-en
Ign:15 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted amd64 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted DEP-11 64x64 Icons
Err:3 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign:4 cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main i386 Packages
Ign:17 http://archive.canonical.com/ubuntu trusty InRelease
Hit:18 http://ppa.launchpad.net/ricotz/unstable/ubuntu xenial InRelease
Hit:19 http://archive.canonical.com/ubuntu trusty Release                 
Hit:20 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu xenial InRelease   
Hit:21 http://ppa.launchpad.net/wine/wine-builds/ubuntu xenial InRelease
Reading package lists... Done 
W: The repository 'cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1)/dists/trusty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
E: Some index files failed to download. They have been ignored, or old ones used instead.
larry3d@larry3d:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial
larry3d@larry3d:~$ 


```

---

### Post by howefield on 2016-10-06
Open up the *Software & Updates* application and uncheck the cdrom section, then try a sudo apt update again.

What is the output from the following command ?

```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

### Post by larry41 on 2016-10-06
i opened  and was already like this as the picture shows

 [ATTACH=CONFIG]271520[/ATTACH]  

```
larry3d@larry3d:~$ egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
/etc/apt/sources.list:deb cdrom:[Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1)]/ trusty main restricted
/etc/apt/sources.list:deb http://archive.canonical.com/ubuntu trusty partner
/etc/apt/sources.list:deb-src http://archive.canonical.com/ubuntu trusty partner
/etc/apt/sources.list.d/clipgrab-team-ppa-trusty.list.distUpgrade:deb http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu trusty main
/etc/apt/sources.list.d/nilarimogard-webupd8-trusty.list.distUpgrade:deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main
/etc/apt/sources.list.d/ricotz-ubuntu-unstable-xenial.list:deb http://ppa.launchpad.net/ricotz/unstable/ubuntu xenial main
/etc/apt/sources.list.d/ricotz-ubuntu-unstable-xenial.list.save:deb http://ppa.launchpad.net/ricotz/unstable/ubuntu xenial main
/etc/apt/sources.list.d/ubuntu-wine-ubuntu-ppa-xenial.list:deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu xenial main
/etc/apt/sources.list.d/ubuntu-wine-ubuntu-ppa-xenial.list.save:deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu xenial main
/etc/apt/sources.list.d/wine-ubuntu-wine-builds-xenial.list:deb http://ppa.launchpad.net/wine/wine-builds/ubuntu xenial main
/etc/apt/sources.list.d/wine-ubuntu-wine-builds-xenial.list.save:deb http://ppa.launchpad.net/wine/wine-builds/ubuntu xenial main
larry3d@larry3d:~$ 


```

---

### Post by howefield on 2016-10-06
Back into the Software & Updates application, you'll need to enable some of the repositories, winetricks is in the universe repository and playonlinux is to be found in the multiverse repository.

I'd suggest you check off the first 4.. main, universe, restricted and multiverse.

Close out and do sudo apt update once more.

By the way, mixing repositories isn't generally a good idea, you have trusty and xenial sources in there.

---

### Post by larry41 on 2016-10-06
i hope you mean that i have to do this[ATTACH=CONFIG]271521[/ATTACH] because after that the still the problem

---

### Post by howefield on 2016-10-06
> **larry41 said:**
> i hope you mean that i have to do this because after that the still the problem

No I meant to check the four (main, universe, restricted and multiverse) on the *Ubuntu Software* tab.

Also uncheck the cdrom option from the *Other Software* tab.

---

### Post by larry41 on 2016-10-06
yes my friend the first picture shows something that i never change no even now  [ATTACH=CONFIG]271522[/ATTACH]  than i went to the other tab and i did this
[ATTACH=CONFIG]271523[/ATTACH] now what do i do please save my life :popcorn:

---

### Post by howefield on 2016-10-06
> **larry41 said:**
> yes my friend the first picture shows something that i never change no even now ...

Shrug, that's up to you. 

Your machine, your choice.

---

### Post by larry41 on 2016-10-06
do i need to select them?

i edit this post because i select everything in the first tab and the problem still there and here is what happeds when i type wine on sofware center[ATTACH=CONFIG]271525[/ATTACH]

---

### Post by howefield on 2016-10-06
Selecting the repositories tells the system that you want to use them, you now need to tell the system what's in the newly selected repositories by doing a further

```
sudo apt update
```

Do that and report any errors back here, if no errors try installing wine again.

Software Centre may not display the wine package but you should be able to install it from the terminal.

```
apt-cache search wine
```

should show you packages available that relate to wine in some way.

---

### Post by larry41 on 2016-10-06
ok my friend for what i understood i did this according to every picture as follows

[ATTACH=CONFIG]271526[/ATTACH][ATTACH=CONFIG]271528[/ATTACH] after that i went to terminal and i type  

```
larry3d@larry3d:~$ apt-cache search wine
libwinpr-asn1-0.1 - Windows Portable Runtime library (ASN1 library)
libwinpr-bcrypt0.1 - Windows Portable Runtime library (bcrypt library)
libwinpr-credentials0.1 - Windows Portable Runtime library (credentials library)
libwinpr-credui0.1 - Windows Portable Runtime library (credeui library)
libwinpr-crt0.1 - Windows Portable Runtime library (crt library)
libwinpr-crypto0.1 - Windows Portable Runtime library (crypto library)
libwinpr-dbg - Windows Portable Runtime library (debug symbols)
libwinpr-dev - Windows Portable Runtime library (development files)
libwinpr-dsparse0.1 - Windows Portable Runtime library (dsparse library)
libwinpr-environment0.1 - Windows Portable Runtime library (environment library)
libwinpr-error0.1 - Windows Portable Runtime library (error library)
libwinpr-file0.1 - Windows Portable Runtime library (file library)
libwinpr-handle0.1 - Windows Portable Runtime library (handle library)
libwinpr-heap0.1 - Windows Portable Runtime library (heap library)
libwinpr-input0.1 - Windows Portable Runtime library (input library)
libwinpr-interlocked0.1 - Windows Portable Runtime library (interlocked library)
libwinpr-io0.1 - Windows Portable Runtime library (io library)
libwinpr-library0.1 - Windows Portable Runtime library (library)
libwinpr-path0.1 - Windows Portable Runtime library (path library)
libwinpr-pipe0.1 - Windows Portable Runtime library (pipe library)
libwinpr-pool0.1 - Windows Portable Runtime library (pool library)
libwinpr-registry0.1 - Windows Portable Runtime library (registry library)
libwinpr-rpc0.1 - Windows Portable Runtime library (RPC library)
libwinpr-sspi0.1 - Windows Portable Runtime library (sspi library)
libwinpr-sspicli0.1 - Windows Portable Runtime library (sspicli library)
libwinpr-synch0.1 - Windows Portable Runtime library (synch library)
libwinpr-sysinfo0.1 - Windows Portable Runtime library (sysinfo library)
libwinpr-thread0.1 - Windows Portable Runtime library (thread library)
libwinpr-timezone0.1 - Windows Portable Runtime library (timezone library)
libwinpr-utils0.1 - Windows Portable Runtime library (utils library)
libwinpr-winhttp0.1 - Windows Portable Runtime library (winhttp library)
libwinpr-winsock0.1 - Windows Portable Runtime library (winsock library)
gemrb - Open-source engine to run Baldur's Gate, Icewind Dale and Planescape: Torment
gnome-colors - set of GNOME icon themes
gnome-exe-thumbnailer - Wine .exe and other executable thumbnailer for GNOME
gnome-wine-icon-theme - red variation of the GNOME-Colors icon theme
innoextract - Tool for extracting data from an Inno Setup installer
libkwineffects7 - KDE window manager effects library
libwine-development - Windows API implementation - library
libwine-development-dev - Windows API implementation - development files
mingw-w64-i686-dev - Development files for MinGW-w64 targeting Win32
mingw-w64-x86-64-dev - Development files for MinGW-w64 targeting Win64
python-neo - Python IO library for electrophysiological data formats
q4wine - Qt GUI for wine (WINE)
shiki-colors - set of Metacity/GTK-2+ themes
shiki-wine-theme - red variation of the Shiki-Colors theme
tellico - Collection manager for books, videos, music, etc
tellico-data - Collection manager for books, videos, music, etc [data]
tellico-doc - Collection manager for books, videos, music, etc [doc]
tellico-scripts - Collection manager for books, videos, music, etc [scripts]
twine - utility for interacting with PyPI
unmass - Extract game archive files
wine - Microsoft Windows Compatibility Layer (meta-package)
wine-development - Windows API implementation - standard suite
wine1.4 - Microsoft Windows Compatibility Layer (dummy package)
wine1.4-amd64 - Microsoft Windows Compatibility Layer (dummy package)
wine1.4-dbg - Microsoft Windows Compatibility Layer (dummy package)
wine1.4-dev - Microsoft Windows Compatibility Layer (dummy package)
wine1.6 - Microsoft Windows Compatibility Layer (Binary Emulator and Library)
wine1.6-amd64 - Microsoft Windows Compatibility Layer (64-bit support)
wine1.6-dbg - Microsoft Windows Compatibility Layer (debugging symbols)
wine1.6-dev - Microsoft Windows Compatibility Layer (Development files)
wine64-development - Windows API implementation - 64-bit binary loader
wine64-development-preloader - Windows API implementation - prelinked 64-bit binary loader
wine64-development-tools - Windows API implementation - 64-bit developer tools
winefish - LaTeX Editor based on Bluefish
winetricks - Microsoft Windows Compatibility Layer (winetricks)
wine32-development - Windows API implementation - 32-bit binary loader
wine32-development-preloader - Windows API implementation - prelinked 32-bit binary loader
wine32-development-tools - Windows API implementation - 32-bit developer tools
wine1.4-i386 - Microsoft Windows Compatibility Layer (dummy package)
wine1.6-i386 - Microsoft Windows Compatibility Layer (32-bit support)
playonlinux - front-end for Wine
wine-gecko2.21 - Microsoft Windows compatibility layer (embedded web browser)
wine-mono0.0.8 - Microsoft Windows compatibility layer (.NET compatibility)
larry3d@larry3d:~$ 


```

is this means that i can install now wine through terminal like wine 1.8 ?

---

### Post by howefield on 2016-10-06
You can try it, playonlinux and winetricks are there in your output at least.

When I add the ppa:ubuntu-wine/ppa repository I see wine1.8 in apt-cache search so not sure why it isn't present in your output. Although you do have several wine ppas installed, not sure why ?

---

### Post by larry41 on 2016-10-06
yeah probably i have those ppa installed because i was trying and trying in one way and another to install wine, taking different versions, how can i delete all those ppa and install wine a new fresh wine 1.8 ?

---

### Post by howefield on 2016-10-06
Go into the Software & Update application, Other Software tab and uncheck all the wine repositories except for the first one you added as per the first post in this thread, ppa:ubuntu-wine/ppa.

As you can see from [this page]("https://launchpad.net/~ubuntu-wine/+archive/ubuntu/ppa?field.series_filter=xenial"), it has the wine1.8 package.

Then to install the packages as per your first post in the thread..

```
sudo apt update
```
```
sudo apt install wine1.8 winetricks
```

Post back any errors.

---

### Post by larry41 on 2016-10-06
i got this```
larry3d@larry3d:~$ sudo apt update
[sudo] password for larry3d: 
Hit:1 http://archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu xenial InRelease
Reading package lists... Done                     
Building dependency tree       
Reading state information... Done
All packages are up to date.
larry3d@larry3d:~$ sudo apt wine1.8 winetricks
E: Invalid operation wine1.8
larry3d@larry3d:~$ ^C
larry3d@larry3d:~$ 



```

---

### Post by howefield on 2016-10-06
Apologies, my mistake, missed the install part of the command (corrected above).

```
sudo apt install wine1.8 winetricks
```

---

### Post by larry41 on 2016-10-06
oh my goodness it looks like terminal is showing me a lot problems only a programmer can fix it :D```
larry3d@larry3d:~$ sudo apt install wine1.8 winetricks
[sudo] password for larry3d: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.8 : Depends: wine1.8-i386 (= 1:1.8.0-0ubuntu1~ubuntu15.10.1~ppa1)
E: Unable to correct problems, you have held broken packages.
larry3d@larry3d:~$ ^C
larry3d@larry3d:~$ 





```

this means that there is no solution?

---

### Post by kc1di on 2016-10-06
Hi Again Larry,

As I said before install playonlinux and you can install from that wine 1.8 or 1.9  i don't think 1.8 is in the repository yet unless you add the PPA repository first. 
give playonlinux a try.

---

### Post by larry41 on 2016-10-06
> **kc1di said:**
> Hi Again Larry,

As I said before install playonlinux and you can install from that wine 1.8 or 1.9  i don't think 1.8 is in the repository yet unless you add the PPA repository first. 
give playonlinux a try.

my friend how can i install playonlinux? because on softwares updates i was trying to find it in every tab and is not nowhere.

because i couln't find playonlinux on softwares updates so i decided to install through terminal and now is install already playonlinux 

 sudo apt-get install playonlinux 

next i type this on terminal
```
larry3d@larry3d:~$ sudo apt install wine1.8 winetricks
[sudo] password for larry3d: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
winetricks is already the newest version (0.0+20141009+svn1208-2ubuntu1).
winetricks set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.8 : Depends: wine1.8-i386 (= 1:1.8.0-0ubuntu1~ubuntu15.10.1~ppa1)
E: Unable to correct problems, you have held broken packages.
larry3d@larry3d:~$ 

```

than because i'm not getting answers i decide to search on how to install wine any version and i found the 1.6 and still the problems

```
larry3d@larry3d:~$ sudo add-apt-repository ppa:ubuntu-wine/ppa
[sudo] password for larry3d: 
 Welcome to the Wine Team PPA.  Here you can get the latest available Wine betas for every supported version of Ubuntu.  This PPA is managed by Scott Ritchie and Maarten Lankhorst.
 More info: https://launchpad.net/~ubuntu-wine/+archive/ubuntu/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpg0sgs1e2/secring.gpg' created
gpg: keyring `/tmp/tmpg0sgs1e2/pubring.gpg' created
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpg0sgs1e2/trustdb.gpg: trustdb created
gpg: key F9CB8DB0: public key "Launchpad PPA for Ubuntu Wine Team" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
larry3d@larry3d:~$ sudo apt-get update
Hit:1 http://archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu xenial InRelease
Reading package lists... Done
larry3d@larry3d:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.6 but it is not going to be installed or
                 wine1.8 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
larry3d@larry3d:~$ 


```

sorry but most of everything i have to figure out on how to do it but the problems still on ubuntu. really sorry if i sounds rude but i'm getting sick of all this and is not supost that in order to fix a problem always i have to make a new  fresh installation of ubuntu. is not about you guys please understand

---

### Post by ian-weisser on 2016-10-07
We understand your frustration. We all had to learn the terminal and how to manage packages, too.

You certainly don't need to reinstall Ubuntu; your problem is generally very easy to fix...though a bit slow and tedious in a forum. You must have patience to learn your new terminal skills and package management skills. You will need those skills again.

Frustration is fully expected when users unfamiliar with package management try to do complex tasks like installing non-Ubuntu software.

---

### Post by kc1di on 2016-10-07
Try this command and see if it fixes at least part of the problem. Then we will go from there. 
```
sudo dpkg --configure -a
```

---

### Post by larry41 on 2016-10-07
i did this command  sudo dpkg --configure -a

```
larry3d@larry3d:~$ sudo dpkg --configure -a
[sudo] password for larry3d: 
larry3d@larry3d:~$ 









```

---

### Post by howefield on 2016-10-09
I'd suggest getting your system back to a default position if possible using ppa-purge.

```
sudo apt-get install ppa-purge
```
```
sudo ppa-purge name_of_added_ppa
```

This should remove the ppas that you added and put back the packages installed from them to Ubuntu default versions, this won't remove installed PPA packages that are not in the official repositories.

---

### Post by larry41 on 2016-10-09
so this command sudo ppa-purge name_of_added_ppa do i need to writte on terminal like this 
sudo ppa-purge wine  i don't get it

---

### Post by howefield on 2016-10-09
> **larry41 said:**
> so this command sudo ppa-purge name_of_added_ppa do i need to writte on terminal like this 
sudo ppa-purge wine  i don't get it

Ok, lets suppose that you installed the wine-builds ppa using the command..

```
sudo add-apt-repository ppa:wine/wine-builds
```

To purge it after installing the ppa-purge package you would use the command..

```
sudo ppa-purge ppa:wine/wine-builds
```

Likewise any other ppa that you added, use the ppa name.

---

### Post by larry41 on 2016-10-09
i just did it and it looks that everything was perfect this time according to terminal
```
larry3d@larry3d:~$ sudo add-apt-repository ppa:wine/wine-builds
[sudo] password for larry3d: 
 
 More info: https://launchpad.net/~wine/+archive/ubuntu/wine-builds
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpkrpmy08y/secring.gpg' created
gpg: keyring `/tmp/tmpkrpmy08y/pubring.gpg' created
gpg: requesting key 77C899CB from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpkrpmy08y/trustdb.gpg: trustdb created
gpg: key 77C899CB: public key "Launchpad PPA for Wine" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
larry3d@larry3d:~$ sudo ppa-purge ppa:wine/wine-builds
Updating packages lists
PPA to be removed: wine wine-builds
Package revert list generated:


Disabling wine PPA from 
/etc/apt/sources.list.d/wine-ubuntu-wine-builds-xenial.list
Updating packages lists
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ca-certificates-java default-jre-headless fonts-dejavu-extra
  fonts-wqy-microhei java-common libasn1-8-heimdal:i386 libasound2:i386
  libasyncns0:i386 libavahi-client3:i386 libavahi-common-data:i386
  libavahi-common3:i386 libbonobo2-0 libbonobo2-common libcaca0:i386
  libcups2:i386 libcurl3:i386 libdbus-1-3:i386 libegl1-mesa:i386 libenca0
  libevdev2:i386 libflac8:i386 libfontconfig1:i386 libfreetype6:i386
  libgbm1:i386 libgcrypt20:i386 libglib2.0-0:i386 libgmp10:i386 libgnome-2-0
  libgnome2-common libgnomevfs2-0 libgnomevfs2-common libgnutls30:i386
  libgraphite2-3:i386 libgssapi-krb5-2:i386 libgssapi3-heimdal:i386
  libgudev-1.0-0:i386 libharfbuzz0b:i386 libhcrypto4-heimdal:i386
  libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386 libhogweed4:i386
  libhx509-5-heimdal:i386 libice6:i386 libicu55:i386 libidn11:i386
  libinput10:i386 libjpeg-turbo8:i386 libjpeg8:i386 libjson-c2:i386
  libk5crypto3:i386 libkeyutils1:i386 libkrb5-26-heimdal:i386 libkrb5-3:i386
  libkrb5support0:i386 libldap-2.4-2:i386 libmtdev1:i386 libnettle6:i386
  libogg0:i386 liborbit-2-0 libp11-kit0:i386 libpcre16-3:i386 libpng12-0:i386
  libproxy1v5:i386 libpulse0:i386 libpython2.7:i386 libpython2.7-minimal:i386
  libpython2.7-stdlib:i386 libqt5core5a:i386 libqt5dbus5:i386 libqt5gui5:i386
  libqt5network5:i386 libqt5opengl5:i386 libqt5printsupport5:i386
  libqt5svg5:i386 libqt5widgets5:i386 libqt5x11extras5:i386 libreadline6:i386
  libroken18-heimdal:i386 librtmp1:i386 libsasl2-2:i386 libsasl2-modules:i386
  libsasl2-modules-db:i386 libsdl1.2debian:i386 libslang2:i386 libsm6:i386
  libsndfile1:i386 libsqlite3-0:i386 libssl1.0.0:i386 libsystemd0:i386
  libtasn1-6:i386 libvorbis0a:i386 libvorbisenc2:i386 libvorbisidec1
  libvpx3:i386 libwacom2:i386 libwayland-client0:i386 libwayland-server0:i386
  libwind0-heimdal:i386 libwrap0:i386 libxcb-icccm4:i386 libxcb-image0:i386
  libxcb-keysyms1:i386 libxcb-randr0:i386 libxcb-render-util0:i386
  libxcb-render0:i386 libxcb-shape0:i386 libxcb-shm0:i386 libxcb-util1:i386
  libxcb-xfixes0:i386 libxcb-xkb1:i386 libxcursor1:i386 libxi6:i386
  libxinerama1:i386 libxkbcommon-x11-0:i386 libxkbcommon0:i386 libxml2:i386
  libxmu6:i386 libxrender1:i386 libxt6:i386 linux-headers-4.4.0-34
  linux-headers-4.4.0-34-generic linux-image-4.4.0-34-generic
  linux-image-extra-4.4.0-34-generic openjdk-8-jre-headless ttf-wqy-microhei
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
PPA purged successfully
larry3d@larry3d:~$ 


```
now if i want to install wine like 1.8 how can i do it without any mistake and thanks in advance

---

### Post by howefield on 2016-10-10
> **larry41 said:**
> i just did it and it looks that everything was perfect this time according to terminal...... now if i want to install wine like 1.8 how can i do it without any mistake and thanks in advance

Not sure why you installed the wine-builds ppa, didn't you already have it ?

Anyway, do the ppa for each ppa that you have installed, then you can look to install wine from a fresh base. If you are not sure what to do, give us the output of ..

```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

so we know where you are with installed repositories.

---

### Post by larry41 on 2016-10-10
i don't have any idea of what my cousin did when he was using my laptop now he move somewhere else. 

when you say " do the ppa that you have installed" i don't have any idea is this about of any file installed already? because i don't know anything about it sorry my friend .
i did the command you gave me on terminal and this is what i got.
```

larry3d@larry3d:~$ egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu xenial main universe restricted multiverse
/etc/apt/sources.list:deb-src http://archive.ubuntu.com/ubuntu xenial main universe restricted multiverse #Added by software-properties
/etc/apt/sources.list.d/clipgrab-team-ppa-trusty.list.distUpgrade:deb http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu trusty main
/etc/apt/sources.list.d/nilarimogard-webupd8-trusty.list.distUpgrade:deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main
/etc/apt/sources.list.d/ubuntu-wine-ubuntu-ppa-xenial.list:deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu xenial main
/etc/apt/sources.list.d/ubuntu-wine-ubuntu-ppa-xenial.list.save:deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu xenial main
larry3d@larry3d:~$ 




```

---

### Post by howefield on 2016-10-10
So now do..

```
sudo ppa-purge ppa:ubuntu-wine/ppa
```

then

```
sudo apt update
```

and

```
sudo apt -s install wine1.6
```

The -s switch will only simulate an install, it is just so we can see the output.

---

### Post by larry41 on 2016-10-11
i did all those commands on terminal but looks like there still some problems, here is what i got.

```


larry3d@larry3d:~$ sudo ppa-purge ppa:ubuntu-wine/ppa
[sudo] password for larry3d: 
Updating packages lists
PPA to be removed: ubuntu-wine ppa
Package revert list generated:


Disabling ubuntu-wine PPA from 
/etc/apt/sources.list.d/ubuntu-wine-ubuntu-ppa-xenial.list
Updating packages lists
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ca-certificates-java default-jre-headless fonts-dejavu-extra
  fonts-wqy-microhei java-common libasn1-8-heimdal:i386 libasound2:i386
  libasyncns0:i386 libavahi-client3:i386 libavahi-common-data:i386
  libavahi-common3:i386 libbonobo2-0 libbonobo2-common libcaca0:i386
  libcups2:i386 libcurl3:i386 libdbus-1-3:i386 libegl1-mesa:i386 libenca0
  libevdev2:i386 libflac8:i386 libfontconfig1:i386 libfreetype6:i386
  libgbm1:i386 libgcrypt20:i386 libglib2.0-0:i386 libgmp10:i386 libgnome-2-0
  libgnome2-common libgnomevfs2-0 libgnomevfs2-common libgnutls30:i386
  libgraphite2-3:i386 libgssapi-krb5-2:i386 libgssapi3-heimdal:i386
  libgudev-1.0-0:i386 libharfbuzz0b:i386 libhcrypto4-heimdal:i386
  libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386 libhogweed4:i386
  libhx509-5-heimdal:i386 libice6:i386 libicu55:i386 libidn11:i386
  libinput10:i386 libjpeg-turbo8:i386 libjpeg8:i386 libjson-c2:i386
  libk5crypto3:i386 libkeyutils1:i386 libkrb5-26-heimdal:i386 libkrb5-3:i386
  libkrb5support0:i386 libldap-2.4-2:i386 libmtdev1:i386 libnettle6:i386
  libogg0:i386 liborbit-2-0 libp11-kit0:i386 libpcre16-3:i386 libpng12-0:i386
  libproxy1v5:i386 libpulse0:i386 libpython2.7:i386 libpython2.7-minimal:i386
  libpython2.7-stdlib:i386 libqt5core5a:i386 libqt5dbus5:i386 libqt5gui5:i386
  libqt5network5:i386 libqt5opengl5:i386 libqt5printsupport5:i386
  libqt5svg5:i386 libqt5widgets5:i386 libqt5x11extras5:i386 libreadline6:i386
  libroken18-heimdal:i386 librtmp1:i386 libsasl2-2:i386 libsasl2-modules:i386
  libsasl2-modules-db:i386 libsdl1.2debian:i386 libslang2:i386 libsm6:i386
  libsndfile1:i386 libsqlite3-0:i386 libssl1.0.0:i386 libsystemd0:i386
  libtasn1-6:i386 libvorbis0a:i386 libvorbisenc2:i386 libvorbisidec1
  libvpx3:i386 libwacom2:i386 libwayland-client0:i386 libwayland-server0:i386
  libwind0-heimdal:i386 libwrap0:i386 libxcb-icccm4:i386 libxcb-image0:i386
  libxcb-keysyms1:i386 libxcb-randr0:i386 libxcb-render-util0:i386
  libxcb-render0:i386 libxcb-shape0:i386 libxcb-shm0:i386 libxcb-util1:i386
  libxcb-xfixes0:i386 libxcb-xkb1:i386 libxcursor1:i386 libxi6:i386
  libxinerama1:i386 libxkbcommon-x11-0:i386 libxkbcommon0:i386 libxml2:i386
  libxmu6:i386 libxrender1:i386 libxt6:i386 linux-headers-4.4.0-34
  linux-headers-4.4.0-34-generic linux-image-4.4.0-34-generic
  linux-image-extra-4.4.0-34-generic openjdk-8-jre-headless ttf-wqy-microhei
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
PPA purged successfully
larry3d@larry3d:~$ sudo apt update
Hit:1 http://archive.ubuntu.com/ubuntu xenial InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
larry3d@larry3d:~$ sudo apt -s install wine1.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.6 : Depends: wine1.6-i386 (= 1:1.6.2-0ubuntu14)
E: Unable to correct problems, you have held broken packages.
larry3d@larry3d:~$ 



```

i only see the icon of winetricks

---

### Post by ian-weisser on 2016-10-11
> **larry41 said:**
> Reading state information... Done
The following packages were automatically installed and are no longer required:
  [Long, long list]
Use 'sudo apt autoremove' to remove them.
The system told you what to do next, and why.
Then try installing Wine.

---

### Post by larry41 on 2016-10-11
i'm only following the commands that you guys are telling to do because i don't even know how to solve this problem in order to install wine. if you tell me that i need to remove something i will do it, but i only know to copy and paste on terminal.

so can i do this command on terminal or is a bad idea? 

sudo apt autoremove

---

### Post by ian-weisser on 2016-10-11
We all started out that way, too.
We are leading you down the path to a fix.

Yes, run autoremove.

---

### Post by larry41 on 2016-10-12
ok friends i just did that command of sudo apt autoremove and this is what i got

```


larry3d@larry3d:~$ sudo apt autoremove 
[sudo] password for larry3d: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ca-certificates-java default-jre-headless fonts-dejavu-extra
  fonts-wqy-microhei java-common libasn1-8-heimdal:i386 libasound2:i386
  libasyncns0:i386 libavahi-client3:i386 libavahi-common-data:i386
  libavahi-common3:i386 libbonobo2-0 libbonobo2-common libcaca0:i386
  libcups2:i386 libcurl3:i386 libdbus-1-3:i386 libegl1-mesa:i386 libenca0
  libevdev2:i386 libflac8:i386 libfontconfig1:i386 libfreetype6:i386
  libgbm1:i386 libgcrypt20:i386 libglib2.0-0:i386 libgmp10:i386 libgnome-2-0
  libgnome2-common libgnomevfs2-0 libgnomevfs2-common libgnutls30:i386
  libgraphite2-3:i386 libgssapi-krb5-2:i386 libgssapi3-heimdal:i386
  libgudev-1.0-0:i386 libharfbuzz0b:i386 libhcrypto4-heimdal:i386
  libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386 libhogweed4:i386
  libhx509-5-heimdal:i386 libice6:i386 libicu55:i386 libidn11:i386
  libinput10:i386 libjpeg-turbo8:i386 libjpeg8:i386 libjson-c2:i386
  libk5crypto3:i386 libkeyutils1:i386 libkrb5-26-heimdal:i386 libkrb5-3:i386
  libkrb5support0:i386 libldap-2.4-2:i386 libmtdev1:i386 libnettle6:i386
  libogg0:i386 liborbit-2-0 libp11-kit0:i386 libpcre16-3:i386 libpng12-0:i386
  libproxy1v5:i386 libpulse0:i386 libpython2.7:i386 libpython2.7-minimal:i386
  libpython2.7-stdlib:i386 libqt5core5a:i386 libqt5dbus5:i386 libqt5gui5:i386
  libqt5network5:i386 libqt5opengl5:i386 libqt5printsupport5:i386
  libqt5svg5:i386 libqt5widgets5:i386 libqt5x11extras5:i386 libreadline6:i386
  libroken18-heimdal:i386 librtmp1:i386 libsasl2-2:i386 libsasl2-modules:i386
  libsasl2-modules-db:i386 libsdl1.2debian:i386 libslang2:i386 libsm6:i386
  libsndfile1:i386 libsqlite3-0:i386 libssl1.0.0:i386 libsystemd0:i386
  libtasn1-6:i386 libvorbis0a:i386 libvorbisenc2:i386 libvorbisidec1
  libvpx3:i386 libwacom2:i386 libwayland-client0:i386 libwayland-server0:i386
  libwind0-heimdal:i386 libwrap0:i386 libxcb-icccm4:i386 libxcb-image0:i386
  libxcb-keysyms1:i386 libxcb-randr0:i386 libxcb-render-util0:i386
  libxcb-render0:i386 libxcb-shape0:i386 libxcb-shm0:i386 libxcb-util1:i386
  libxcb-xfixes0:i386 libxcb-xkb1:i386 libxcursor1:i386 libxi6:i386
  libxinerama1:i386 libxkbcommon-x11-0:i386 libxkbcommon0:i386 libxml2:i386
  libxmu6:i386 libxrender1:i386 libxt6:i386 linux-headers-4.4.0-34
  linux-headers-4.4.0-34-generic linux-image-4.4.0-34-generic
  linux-image-extra-4.4.0-34-generic openjdk-8-jre-headless ttf-wqy-microhei
0 upgraded, 0 newly installed, 125 to remove and 0 not upgraded.
After this operation, 539 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 497594 files and directories currently installed.)
Removing default-jre-headless (2:1.8-56ubuntu2) ...
Removing fonts-dejavu-extra (2.35-1) ...
Removing ttf-wqy-microhei (0.2.0-beta-2) ...
Removing fonts-wqy-microhei (0.2.0-beta-2) ...
Removing libcurl3:i386 (7.47.0-1ubuntu2.1) ...
Removing libldap-2.4-2:i386 (2.4.42+dfsg-2ubuntu3.1) ...
Removing libgssapi3-heimdal:i386 (1.7~git20150920+dfsg-4ubuntu1) ...
Removing libheimntlm0-heimdal:i386 (1.7~git20150920+dfsg-4ubuntu1) ...
Removing libkrb5-26-heimdal:i386 (1.7~git20150920+dfsg-4ubuntu1) ...
Removing libhx509-5-heimdal:i386 (1.7~git20150920+dfsg-4ubuntu1) ...
Removing libsdl1.2debian:i386 (1.2.15+dfsg1-3) ...
Removing libasound2:i386 (1.1.0-0ubuntu1) ...
Removing libpulse0:i386 (1:8.0-0ubuntu3) ...
Removing libasyncns0:i386 (0.8-5build1) ...
Removing libqt5printsupport5:i386 (5.5.1+dfsg-16ubuntu7.1) ...
Removing libcups2:i386 (2.1.3-4) ...
Removing libavahi-client3:i386 (0.6.32~rc+dfsg-1ubuntu2) ...
Removing libavahi-common3:i386 (0.6.32~rc+dfsg-1ubuntu2) ...
Removing libavahi-common-data:i386 (0.6.32~rc+dfsg-1ubuntu2) ...
Removing libgnome-2-0:amd64 (2.32.1-5ubuntu1) ...
Removing libbonobo2-0:amd64 (2.32.1-3) ...
Removing libbonobo2-common (2.32.1-3) ...
Removing libcaca0:i386 (0.99.beta19-2build2~gcc5.2) ...
Removing libqt5opengl5:i386 (5.5.1+dfsg-16ubuntu7.1) ...
Removing libqt5svg5:i386 (5.5.1-2build1) ...
Removing libqt5widgets5:i386 (5.5.1+dfsg-16ubuntu7.1) ...
Removing libenca0:amd64 (1.18-1) ...
Removing libsndfile1:i386 (1.0.25-10) ...
Removing libflac8:i386 (1.3.1-4) ...
Removing libqt5x11extras5:i386 (5.5.1-3build1) ...
Removing librtmp1:i386 (2.4+20151223.gitfa8646d-1build1) ...
Removing libgnutls30:i386 (3.4.10-4ubuntu1.1) ...
Removing libhogweed4:i386 (3.2-1) ...
Removing libgmp10:i386 (2:6.1.0+dfsg-2) ...
Removing libgnome2-common (2.32.1-5ubuntu1) ...
Removing libgnomevfs2-0:amd64 (1:2.24.4-6.1ubuntu1) ...
Removing libgnomevfs2-common (1:2.24.4-6.1ubuntu1) ...
Removing libgssapi-krb5-2:i386 (1.13.2+dfsg-5) ...
Removing libhcrypto4-heimdal:i386 (1.7~git20150920+dfsg-4ubuntu1) ...
Removing libheimbase1-heimdal:i386 (1.7~git20150920+dfsg-4ubuntu1) ...
Removing libxmu6:i386 (2:1.1.2-2) ...
Removing libxt6:i386 (1:1.1.5-0ubuntu1) ...
Removing libxml2:i386 (2.9.3+dfsg1-1ubuntu0.1) ...
Removing libidn11:i386 (1.32-3ubuntu1.1) ...
Removing libjson-c2:i386 (0.11-4ubuntu2) ...
Removing libkrb5-3:i386 (1.13.2+dfsg-5) ...
Removing libk5crypto3:i386 (1.13.2+dfsg-5) ...
Removing libkeyutils1:i386 (1.5.9-8ubuntu1) ...
Removing libkrb5support0:i386 (1.13.2+dfsg-5) ...
Removing libnettle6:i386 (3.2-1) ...
Removing libvorbisenc2:i386 (1.3.5-3) ...
Removing libvorbis0a:i386 (1.3.5-3) ...
Removing libogg0:i386 (1.3.2-1) ...
Removing liborbit-2-0:amd64 (1:2.14.19-1build1) ...
Removing libp11-kit0:i386 (0.23.2-5~ubuntu16.04.1) ...
Removing libpython2.7:i386 (2.7.12-1~16.04) ...
Removing libpython2.7-stdlib:i386 (2.7.12-1~16.04) ...
Removing libpython2.7-minimal:i386 (2.7.12-1~16.04) ...
Removing libreadline6:i386 (6.3-8ubuntu2) ...
Removing libwind0-heimdal:i386 (1.7~git20150920+dfsg-4ubuntu1) ...
Removing libsasl2-2:i386 (2.1.26.dfsg1-14build1) ...
Removing libsasl2-modules:i386 (2.1.26.dfsg1-14build1) ...
Removing libsasl2-modules-db:i386 (2.1.26.dfsg1-14build1) ...
Removing libslang2:i386 (2.3.0-2ubuntu1) ...
Removing libsqlite3-0:i386 (3.11.0-1ubuntu1) ...
Removing libssl1.0.0:i386 (1.0.2g-1ubuntu4.5) ...
Removing libtasn1-6:i386 (4.7-3ubuntu0.16.04.1) ...
Removing libvorbisidec1 (1.0.2+svn18153-0.2) ...
Removing libvpx3:i386 (1.5.0-2ubuntu1) ...
Removing libwrap0:i386 (7.6.q-25) ...
Removing libxcursor1:i386 (1:1.1.14-1) ...
Removing libxinerama1:i386 (2:1.1.3-1) ...
Removing linux-headers-4.4.0-34-generic (4.4.0-34.53) ...
Removing linux-headers-4.4.0-34 (4.4.0-34.53) ...
Removing linux-image-extra-4.4.0-34-generic (4.4.0-34.53) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
Error! Your kernel headers for kernel 4.4.0-34-generic cannot be found.
Please install the linux-headers-4.4.0-34-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-34-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-38-generic
Found initrd image: /boot/initrd.img-4.4.0-38-generic
Found linux image: /boot/vmlinuz-4.4.0-36-generic
Found initrd image: /boot/initrd.img-4.4.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-34-generic
Found initrd image: /boot/initrd.img-4.4.0-34-generic
Found linux image: /boot/vmlinuz-4.2.0-42-generic
Found initrd image: /boot/initrd.img-4.2.0-42-generic
Found linux image: /boot/vmlinuz-4.2.0-41-generic
Found initrd image: /boot/initrd.img-4.2.0-41-generic
Found linux image: /boot/vmlinuz-4.2.0-38-generic
Found initrd image: /boot/initrd.img-4.2.0-38-generic
Found linux image: /boot/vmlinuz-4.2.0-36-generic
Found initrd image: /boot/initrd.img-4.2.0-36-generic
Found linux image: /boot/vmlinuz-4.2.0-35-generic
Found initrd image: /boot/initrd.img-4.2.0-35-generic
Found linux image: /boot/vmlinuz-4.2.0-34-generic
Found initrd image: /boot/initrd.img-4.2.0-34-generic
Found linux image: /boot/vmlinuz-4.2.0-30-generic
Found initrd image: /boot/initrd.img-4.2.0-30-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Removing linux-image-4.4.0-34-generic (4.4.0-34.53) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-38-generic
Found initrd image: /boot/initrd.img-4.4.0-38-generic
Found linux image: /boot/vmlinuz-4.4.0-36-generic
Found initrd image: /boot/initrd.img-4.4.0-36-generic
Found linux image: /boot/vmlinuz-4.2.0-42-generic
Found initrd image: /boot/initrd.img-4.2.0-42-generic
Found linux image: /boot/vmlinuz-4.2.0-41-generic
Found initrd image: /boot/initrd.img-4.2.0-41-generic
Found linux image: /boot/vmlinuz-4.2.0-38-generic
Found initrd image: /boot/initrd.img-4.2.0-38-generic
Found linux image: /boot/vmlinuz-4.2.0-36-generic
Found initrd image: /boot/initrd.img-4.2.0-36-generic
Found linux image: /boot/vmlinuz-4.2.0-35-generic
Found initrd image: /boot/initrd.img-4.2.0-35-generic
Found linux image: /boot/vmlinuz-4.2.0-34-generic
Found initrd image: /boot/initrd.img-4.2.0-34-generic
Found linux image: /boot/vmlinuz-4.2.0-30-generic
Found initrd image: /boot/initrd.img-4.2.0-30-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Removing libasn1-8-heimdal:i386 (1.7~git20150920+dfsg-4ubuntu1) ...
Removing libqt5gui5:i386 (5.5.1+dfsg-16ubuntu7.1) ...
Removing libqt5network5:i386 (5.5.1+dfsg-16ubuntu7.1) ...
Removing libqt5dbus5:i386 (5.5.1+dfsg-16ubuntu7.1) ...
Removing libdbus-1-3:i386 (1.10.6-1ubuntu3) ...
Removing libegl1-mesa:i386 (11.2.0-1ubuntu2.2) ...
Removing libinput10:i386 (1.2.3-1ubuntu1) ...
Removing libevdev2:i386 (1.4.6+dfsg-1) ...
Removing libfontconfig1:i386 (2.11.94-0ubuntu1.1) ...
Removing libharfbuzz0b:i386 (1.0.1-1ubuntu0.1) ...
Removing libfreetype6:i386 (2.6.1-0.1ubuntu2) ...
Removing libgbm1:i386 (11.2.0-1ubuntu2.2) ...
Removing libsystemd0:i386 (229-4ubuntu8) ...
Removing libgcrypt20:i386 (1.6.5-2ubuntu0.2) ...
Removing libqt5core5a:i386 (5.5.1+dfsg-16ubuntu7.1) ...
Removing libgraphite2-3:i386 (1.3.6-1ubuntu1) ...
Removing libwacom2:i386 (0.18-1) ...
Removing libgudev-1.0-0:i386 (1:230-2) ...
Removing libsm6:i386 (2:1.2.2-1) ...
Removing libice6:i386 (2:1.0.9-1) ...
Removing libicu55:i386 (55.1-7) ...
Removing libjpeg8:i386 (8c-2ubuntu8) ...
Removing libjpeg-turbo8:i386 (1.4.2-0ubuntu3) ...
Removing libmtdev1:i386 (1.1.5-1ubuntu2) ...
Removing libpcre16-3:i386 (2:8.38-3.1) ...
Removing libpng12-0:i386 (1.2.54-1ubuntu1) ...
Removing libproxy1v5:i386 (0.4.11-5ubuntu1) ...
Removing libroken18-heimdal:i386 (1.7~git20150920+dfsg-4ubuntu1) ...
Removing libwayland-client0:i386 (1.9.0-1) ...
Removing libwayland-server0:i386 (1.9.0-1) ...
Removing libxcb-icccm4:i386 (0.4.1-1ubuntu1) ...
Removing libxcb-image0:i386 (0.4.0-1build1) ...
Removing libxcb-keysyms1:i386 (0.4.0-1) ...
Removing libxcb-randr0:i386 (1.11.1-1ubuntu1) ...
Removing libxcb-render-util0:i386 (0.3.9-1) ...
Removing libxcb-render0:i386 (1.11.1-1ubuntu1) ...
Removing libxcb-shape0:i386 (1.11.1-1ubuntu1) ...
Removing libxcb-shm0:i386 (1.11.1-1ubuntu1) ...
Removing libxcb-util1:i386 (0.4.0-0ubuntu3) ...
Removing libxcb-xfixes0:i386 (1.11.1-1ubuntu1) ...
Removing libxkbcommon-x11-0:i386 (0.5.0-1ubuntu2) ...
Removing libxcb-xkb1:i386 (1.11.1-1ubuntu1) ...
Removing libxi6:i386 (2:1.7.6-1) ...
Removing libxkbcommon0:i386 (0.5.0-1ubuntu2) ...
Removing libxrender1:i386 (1:0.9.9-0ubuntu1) ...
Removing libglib2.0-0:i386 (2.48.1-1~ubuntu16.04.1) ...
Removing openjdk-8-jre-headless:amd64 (8u91-b14-3ubuntu1~16.04.1) ...
Removing ca-certificates-java (20160321) ...
Removing java-common (0.56ubuntu2) ...
Processing triggers for fontconfig (2.11.94-0ubuntu1.1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for gconf2 (3.2.6-3ubuntu6) ...
Processing triggers for ca-certificates (20160104ubuntu1) ...
Updating certificates in /etc/ssl/certs...
0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d...

updates of cacerts keystore disabled.
done.
larry3d@larry3d:~$ 




```

---

### Post by ian-weisser on 2016-10-13
Ensure all those PPAs are really unchecked or deleted.

Then make sure old PPA packages are not sill in your cache: 'sudo apt autoclean'

Then install wine: 'sudo apt install wine'

---

### Post by larry41 on 2016-10-13
ok i deselect all the PPA and here is the proof [ATTACH=CONFIG]271600[/ATTACH] after that i did this command because i guess that should be next sudo apt autoremove

and this is the result

 ```

larry3d@larry3d:~$ sudo apt autoremove 
[sudo] password for larry3d: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libbz2-1.0:i386 libdb5.3:i386 libdevmapper1.02.1:i386 libgpg-error0:i386
  libncursesw5:i386
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
After this operation, 3,175 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 464581 files and directories currently installed.)
Removing libbz2-1.0:i386 (1.0.6-8) ...
Removing libdb5.3:i386 (5.3.28-11) ...
Removing libdevmapper1.02.1:i386 (2:1.02.110-1ubuntu10) ...
Removing libgpg-error0:i386 (1.21-2ubuntu1) ...
Removing libncursesw5:i386 (6.0+20160213-1ubuntu1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
larry3d@larry3d:~$ ^C
larry3d@larry3d:~$ 




```

after all that i did the next command sudo apt autoclean and this is the result 
```

larry3d@larry3d:~$ sudo apt autoclean
[sudo] password for larry3d: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
larry3d@larry3d:~$ ^C
larry3d@larry3d:~$ 



```

then by following every step i type this on terminal sudo apt install wine and this is what i got 

```

larry3d@larry3d:~$ sudo apt install wine
[sudo] password for larry3d: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is a virtual package provided by:
  wine1.6 1:1.6.2-0ubuntu14 [Not candidate version]

E: Package 'wine' has no installation candidate
larry3d@larry3d:~$ 






```

wine has no installation candidate? what that means i don't get it is not suppost that everything is installed these days through terminal?

---

### Post by ian-weisser on 2016-10-13
Apt did tell you the next step to try: 'sudo apt install wine1.6'

---

### Post by larry41 on 2016-10-13
i just did that command on terminal sudo apt install wine 1.6


```


larry3d@larry3d:~$ sudo apt install wine1.6
[sudo] password for larry3d: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine1.6 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'wine1.6' has no installation candidate
larry3d@larry3d:~$ 






```

:confused:

---

### Post by ian-weisser on 2016-10-13
You were supposed to uncheck the just the PPAs in the 'Other Software' tab, not everything.
When you unchecked the Main repository, you told your system to stop using it. You need it. That's where Wine is.

You need to go back you your sources, disable the PPAs, and enable the Ubuntu Main repository.

---

### Post by larry41 on 2016-10-13
here is what i did and i activate the first tab with the PPA as the pictures shows [ATTACH=CONFIG]271602[/ATTACH] than i went to the second tab and i desactivated everything as the picture shows [ATTACH=CONFIG]271603[/ATTACH] than i went to terminal and i did all over again first sudo apt autoremove
```

larry3d@larry3d:~$ sudo apt autoremove 
[sudo] password for larry3d: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
larry3d@larry3d:~$ 




```

after that i did this sudo apt autoclean and this came

 ```

larry3d@larry3d:~$ sudo apt autoclean
[sudo] password for larry3d: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
larry3d@larry3d:~$ ^C
larry3d@larry3d:~$ 



```

than because i don't want to miss anything i did this sudo apt install wine
```

larry3d@larry3d:~$ sudo apt install wine
[sudo] password for larry3d: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.6 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
larry3d@larry3d:~$ 




```
but than because i know that i need wine 1.6 i did this on terminal sudo apt install wine1.6
```

larry3d@larry3d:~$ sudo apt install wine1.6
[sudo] password for larry3d: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.6 : Depends: wine1.6-i386 (= 1:1.6.2-0ubuntu14)
E: Unable to correct problems, you have held broken packages.
larry3d@larry3d:~$ 




```
am i'm missing something?

---

### Post by ian-weisser on 2016-10-14
You enabled *all* the Ubuntu repositories by checking all those boxes, including Restricted and Source Code. That is unwise.
If you read up, I merely suggested enabling Main.

Anyway, let's follow the trail of bread crumbs until we discover the problem.
Try 'sudo apt install wine1.6-i386'

---

### Post by larry41 on 2016-10-14
holly moly i did that command on terminal sudo apt install wine1.6-i386 and i got bad news well thats what i guess


```


larry3d@larry3d:~$ sudo apt install wine1.6-i386
[sudo] password for larry3d: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.6-i386:i386 : Depends: libgphoto2-6:i386 (>= 2.5.9) but it is not going to be installed
                     Depends: libldap-2.4-2:i386 (>= 2.4.7) but it is not going to be installed
                     Depends: libxml2:i386 (>= 2.9.0) but it is not going to be installed
                     Recommends: libasound2-plugins:i386 but it is not going to be installed
                     Recommends: libcups2:i386 but it is not going to be installed
                     Recommends: libdbus-1-3:i386 but it is not going to be installed
                     Recommends: libfontconfig1:i386 but it is not going to be installed or
                                 libfontconfig:i386
                     Recommends: libgnutls30:i386 but it is not going to be installed
                     Recommends: libosmesa6:i386 but it is not going to be installed
                     Recommends: libpulse0:i386 but it is not going to be installed
                     Recommends: libsane:i386 but it is not going to be installed
                     Recommends: libxslt1.1:i386 but it is not going to be installed
                     Recommends: p11-kit-modules:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
larry3d@larry3d:~$ 




```

after that i decided to do what you suggest so i went to softwares updates and i did what the picture shows [ATTACH=CONFIG]271604[/ATTACH]  but maybe i need to start all over again lol. oh man i'm getting crazy

ok and i did it all over again keeping in mind to disable restricted  and source code on the first tab, after that i did all the commands on terminal but this time in one window

 ```


larry3d@larry3d:~$ sudo apt autoremove 
[sudo] password for larry3d: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
larry3d@larry3d:~$ sudo apt autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
larry3d@larry3d:~$ sudo apt install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.6 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
larry3d@larry3d:~$ sudo apt install wine1.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.6 : Depends: wine1.6-i386 (= 1:1.6.2-0ubuntu14)
E: Unable to correct problems, you have held broken packages.
larry3d@larry3d:~$ 




```

i only see broken packages :confused:

---

### Post by ian-weisser on 2016-10-14
Run the following command: 'apt rdepends libgphoto2-6'

Look at all the results.
Did you install any of those results from a PPA or non-Ubuntu source?

If not, please show us the output of these three commands:
```
apt policy libgphoto2-6
apt policy libldap-2.4-2
apt policy libxml2
```

---

### Post by larry41 on 2016-10-14
ok i open my terminal and i did  "apt rdepends libgphoto2-6"

```


larry3d@larry3d:~$ apt rdepends libgphoto2-6
libgphoto2-6
Reverse Depends:
  Depends: libsane (>= 2.5.2)
  Depends: gvfs-backends (>= 2.5.9)
  Depends: wine1.6-amd64 (>= 2.5.9)
  Depends: python3-gphoto2cffi (>= 2.5.9)
  Depends: python-piggyphoto
  Depends: python-gphoto2cffi (>= 2.5.9)
  Depends: kamera (>= 2.5.9)
  Depends: gtkam-gimp (>= 2.5.2)
  Depends: gtkam (>= 2.5.2)
  Recommends: gthumb
  Depends: gphotofs (>= 2.5.2)
  Depends: gphoto2 (>= 2.5.9)
  Depends: entangle (>= 2.5.9)
  Depends: digikam (>= 2.5.9)
  Depends: darktable (>= 2.5.9)
  Depends: camera.app (>= 2.5.2)
  Depends: shotwell (>= 2.5.9)
  Depends: libgphoto2-dev (= 2.5.9-3)
  Depends: gvfs-backends (>= 2.5.9)
larry3d@larry3d:~$ 




```

NO i haven't install any of those results from a PPA or non-Ubuntu source

```

larry3d@larry3d:~$ apt policy libgphoto2-6
libgphoto2-6:
  Installed: 2.5.9-3
  Candidate: 2.5.9-3
  Version table:
 *** 2.5.9-3 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
larry3d@larry3d:~$ 


```

```

larry3d@larry3d:~$ apt policy libldap-2.4-2
libldap-2.4-2:
  Installed: 2.4.42+dfsg-2ubuntu3.1
  Candidate: 2.4.42+dfsg-2ubuntu3.1
  Version table:
 *** 2.4.42+dfsg-2ubuntu3.1 100
        100 /var/lib/dpkg/status
     2.4.42+dfsg-2ubuntu3 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
larry3d@larry3d:~$ 

```

```


larry3d@larry3d:~$ apt policy libxml2
libxml2:
  Installed: 2.9.3+dfsg1-1ubuntu0.1
  Candidate: 2.9.3+dfsg1-1ubuntu0.1
  Version table:
 *** 2.9.3+dfsg1-1ubuntu0.1 100
        100 /var/lib/dpkg/status
     2.9.3+dfsg1-1 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
larry3d@larry3d:~$ 



```

---

### Post by ian-weisser on 2016-10-14
Ah, go to your Sources, and enable Xenial-Updates and Xenial-Security.
Then sudo apt update
Then sudo apt upgrade
Then sudo apt install wine

---

### Post by larry41 on 2016-10-15
i open Softwares Updates and i enable Xenial-Updates and also Xenial-Security as the pictures shows [ATTACH=CONFIG]271629[/ATTACH] then i went to terminal and i type all those commands 
 sudo apt update
 sudo apt upgrade
 sudo apt install wine

i'm not writting the outputs of terminal because i did all that last night and i was struggling posting all the steps but whatever :) after doing all those commands this is what i got as the pictures shows[ATTACH=CONFIG]271632[/ATTACH] [ATTACH=CONFIG]271630[/ATTACH][ATTACH=CONFIG]271631[/ATTACH]  now i have to say thank you everyone for your help. it took kind of while to install wine but now wine is running perfectly on my computer, and i learned a lot from all this. just follow all the indications of the developers and be nice with them, sometimes they are busy taking care of others but just wait  and wait :) they will answer your questions

---

### Post by ian-weisser on 2016-10-15
Congratulation!
Very pleased to see that you have successfully installed Wine.

---

