---
title: "Chrubuntu WINE/PlayOnLinux Help"
date: 2014-03-27
forum: Wine
---

### Post by David_Estes on 2014-03-27
Hello,

I've recently moved my Acer C7 Chromebook from Chrome OS to Chrubuntu. I found out about PlayOnLinux because I want to play WoW but whenever I open PlayOnLinux, it says this: 

[I]PlayOnLinux is unable to find 32bits OpenGL libraries.

You might encounter problem with your games
[/I]
and also this:
[I]
PlayOnLInux cannot find wine (from Wine)

You should install it to play PlayOnLinux
[/I]
So I ignored the first message but the second got me confused. I tried to install WoW but in the middle of the PlayOnLinux Wizard or whatever it was, it stopped (I can't seem to copy and paste the error). I then tried installing WINE but I got an error. This is my log:

```
user@chrubuntu:~$ sudo add-apt-repository ppa:ubuntu-wine/ppa
[sudo] password for user: 
 Welcome to the Wine Team PPA.  Here you can get the latest available Wine betas for every supported version of Ubuntu.  This PPA is managed by Scott Ritchie and Maarten Lankhorst.
 More info: https://launchpad.net/~ubuntu-wine/+archive/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it


gpg: keyring `/tmp/tmpru0lq7/secring.gpg' created
gpg: keyring `/tmp/tmpru0lq7/pubring.gpg' created
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpru0lq7/trustdb.gpg: trustdb created
gpg: key F9CB8DB0: public key "Launchpad PPA for Ubuntu Wine Team" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
user@chrubuntu:~$ sudo apt-get update
Ign http://dl.google.com stable InRelease
Ign http://archive.ubuntu.com saucy InRelease                            
Ign http://archive.ubuntu.com saucy-updates InRelease                    
Get:1 http://dl.google.com stable Release.gpg [198 B]
Ign http://archive.ubuntu.com saucy-security InRelease                         
Get:2 http://dl.google.com stable Release [1351 B]                   
Hit http://archive.ubuntu.com saucy Release.gpg                                
Ign http://ppa.launchpad.net saucy InRelease                            
Get:3 http://archive.ubuntu.com saucy-updates Release.gpg [933 B]       
Get:4 http://archive.ubuntu.com saucy-security Release.gpg [933 B]             
Get:5 http://dl.google.com stable/main amd64 Packages [1259 B]        
Get:6 http://ppa.launchpad.net saucy Release.gpg [316 B]              
Hit http://archive.ubuntu.com saucy Release                                    
Get:7 http://archive.ubuntu.com saucy-updates Release [49.6 kB]                
Get:8 http://ppa.launchpad.net saucy Release [11.8 kB]                         
Get:9 http://archive.ubuntu.com saucy-security Release [49.6 kB]               
Get:10 http://ppa.launchpad.net saucy/main amd64 Packages [4776 B]           
Ign http://dl.google.com stable/main Translation-en                            
Hit http://archive.ubuntu.com saucy/main Sources                      
Hit http://archive.ubuntu.com saucy/restricted Sources
Hit http://archive.ubuntu.com saucy/universe Sources
Hit http://archive.ubuntu.com saucy/multiverse Sources
Hit http://archive.ubuntu.com saucy/main amd64 Packages
Hit http://archive.ubuntu.com saucy/restricted amd64 Packages
Hit http://archive.ubuntu.com saucy/universe amd64 Packages
Hit http://archive.ubuntu.com saucy/multiverse amd64 Packages
Ign http://ppa.launchpad.net saucy/main Translation-en
Hit http://archive.ubuntu.com saucy/main Translation-en
Hit http://archive.ubuntu.com saucy/multiverse Translation-en
Hit http://archive.ubuntu.com saucy/restricted Translation-en
Hit http://archive.ubuntu.com saucy/universe Translation-en
Get:11 http://archive.ubuntu.com saucy-updates/main Sources [80.6 kB]
Get:12 http://archive.ubuntu.com saucy-updates/restricted Sources [14 B]
Get:13 http://archive.ubuntu.com saucy-updates/universe Sources [67.9 kB]
Get:14 http://archive.ubuntu.com saucy-updates/multiverse Sources [1348 B]
Get:15 http://archive.ubuntu.com saucy-updates/main amd64 Packages [223 kB]
Get:16 http://archive.ubuntu.com saucy-updates/restricted amd64 Packages [14 B]
Get:17 http://archive.ubuntu.com saucy-updates/universe amd64 Packages [158 kB]
Get:18 http://archive.ubuntu.com saucy-updates/multiverse amd64 Packages [1552 B]
Hit http://archive.ubuntu.com saucy-updates/main Translation-en
Hit http://archive.ubuntu.com saucy-updates/multiverse Translation-en
Hit http://archive.ubuntu.com saucy-updates/restricted Translation-en
Hit http://archive.ubuntu.com saucy-updates/universe Translation-en
Get:19 http://archive.ubuntu.com saucy-security/main Sources [38.8 kB]
Get:20 http://archive.ubuntu.com saucy-security/restricted Sources [14 B]
Get:21 http://archive.ubuntu.com saucy-security/universe Sources [8397 B]
Get:22 http://archive.ubuntu.com saucy-security/multiverse Sources [692 B]
Get:23 http://archive.ubuntu.com saucy-security/main amd64 Packages [106 kB]
Get:24 http://archive.ubuntu.com saucy-security/restricted amd64 Packages [14 B]
Get:25 http://archive.ubuntu.com saucy-security/universe amd64 Packages [36.3 kB]
Get:26 http://archive.ubuntu.com saucy-security/multiverse amd64 Packages [1160 B]
Hit http://archive.ubuntu.com saucy-security/main Translation-en
Hit http://archive.ubuntu.com saucy-security/multiverse Translation-en
Hit http://archive.ubuntu.com saucy-security/restricted Translation-en
Hit http://archive.ubuntu.com saucy-security/universe Translation-en
Fetched 845 kB in 3s (244 kB/s)
Reading package lists... Done
W: Duplicate sources.list entry http://dl.google.com/linux/chrome/deb/ stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems
user@chrubuntu:~$ sudo apt-get install wine1.7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 wine1.7 : Depends: wine1.7-i386 (= 1:1.7.15-0ubuntu1~saucy1) but it is not installable
           Recommends: gnome-exe-thumbnailer but it is not going to be installed or
                       kde-runtime but it is not going to be installed
           Recommends: fonts-droid but it is not going to be installed
           Recommends: ttf-mscorefonts-installer but it is not going to be installed
           Recommends: fonts-horai-umefont but it is not going to be installed
           Recommends: fonts-unfonts-core but it is not going to be installed
           Recommends: winbind but it is not going to be installed
           Recommends: winetricks but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
user@chrubuntu:~$ 

```

---

### Post by Kris_Spencer on 2014-03-28
I'm not 100% possitive, but I think you install an ARM architecture OS.  That means that x86 and x86_64 packages will not run on it. The reason  is that an ARM processor uses a different instruction set than a  "normal" processor. I'm sorry to say, but if this is true, wine and playonlinux aren't going to work for you. Nor is WoW, as WoW is written for x86.

---

### Post by oldrocker99 on 2014-03-28
before anything else, try this:

```
sudo apt-get -f install
``` 

The Acer C7 has an Intel Centrino 847 64-bit CPU, and I have used PlayonLinux successfully on mine (using Chrubuntu 12.04, which allows the installation of the **ia32-libs** package, which is not present in 13.10), using MATE as a desktop (it's pretty lightweight) and installed and played a number of games from GOG.com successfully. You can install an older version of PLayOnLinux from the repos, or get the latest build here:
[http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html)

Steam for Linux also works well on the Chrubuntuized Acer C7. I can play Half-Life 1+2, Portal, Papers, Please, and several other lightweight games. I have, on mine, gotten a bigger battery, 4GB more RAM, and a SSD (nice and zippy). It's still the best $$ I spent on a Linux laptop, and no Windows tax!

Although I pay for Crossover, I end up using PlayOnLinux almost exclusively, and it's one hell of a good program. Its scripts are specific to each game or program (something Crossover also does), and install the wine version that best runs each program (which Crossover doesn't do). I tried to install Skyrim on my desktop using Crossover, and failed. I tried it with PlayOnLinux, and it installed Steam for Windows, which, once logged in, allowed me to install Skyrim, and an hour later I was playing.

---

### Post by Kris_Spencer on 2014-03-28
Oh good! I wasn't sure about the architecture. I'm glad that it's an x86 model. PoL is a wonderful program. For the "Cannot find wine" problem, just install wine before PoL.

---

