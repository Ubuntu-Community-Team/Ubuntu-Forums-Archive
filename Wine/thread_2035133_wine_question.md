---
title: "wine question"
date: 2012-07-29
forum: Wine
---

### Post by gandalf3 on 2012-07-29
i have a question about what a "wine prefix" is
i want to install a program in wine, but it needs directx. 
it automatically suggests installation on my C drive, but i want  to install on my ubuntu drive (wine sees it as "Z")
its supposed to work if i install directx in the same "wine prefix"
but is the C drive it suggests my real C drive? or a fake drive produced by wine?
(what i assumed a "wine prefix" to be.):confused:
thanks in advance

---

### Post by levlaz on 2012-07-29
I am not familiar with wine, but hopefully [this]("http://wiki.winehq.org/FAQ/#wineprefix") will point you in the right direction. 

Best, 

Lev

---

### Post by Kelvari on 2012-07-30
The Wine Prefix is simply the directory that all of your Wine information is in. Generally, that would be ~/.wine unless you've done a custom install, or have more than one Wine environment set up for some reason.

---

### Post by mastablasta on 2012-07-30
> **gandalf3 said:**
> but is the C drive it suggests my real C drive? or a fake drive produced by wine?

 
if you are installing it in linux using wine, then it's wine fake drive. the directory would be hidden in your home folder (as explaine in ~./wine).

---

### Post by Lyfang on 2012-07-30
Instead of MS Office (step 2) choose e.g. POL_Install_directx9 at: [http://www.playonlinux.com/repository/?cat=100&type=0](http://www.playonlinux.com/repository/?cat=100&type=0)
> **Lyfang said:**
> I like PlayOnLinux since that program uses installation scripts.
1. Install PlayOnLinux, choose e.g. Ubuntu [http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html)
2. Choose MS Office version: [http://www.playonlinux.com/repository/?cat=3&type=0](http://www.playonlinux.com/repository/?cat=3&type=0)
3. "Install this program"
I hope this will help.

---

### Post by Ubun2to on 2012-07-30
You need to use the C drive. The C drive emulates the actual Windows filesystem. The Z drive is /. If you mess around with /, you could do serious damage. If you are trying to install to / (Z) because of no space on C, you need to either move away from Wubi or resize your partitions if you don't use Wubi (if you can't resize your partition, as your drive is full, you need to get a new drive and clone the current one).

---

### Post by Toz on 2012-07-30
Moved to the Wine forum.

---

### Post by ergo-proxy on 2012-07-30
> **gandalf3 said:**
> i have a question about what a "wine prefix" is
i want to install a program in wine, but it needs directx. 
it automatically suggests installation on my C drive, but i want to install on my ubuntu drive (wine sees it as "Z")
its supposed to work if i install directx in the same "wine prefix"
but is the C drive it suggests my real C drive? or a fake drive produced by wine?
(what i assumed a "wine prefix" to be.):confused:
thanks in advance
 
Wineprefix is just a location where your individual configuration is stored (installation files, addonss, configuration files etc)
 
So if you want to create a dedicated configuration (always recommended) for example for Warcraft do this:
 
export WINEPREFIX=/home/user/.wineprefixes/.wine-warcraft/
winetricks d3dx9 (it will install directx9 in the location specified by the wineprefix)

---

### Post by gandalf3 on 2012-07-30
thanks, i think i get it now.. i try some stuff out and see what happens:)

> **Lyfang said:**
> Instead of MS Office (step 2) choose e.g. POL_Install_directx9 at: [http://www.playonlinux.com/repository/?cat=100&type=0](http://www.playonlinux.com/repository/?cat=100&type=0)

not entirely sure what you are talking about..:confused:
but i tried to install play on linux but it doesn't work..

thanks.

---

### Post by Ubun2to on 2012-07-30
> **gandalf3 said:**
> thanks, i think i get it now.. i try some stuff out and see what happens:)



not entirely sure what you are talking about..:confused:
but i tried to install play on linux but it doesn't work..

thanks.

You can use the Software Center version, but it is really outdated. The current version can be downloaded here:
[http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html)
Click on Ubuntu. Click the link that says "PlayOnLinux_4.1.3.deb".
That is the latest version. Once it is downloaded, open the file. It should automatically go to the Software Center. Install it.
Then, open POL, go to Install, select the Office category, and select the software you have.
If it doesn't work (it's hit or miss in my experience), you may have to go to a virtual machine. I hate having to boot up VirtualBox, but that's just what it comes down to sometimes, so you don't have to dual boot.

