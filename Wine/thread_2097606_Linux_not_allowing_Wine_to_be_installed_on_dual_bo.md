---
title: "Linux not allowing Wine to be installed on dual boot Windows 7"
date: 2012-12-23
forum: Wine
---

### Post by send2 on 2012-12-23
Is there a section here where i can ask about the Wine program? i am  using Linux Ubuntu 12.10 Quetzal on a Toshiba laptop, on Windows 7 with  19 GB partitioned for Linux. I am dual booting with WIndows 7. Here is some additional info about my system:  

Ubuntu 12.10, Memory 3.9GB, processor: Intel Core 2 Duo CPU T600 @ 2.20GHz x2, OS type 64 bit. 

Here is the message I got when I tried to install Wine from the software center and also trying from the terminal and Wine website:

warrior@ubuntu:~$ sudo add-apt-repository ppa:ubuntu-wine/ppa
[sudo] password for warrior: 
You are about to add the following PPA to your system:
 Welcome  to the Wine Team PPA.  Here you can get the latest available Wine betas  for every supported version of Ubuntu.  This PPA is managed by Scott  Ritchie and Maarten Lankhorst.
 More info: [https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpbdj_x9/secring.gpg' created
gpg: keyring `/tmp/tmpbdj_x9/pubring.gpg' created
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpbdj_x9/trustdb.gpg: trustdb created
gpg: key F9CB8DB0: public key "Launchpad PPA for Ubuntu Wine Team" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
warrior@ubuntu:~$ sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal InRelease                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal InRelease                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg          
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release.gpg                 
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg [316 B]           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates InRelease              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release              
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release                     
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release [11.9 kB]              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release.gpg                              
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates Release.gpg [933 B]            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main amd64 Packages            
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner amd64 Packages       
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources [2,425 B]         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted amd64 Packages      
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages [3,001 B]           
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates Release [49.6 kB]              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe amd64 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse amd64 Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main amd64 Packages                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted amd64 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe amd64 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse amd64 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en_US    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Translation-en             
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Translation-en
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main amd64 Packages [158 kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted amd64 Packages [1,970 B]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe amd64 Packages [135 kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_US
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse amd64 Packages [7,936 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Translation-en_US                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Translation-en_US       
Fetched 371 kB in 9s (40.8 kB/s)                                               
Reading package lists... Done
warrior@ubuntu:~$ sudo apt-get install wine1.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.4 : Depends: wine1.4-i386 (= 1.4.1-0ubuntu1) but it is not installable
           Recommends: gnome-exe-thumbnailer but it is not going to be installed or
                       kde-runtime but it is not going to be installed
           Recommends: ttf-droid
           Recommends: ttf-mscorefonts-installer but it is not going to be installed
           Recommends: ttf-umefont but it is not going to be installed
           Recommends: ttf-unfonts-core but it is not going to be installed
           Recommends: winbind but it is not going to be installed
           Recommends: winetricks but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
warrior@ubuntu:~$ 

I  installed as indicated by the Wine website their WineHQ PPA repository  and after that I tried installing their latest stable version Wine 1.4  64 bit. and still no dice.

Any ideas about what I need to do next? I am trying to use Wine for old  Windows games. 

I am a noob, just installed  Linux yesterday! :D

TIA

---

### Post by cariboo on 2012-12-23
Moved to the Wine sub-forum.

---

### Post by TOMBSTONEV2 on 2012-12-24
Have you tried:  ```
 sudo apt-get install wine
``` I'm sure this will get the latest on there as it did for my ubuntu 12.04 LTS

---

### Post by send2 on 2012-12-24
Hi tombstonev2, I still get the same installation error: here is what I get from the terminal:


warrior@ubuntu:~$  sudo apt-get install wine
[sudo] password for warrior: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.5 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
warrior@ubuntu:~$ 

thanks for your reply

---

### Post by Georgia boy on 2012-12-24
> **send2 said:**
> Hi tombstonev2, I still get the same installation error: here is what I get from the terminal:


warrior@ubuntu:~$  sudo apt-get install wine
[sudo] password for warrior: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.5 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
warrior@ubuntu:~$ 

thanks for your reply

I'm not that up on Wine but did you try going from Repos or Synaptic Package Manager and install that way? I know hat you can repair broken packages there. That might be a shot to go into package manager and do the repair package bit to see if that will help with allowing the install. Again, I'm not up on Wine and have only installed it once a while back.

GB

---

### Post by TOMBSTONEV2 on 2012-12-24
Try this:

```
sudo apt-get autoremove wine
```

```
sudo apt-get update
```

```
sudo apt-get autoclean
```

```
sudo apt-get clean
```

```
sudo apt-get autoremove
```

```
sudo apt-get install wine
```

If that doesn't work we will have to identify exactly what packages are broken.

---

### Post by orb9220 on 2012-12-25
- Is the systems have multiarch if not enabled is simple to do so

> Code: Select all

    sudo dpkg --add-architecture i386


Code: Select all

    apt update

Fixed my issue and allowed me to intall wine.
.

---

### Post by send2 on 2012-12-26
> **Georgia boy said:**
> I'm not that up on Wine but did you try going from Repos or Synaptic Package Manager and install that way? I know hat you can repair broken packages there. That might be a shot to go into package manager and do the repair package bit to see if that will help with allowing the install. Again, I'm not up on Wine and have only installed it once a while back.

GB

Hi Georgia boy, i tried to install from there and got the same errors as above. I tried to install Wine from the software manager, also from the Wine website, and from the terminal. I don't yet know how to repair packages. Just got the OS :) Thanks for your reply.

> **TOMBSTONEV2 said:**
> Try this:

```
sudo apt-get autoremove wine
``````
sudo apt-get update
``````
sudo apt-get autoclean
``````
sudo apt-get clean
``````
sudo apt-get autoremove
``````
sudo apt-get install wine
```If that doesn't work we will have to identify exactly what packages are broken.

thanks again, i will have to wait until Friday or Saturday when I will  have a new hard drive. I had installed Ubuntu until late list night  until i read an article online on installing wine using the terminal.  Well the commands wiped out all my software packages and now i have to  reinstall Ubuntu. But i am going to do it on a separate drive. I don't  want to have problems with my Windows pc. Since I am new to this OS, it  makes sense to have a separate hard drive in case  I mess up, i don't  loose important files. I will come back to this thread after I install  Ubuntu on my new drive and try the advice you and other posters here  have kindly given me. I will keep you and other posters here posted.


> **orb9220 said:**
> - Is the systems have multiarch if not enabled is simple to do so 

Fixed my issue and allowed me to intall wine.
.

Hi orb9220, thanks for your help, can you be more specific please? I just installed the OS and am very new to Linux. I am reading a lot now on this OS and the more I read the more I like :)

---

### Post by send2 on 2013-01-07
Update to thread: I am reading on how to partition my new hard drive. I removed Ubuntu from my Windows hard disk, not a lot of space left. Now to check on how to partition, thanks to all of you who helped :)

---

### Post by send2 on 2013-01-12
One last reply for this thread. I have installed Ubuntu on a separate hard drive and have installed Wine. I will mark this thread closed. Thanks to all again.

---

