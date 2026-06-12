---
title: "[SOLVED] Could not download all repository indexes"
date: 2007-06-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by PaulRSte on 2007-06-24
I'm a newcomer to linux, so before setting out to build a Mythtv system, I first of all installed 
feisty 32 bit edition under VMWare on my XP system.  This went surprisingly well, including installing and configuring Mythtv itself.  I couldn't view TV programs on this as VMWare won't use the PCI tuner, but having got that far I decided to go ahead and build a system.

I now have an Antec Fusion case with an Asus M2NPV-VM motherboard with AMD 64 X2 and 2GB RAM and a Nova T-500 dual tuner card, and have installed the 64 bit version of Feisty.

I was getting lots of error messages using apt-get even after a complete reinstall of Feisty.  As my test rig on my XP machine still runs apt-get ok, I copied the /etc/apt/sources.list to the new system, then went into synaptic package manager and did a reload which produces the following error :-

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://gb.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-amd64/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-amd64/Packages.gz:) Sub-process gzip returned an error code (1)
[http://gb.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-amd64/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-amd64/Packages.gz:) Sub-process gzip returned an error code (1)

This process runs error free on my test system.   I have checked the network and proxy settings on both systems and are both using DHCP to obtain network settings and the Proxy settings are both set to direct connection.

Can anyone assist please?

---

### Post by Mr_bleu on 2007-06-24
If I understand correctly, you copied the 32 bit repository addresses into your 64 bit system?   That might be where the errors are coming from.  The 64 bit has its own repositories.

---

### Post by jamesford on 2007-06-24
i thought the 32 and 64 bit repos were the same
it might just be a matter of a server being temporarily down

---

### Post by Mr_bleu on 2007-06-24
No, they aren't the same. If you try downloading a 32 bit program from the 64 bit repositories using apt-get it will error out. Why would they have 32 bit repositories and 64 bit ones if they were the same?

---

### Post by jamesford on 2007-06-24
the lines in sources.list are the same at least

---

### Post by Mr_bleu on 2007-06-24
In a terminal run sudo apt-get check & sudo apt-get update.

---

### Post by PaulRSte on 2007-06-24
Still getting same errors as below:-


paul@PVR-1:~$ sudo apt-get check
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
paul@PVR-1:~$ sudo apt-get update
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release.gpg [191B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Translation-en_GB                 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Translation-en_GB         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Translation-en_GB
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release             
Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Packages [4850kB]
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Packages [183kB]
99% [4 Packages gzip 0] [Waiting for headers]
gzip: stdin: not in gzip format
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Packages
  Sub-process gzip returned an error code (1)
99% [5 Packages gzip 0] [Waiting for headers]
gzip: stdin: not in gzip format
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Packages
  Sub-process gzip returned an error code (1)
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Fetched 5B in 0s (6B/s)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-amd64/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-amd64/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-amd64/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-amd64/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
paul@PVR-1:~$ 
paul@PVR-1:~$

---

### Post by Mr_bleu on 2007-06-24
have you tried System>administration>Synaptic Package Manager>Edit>fix broken packages?

---

### Post by PaulRSte on 2007-06-24
Selected all packages in package manager and did fix-broken-packages which reported a sucess.  Then tried a reload and got same error as originally logged.  Still complaining about Packages.gz.  NB That this wasn't in the list of packages  in package manager

---

### Post by PaulRSte on 2007-06-25
I have just found another thread that suggests changing http to ftp in /etc/apt/sources.list.  I have tried this for the two repositories giving the error and now get an error saying that the file size reported by the server is incorrect - see below.  It looks as though the indexes have downloaded ok though as when I try to install mythtv I no longer get "cannot find package" but instead get a long list of packages to install.  Will see where I get to from here.

paul@PVR-1:~$ sudo apt-get update
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release.gpg [191B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Translation-en_GB                 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Translation-en_GB           
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release.gpg [191B]          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Translation-en_GB         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release                        
Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_GB          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Packages                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Sources                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Packages                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Sources                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Sources             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_GB    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Get: 4 [ftp://gb.archive.ubuntu.com](ftp://gb.archive.ubuntu.com) feisty Release.gpg [191B]
Get: 5 [ftp://gb.archive.ubuntu.com](ftp://gb.archive.ubuntu.com) feisty/universe Translation-en_GB
Ign [ftp://gb.archive.ubuntu.com](ftp://gb.archive.ubuntu.com) feisty/universe Translation-en_GB
Hit [ftp://gb.archive.ubuntu.com](ftp://gb.archive.ubuntu.com) feisty/multiverse Translation-en_GB
Get: 6 [ftp://gb.archive.ubuntu.com](ftp://gb.archive.ubuntu.com) feisty Release [57.2kB]
Get: 7 [ftp://gb.archive.ubuntu.com](ftp://gb.archive.ubuntu.com) feisty/universe Packages [3702kB]           
Hit [ftp://gb.archive.ubuntu.com](ftp://gb.archive.ubuntu.com) feisty/universe Sources                        
Get: 8 [ftp://gb.archive.ubuntu.com](ftp://gb.archive.ubuntu.com) feisty/multiverse Packages [142kB]          
Hit [ftp://gb.archive.ubuntu.com](ftp://gb.archive.ubuntu.com) feisty/multiverse Sources                      
Fetched 3902kB in 18s (210kB/s)                                                
Reading package lists... Done
W: Bizarre Error - File size is not what the server reported 3702498 4850445
W: Bizarre Error - File size is not what the server reported 141715 183429
W: You may want to run apt-get update to correct these problems
paul@PVR-1:~$

---

### Post by PaulRSte on 2007-06-29
Went through the rest of the mythtv install as described at [http://parker1.co.uk](http://parker1.co.uk) and everything worked like a charm.  No errors and now able to watch TV on mythtv.  Just some final tweaking to do.

---