---

### Post by gandalf3 on 2012-08-01
> **ergo-proxy said:**
> Wineprefix is just a location where your individual configuration is stored (installation files, addonss, configuration files etc)
 
So if you want to create a dedicated configuration (always recommended) for example for Warcraft do this:
 
export WINEPREFIX=/home/user/.wineprefixes/.wine-warcraft/
winetricks d3dx9 (it will install directx9 in the location specified by the wineprefix)

.wineprefixes doesn't exist, should i just create it?
or is it supposed to be there by default and something is wrong?
:confused:

---

### Post by Lyfang on 2012-08-01
> **gandalf3 said:**
> not entirely sure what you are talking about..:confused:
but i tried to install play on linux but it doesn't work..

thanks.

Open Terminal:
```
sudo apt-get update && sudo apt-get install playonlinux
```
Open PlayOnLinux & try to find the program that you want to install & install it. PlayOnLinux should create a Wine "prefix" or "fake drive" automatically for you. I don't think you need to fully understand what the Wine "prefix" does, especially with PlayOnLinux(?). A little bit of clarification, I hope this will help.

---

### Post by gandalf3 on 2012-08-01
no, it installed, just the program won't start (sorry if i was unclear)
i haven't tried > ```
sudo apt-get update && sudo apt-get install playonlinux
```, but here's what happens when i run the playonlinux command: ```

playonlinux
Traceback (most recent call last):
  File "mainwindow.py", line 31, in <module>
    import wxversion
ImportError: No module named wxversion
/usr/share/playonlinux/playonlinux: line 89: python2.6: command not found

```

EDIT i installed from the .deb from they're website

---

### Post by Lyfang on 2012-08-01
> **gandalf3 said:**
> EDIT i installed from the .deb from they're website
Open Terminal & try: 
```
sudo apt-get remove playonlinux
sudo apt-get update && sudo apt-get install playonlinux
```

---

### Post by gandalf3 on 2012-08-01
nope.. :( ```
username@ubuntu01:~$ sudo apt-get remove playonlinux
[sudo] password for username: 
My mind is going. I can feel it.
[sudo] password for username: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  torcs-data simgear2.0.0 libaccess-bridge-java-jni torcs-data-tracks
  torcs-data-cars libaccess-bridge-java torcs
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  playonlinux
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 12.4 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 485377 files and directories currently installed.)
Removing playonlinux ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for gconf2 ...
Processing triggers for man-db ...
username@ubuntu01:~$ sudo apt-get update && sudo apt-get install playonlinux
Ign http://dl.google.com stable InRelease
Ign http://dl.google.com stable InRelease                                      
Ign http://dl.google.com stable InRelease                                      
Ign http://us.archive.ubuntu.com oneiric InRelease                             
Ign http://us.archive.ubuntu.com oneiric-updates InRelease                     
Ign http://us.archive.ubuntu.com oneiric-backports InRelease                   
Hit http://deb.playonlinux.com oneiric InRelease                               
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Ign http://archive.getdeb.net oneiric-getdeb InRelease                         
Ign http://ppa.launchpad.net oneiric InRelease                                 
Get:2 http://dl.google.com stable Release.gpg [198 B]                          
Ign http://archive.canonical.com oneiric InRelease                             
Ign http://archive.ubuntu.com oneiric InRelease                                
Ign http://security.ubuntu.com oneiric-security InRelease                      
Ign http://extras.ubuntu.com oneiric InRelease                                 
Get:3 http://dl.google.com stable Release.gpg [198 B]                          
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Get:4 http://us.archive.ubuntu.com oneiric Release.gpg [198 B]                 
Get:5 http://dl.google.com stable Release                                      
Ign http://ppa.launchpad.net oneiric InRelease                                 
Get:6 http://dl.google.com stable Release                                      
Hit http://archive.canonical.com oneiric Release.gpg                           
Get:7 http://archive.ubuntu.com oneiric Release.gpg [198 B]                    
Hit http://deb.playonlinux.com oneiric/main i386 Packages                      
Get:8 http://security.ubuntu.com oneiric-security Release.gpg [198 B]          
Get:9 http://us.archive.ubuntu.com oneiric-updates Release.gpg [198 B]         
Get:10 http://extras.ubuntu.com oneiric Release.gpg [72 B]                     
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Get:11 http://dl.google.com stable Release                                     
Get:12 http://dl.google.com stable/main i386 Packages [1,220 B]                
Get:13 http://us.archive.ubuntu.com oneiric-backports Release.gpg [198 B]      
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://archive.canonical.com oneiric Release                               
Get:14 http://archive.ubuntu.com oneiric Release [40.8 kB]                     
Hit http://archive.getdeb.net oneiric-getdeb Release.gpg                       
Get:15 http://security.ubuntu.com oneiric-security Release [40.8 kB]           
Hit http://extras.ubuntu.com oneiric Release                                   
Get:16 http://dl.google.com stable/main i386 Packages [464 B]                  
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Get:17 http://us.archive.ubuntu.com oneiric Release [40.8 kB]                  
Hit http://archive.canonical.com oneiric/partner Sources                       
Ign http://deb.playonlinux.com oneiric/main TranslationIndex                   
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Get:18 http://archive.ubuntu.com oneiric/main Sources [877 kB]                 
Get:19 http://us.archive.ubuntu.com oneiric-updates Release [40.8 kB]          
Hit http://archive.getdeb.net oneiric-getdeb Release                           
Hit http://ppa.launchpad.net oneiric Release                                   
Get:20 http://security.ubuntu.com oneiric-security/restricted Sources [1,959 B]
Get:21 http://us.archive.ubuntu.com oneiric-backports Release [40.8 kB]        
Get:22 http://dl.google.com stable/main i386 Packages [770 B]                  
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Get:23 http://security.ubuntu.com oneiric-security/main Sources [51.9 kB]      
Get:24 http://us.archive.ubuntu.com oneiric/restricted Sources [5,351 B]       
Get:25 http://us.archive.ubuntu.com oneiric/main Sources [877 kB]              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://archive.getdeb.net oneiric-getdeb/games i386 Packages               
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Get:26 http://security.ubuntu.com oneiric-security/multiverse Sources [1,641 B]
Get:27 http://security.ubuntu.com oneiric-security/universe Sources [18.9 kB]  
Get:28 http://security.ubuntu.com oneiric-security/main i386 Packages [190 kB] 
Ign http://archive.canonical.com oneiric/partner Translation-en_US             
Ign http://archive.getdeb.net oneiric-getdeb/games TranslationIndex            
Ign http://archive.canonical.com oneiric/partner Translation-en                
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://extras.ubuntu.com oneiric/main Translation-en_US                    
Ign http://deb.playonlinux.com oneiric/main Translation-en_US                  
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Get:29 http://security.ubuntu.com oneiric-security/restricted i386 Packages [3,939 B]
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Get:30 http://security.ubuntu.com oneiric-security/universe i386 Packages [50.7 kB]
Ign http://deb.playonlinux.com oneiric/main Translation-en                     
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Get:31 http://security.ubuntu.com oneiric-security/multiverse i386 Packages [3,380 B]
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex          
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex      
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Hit http://security.ubuntu.com oneiric-security/main Translation-en            
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en      
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en      
Hit http://security.ubuntu.com oneiric-security/universe Translation-en        
Get:32 http://us.archive.ubuntu.com oneiric/multiverse Sources [149 kB]        
Get:33 http://archive.ubuntu.com oneiric/restricted Sources [5,351 B]          
Ign http://archive.getdeb.net oneiric-getdeb/games Translation-en_US           
Get:34 http://us.archive.ubuntu.com oneiric/universe Sources [4,677 kB]        
Ign http://archive.getdeb.net oneiric-getdeb/games Translation-en              
Get:35 http://us.archive.ubuntu.com oneiric/main i386 Packages [1,226 kB]      
Get:36 http://us.archive.ubuntu.com oneiric/restricted i386 Packages [8,216 B] 
Get:37 http://us.archive.ubuntu.com oneiric/universe i386 Packages [4,468 kB]  
Get:38 http://us.archive.ubuntu.com oneiric/multiverse i386 Packages [119 kB]  
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex                 
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex             
Get:39 http://us.archive.ubuntu.com oneiric-updates/restricted Sources [3,347 B]
Get:40 http://us.archive.ubuntu.com oneiric-updates/main Sources [149 kB]      
Get:41 http://us.archive.ubuntu.com oneiric-updates/multiverse Sources [3,666 B]
Get:42 http://us.archive.ubuntu.com oneiric-updates/universe Sources [57.6 kB] 
Get:43 http://us.archive.ubuntu.com oneiric-updates/main i386 Packages [374 kB]
Get:44 http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages [6,631 B]
Get:45 http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages [124 kB]
Get:46 http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages [6,371 B]
Hit http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex   
Hit http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex     
Get:47 http://us.archive.ubuntu.com oneiric-backports/main Sources [2,742 B]   
Get:48 http://us.archive.ubuntu.com oneiric-backports/restricted Sources [14 B]
Get:49 http://us.archive.ubuntu.com oneiric-backports/universe Sources [9,019 B]
Get:50 http://us.archive.ubuntu.com oneiric-backports/multiverse Sources [14 B]
Get:51 http://us.archive.ubuntu.com oneiric-backports/main i386 Packages [3,296 B]
Get:52 http://us.archive.ubuntu.com oneiric-backports/restricted i386 Packages [14 B]
Get:53 http://us.archive.ubuntu.com oneiric-backports/universe i386 Packages [13.4 kB]
Get:54 http://us.archive.ubuntu.com oneiric-backports/multiverse i386 Packages [14 B]
Hit http://us.archive.ubuntu.com oneiric-backports/main TranslationIndex       
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com oneiric-backports/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com oneiric-backports/universe TranslationIndex   
Hit http://us.archive.ubuntu.com oneiric/main Translation-en                   
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en             
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en             
Hit http://us.archive.ubuntu.com oneiric/universe Translation-en               
Hit http://us.archive.ubuntu.com oneiric-updates/main Translation-en           
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com oneiric-updates/universe Translation-en       
Hit http://us.archive.ubuntu.com oneiric-backports/main Translation-en         
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com oneiric-backports/universe Translation-en     
Fetched 13.7 MB in 3min 3s (74.8 kB/s)                                         
Reading package lists... Done
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ oneiric/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  torcs-data simgear2.0.0 libaccess-bridge-java-jni torcs-data-tracks
  torcs-data-cars libaccess-bridge-java torcs
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  playonlinux
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/4,161 kB of archives.
After this operation, 12.4 MB of additional disk space will be used.
Selecting previously deselected package playonlinux.
(Reading database ... 484853 files and directories currently installed.)
Unpacking playonlinux (from .../playonlinux_4.1.3_all.deb) ...
Processing triggers for man-db ...
Processing triggers for gconf2 ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up playonlinux (4.1.3) ...
gconf-schemas is /usr/sbin/gconf-schemas
username@ubuntu01:~$ playonlinux
Traceback (most recent call last):
  File "mainwindow.py", line 31, in <module>
    import wxversion
ImportError: No module named wxversion
/usr/share/playonlinux/playonlinux: line 89: python2.6: command not found

```

---

### Post by ergo-proxy on 2012-08-02
> **gandalf3 said:**
> .wineprefixes doesn't exist, should i just create it?
or is it supposed to be there by default and something is wrong?
:confused:
 
You can create it and it can be any location you want (it doesnt exist be default).

---

### Post by Lyfang on 2012-08-02
> **gandalf3 said:**
>                   
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) oneiric InRelease                                                  
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) oneiric/main i386 Packages                                            
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) oneiric/main TranslationIndex                                       
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) oneiric/main Translation-en_US                  
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) oneiric/main Translation-en                    
Carefully remove the [http://deb.playonlinux.com](http://deb.playonlinux.com) from the repositories & try again.

---

### Post by gandalf3 on 2012-08-02
i couldn't find  [http://deb.playonlinux.com](http://deb.playonlinux.com) in /etc/apt/sources.list,
so unchecked it from the sources in the software center then did sudo apt-get playonlinux,
but i still got the same error... :(

---

### Post by Lyfang on 2012-08-03
> **gandalf3 said:**
> i couldn't find  [http://deb.playonlinux.com](http://deb.playonlinux.com) in /etc/apt/sources.list
Can you find /etc/apt/sources.list.d/playonlinux.list?

---

### Post by gandalf3 on 2012-08-03
yes, there's a playonlinux.list, and a playonlinux.list.save there's no difference that i can see, other than the "  [http://deb.playonlinux.com](http://deb.playonlinux.com)" in playonlinux.list is commented out.

EDIT

> You can create it and it can be any location you want (it doesnt exist be default).

i created the directory and everything, installed directx, but it still says directx is missing..
i tried using the normal installer from Microsoft, but that didn't work either. :(

---

### Post by Lyfang on 2012-08-03
Open Terminal & try: 
```
sudo apt-get remove playonlinux
```
Download [playonlinux_4.0.14-1_all.deb]("http://mirror.pnl.gov/ubuntu//pool/multiverse/p/playonlinux/playonlinux_4.0.14-1_all.deb") 
If you are curious I found the package [here]("http://packages.ubuntu.com/en/precise/playonlinux") (or rather [http://packages.ubuntu.com/en/precise/all/playonlinux/download](http://packages.ubuntu.com/en/precise/all/playonlinux/download)).

---

### Post by gandalf3 on 2012-08-04
> **gandalf3 said:**
> no, it installed, just the program won't start (sorry if i was unclear)
i haven't tried , but here's what happens when i run the playonlinux command: ```

playonlinux
Traceback (most recent call last):
  File "mainwindow.py", line 31, in <module>
    import wxversion
ImportError: No module named wxversion
/usr/share/playonlinux/playonlinux: line 89: python2.6: command not found

```EDIT i installed from the .deb from they're website
the old error is "wxversion missing"

> **Lyfang said:**
> Open Terminal & try: 
```
sudo apt-get remove playonlinux
```Download [playonlinux_4.0.14-1_all.deb]("http://mirror.pnl.gov/ubuntu//pool/multiverse/p/playonlinux/playonlinux_4.0.14-1_all.deb") 
If you are curious I found the package [here]("http://packages.ubuntu.com/en/precise/playonlinux") (or rather [http://packages.ubuntu.com/en/precise/all/playonlinux/download](http://packages.ubuntu.com/en/precise/all/playonlinux/download)).

i installed and with Ubuntu software center, then ran in the terminal.
```
playonlinux
Traceback (most recent call last):
  File "mainwindow.py", line 30, in <module>
    import wx
ImportError: No module named wx
/usr/share/playonlinux/playonlinux: line 96: python2.6: command not found

```
now it's just "wx missing"
also interesting that it says python 2.6
 (i thought i installed 3.x or something)
do you know why that is?:confused:

---

### Post by Lyfang on 2012-08-04
> **gandalf3 said:**
> now it's just "wx missing" I think that you should run:
```
sudo apt-get remove playonlinux
```
Click & install [http://mirror.pnl.gov/ubuntu//pool/multiverse/p/playonlinux/playonlinux_4.0.14-1_all.deb](http://mirror.pnl.gov/ubuntu//pool/multiverse/p/playonlinux/playonlinux_4.0.14-1_all.deb). Otherwise you seem to be installing another version than found in the official Ubuntu repository(?).

---

### Post by gandalf3 on 2012-08-04
> I think that you should run:
 	Code:
 	sudo apt-get remove playonlinux 
Click & install [http://mirror.pnl.gov/ubuntu//pool/m...0.14-1_all.deb]("http://mirror.pnl.gov/ubuntu//pool/multiverse/p/playonlinux/playonlinux_4.0.14-1_all.deb"). Otherwise you seem to be installing another version than found in the official Ubuntu repository(?).oh sorry..
yes i did..
umm sorry, wasn't very clear.. :/
i ran sudo apt-get remove playonlinux, THEN downloaded the link you gave me, opened it (by default with ubuntu software center) clicked install, ran "playonlinux" in the terminal, and got this error >  	Code:
 	playonlinux Traceback (most recent call last):   File "mainwindow.py", line 30, in <module>     import wx ImportError: No module named wx /usr/share/playonlinux/playonlinux: line 96: python2.6: command not found 
now it's just "wx missing"

---

### Post by Lyfang on 2012-08-05
I think PlayOnLinux is written in Python. Maybe reinstalling Python would help?

---

### Post by gandalf3 on 2012-08-06
> **Lyfang said:**
> I think PlayOnLinux is written in Python. Maybe reinstalling Python would help?

haven't tried yet, but after looking at *this* thread, i think that might work..

> **gandalf3 said:**
> 
i created the directory and everything, installed directx, but it still says directx is missing..
i tried using the normal installer from Microsoft, but that didn't work either. :(
i found out that wine is installing directx in the right place, but not the program.. how do i get the program to install in the new wineprefix? d3dx9 did..:confused:

---

### Post by Lyfang on 2012-08-09
> **gandalf3 said:**
> how do i get the program to install in the new wineprefix? d3dx9 did..:confused:
I found [Q4Wine]("http://sourceforge.net/projects/q4wine/") but I haven't tried the program. "It will help you manage wine prefixes and installed applications."

---

### Post by gandalf3 on 2012-08-12
installed 12.04, now playonlinux installed successfully!
still downloading Microsoft fonts.. I'll update after i try some stuff out.
Thanks! :)

---

### Post by gandalf3 on 2012-08-13
works perfectly, but doesn't have the program i was originally trying to install.. 
unrelated, i install 7zip with it to extract a .DMG file, but should i navigate to the file somehow through the "c: drive" and if so, how? or is it safe to find it through the "z:\" option?
thanks..

---

### Post by Ubun2to on 2012-08-14
> **gandalf3 said:**
> works perfectly, but doesn't have the program i was originally trying to install.. 
unrelated, i install 7zip with it to extract a .DMG file, but should i navigate to the file somehow through the "c: drive" and if so, how? or is it safe to find it through the "z:\" option?
thanks..

Unless you configured Wine otherwise, Z:\ is your / (root) directory. C:\ has all the standard program file structures (it is basically a copy of the Windows filesystem, with all the files they can legally supply to help Windows programs run).

---

### Post by gandalf3 on 2012-08-14
so it's safe to find the file through the z:\ in 7zip's file browser?
(i heard you could do damage by using the z drive in wine)

---

### Post by Ubun2to on 2012-08-16
> **gandalf3 said:**
> so it's safe to find the file through the z:\ in 7zip's file browser?
(i heard you could do damage by using the z drive in wine)

Z:\ is your root directory ( / ). Go into the file browser, and click on File System. That is the root directory, also known as Z:\. If you install here or modify anything here, you can do some serious damage.

---

### Post by gandalf3 on 2012-08-16
yes, that's what i heard. but if i open 7z running in wine, can i safely navigate to ~/Downloads/File.dmg in 7z's file browser and extract "file.dmg"? does that count as "modifying"? if it does, then what do i do?

---

### Post by Ubun2to on 2012-08-17
> **gandalf3 said:**
> yes, that's what i heard. but if i open 7z running in wine, can i safely navigate to ~/Downloads/File.dmg in 7z's file browser and extract "file.dmg"? does that count as "modifying"? if it does, then what do i do?

Oh. I see what you want to do. There is actually a 7Zip app in the software center. Try using that first-native apps run much better than under Wine.

---

### Post by gandalf3 on 2012-08-17
yes, i believe that is only for extracting 7zip files.
i want to extract a .DMG file.
if that native 7z does do that, please tell me how it works, because i have not been able to figure it out..:confused:

---

### Post by Ubun2to on 2012-08-17
> **gandalf3 said:**
> yes, i believe that is only for extracting 7zip files.
i want to extract a .DMG file.
if that native 7z does do that, please tell me how it works, because i have not been able to figure it out..:confused:

I have never worked with .DMG files, but it does say on the 7Zip page in the Software Center that it supports unpacking .DMG files.

---

### Post by gandalf3 on 2012-08-20
oh thanks, i figured it out.. kind of. it's terminal based, but i don't  know how to use it in the terminal. (when i went to the directory of the  .DMG, and did "7z e: file.DMG"
but got "error, invalid terminal" what do i do?

---

### Post by Ubun2to on 2012-08-21
> **gandalf3 said:**
> oh thanks, i figured it out.. kind of. it's terminal based, but i don't  know how to use it in the terminal. (when i went to the directory of the  .DMG, and did "7z e: file.DMG"
but got "error, invalid terminal" what do i do?

If I'm correct, I remember seeing in the comments that 7Zip integrates with the Archive Manger. You should see if that is true. I don't know if it is true, as the built in Archive Manager has met all of my needs.

---

### Post by thatguruguy on 2012-08-21
gandalf3, would it be possible for you to tell us exactly what it is you are trying to accomplish?

As far as opening .dmg files, I think the tool you want may be dmg2img, which is available in the Ubuntu Software Center or through Synaptic (or by typing "sudo apt-get install dmg2img" in a terminal).

---

### Post by gandalf3 on 2012-08-21
> **Ubun2to said:**
> If I'm correct, I remember seeing in the comments that 7Zip integrates with the Archive Manger. You should see if that is true. I don't know if it is true, as the built in Archive Manager has met all of my needs.

 > p7zip is the Unix command-line port of 7-Zip, a file archiver that archives with high compression ratios.

p7zip-full provides utilities to pack and unpack 7z archives within a shell or using a GUI (such as Ark, File Roller or Nautilus).

Installing p7zip-full allows File Roller to use the very efficient 7z compression format for packing and unpacking files and directories. Additionally, it provides the 7z and 7za commands.

List of supported formats:

Packing / unpacking: 7z, ZIP, GZIP, BZIP2, XZ and TAR

Unpacking only: APM, ARJ, CAB, CHM, CPIO, CramFS, DEB, DMG, FAT, HFS, ISO, LZH, LZMA, LZMA2, MBR, MSI, MSLZ, NSIS, NTFS, RAR (only if non-free p7zip-rar package is installed), RPM, SquashFS, UDF, VHD, WIM, XAR and Z.

p7zip provides 7zr, a light version of 7za, and p7zip, a gzip-like wrapper around 7zr. it only works with 7z files through the file-roller/nautilus.
i know i 7z (through wine) works, i used it before i upgraded to 12.04 to extract other DMG files, (navigating through the graphical file browser through the z: drive) worked fine. according to the software center (quoted above) the native version works too, but it is terminal based, and when i tried the only obvious (to me) command, ```
cd ~/Downloads
7z e: filename.DMG
```
i got something like "error wrong command line" does anyone know if either navigating to the DMG file (in Z:) through (wine) 7z graphical file browser is safe, or the command to extract using the terminal native 7z.
i would rather use 7z because it comes out all ready to use, where it seems i still have to mount or do something to  the stuff that comes out of dmg2img. (and since i know 7z works)
Thanks.

---

### Post by thatguruguy on 2012-08-21
> **gandalf3 said:**
> it only works with 7z files through the file-roller/nautilus.
i know i 7z (through wine) works, i used it before i upgraded to 12.04 to extract other DMG files, (navigating through the graphical file browser through the z: drive) worked fine. according to the software center (quoted above) the native version works too, but it is terminal based, and when i tried the only obvious (to me) command, ```
cd ~/Downloads
7z e: filename.DMG
```i got something like "error wrong command line" does anyone know if either navigating to the DMG file (in Z:) through (wine) 7z graphical file browser is safe, or the command to extract using the terminal native 7z.
i would rather use 7z because it comes out all ready to use, where it seems i still have to mount or do something to  the stuff that comes out of dmg2img. (and since i know 7z works)
Thanks.

The man entry for 7z is confusing. The correct way to do use it is as follows:
```
7z e filename.DMG
```
... without the colon after the e.

---

### Post by gandalf3 on 2012-08-22
Thanks.
it worked, kinda.. it extracted several (as far as i can tell) useless files that i can't open.
they are:
0 - DDM
1.Apple_partition_map
2.hfs
3.free
:confused;

---

### Post by thatguruguy on 2012-08-22
> **gandalf3 said:**
> Thanks.
it worked, kinda.. it extracted several (as far as i can tell) useless files that i can't open.
they are:
0 - DDM
1.Apple_partition_map
2.hfs
3.free
:confused;

Perhaps it's time to address the 800 pound gorilla in the room. .DMG files are for Apple computers, typically. What is it, exactly, that you are trying to do? It may be useful to let us know exactly what file you are trying to open, and what you're trying to do with it.

---

### Post by Ubun2to on 2012-08-22
> **thatguruguy said:**
> Perhaps it's time to address the 800 pound gorilla in the room. .DMG files are for Apple computers, typically. What is it, exactly, that you are trying to do? It may be useful to let us know exactly what file you are trying to open, and what you're trying to do with it.

That was what I was wondering-why work with Apple's proprietary formats to begin with?

---

### Post by gandalf3 on 2012-08-22
there's a chat theme for empathy that i had on 11.10, and i don't like any of the default themes... it seems that almost all the various themes that i like that i can read are in annoying apple disk image format..
:(

---

