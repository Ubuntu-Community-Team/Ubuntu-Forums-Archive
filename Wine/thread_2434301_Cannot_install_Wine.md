---
title: "Cannot install Wine"
date: 2020-01-03
forum: Wine
---

### Post by alvinrr on 2020-01-03
I cannot install Wine in my Ubuntu 18.04, I followed the instructions here [https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu), but when I was about to install the packages, this happens.

```
alvin@alvin:~$ sudo apt install --install-recommends winehq-stable
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
winehq-stable : Depends: wine-stable (= 4.0.3~bionic)
E: Unable to correct problems, you have held broken packages.
```

---

### Post by slickymaster on 2020-01-03
*Thread moved to **Wine**.*

---

### Post by alvinrr on 2020-01-04
Can someone help me with this...please...

---

### Post by cmcanulty on 2020-01-04
Wine is always confusing to install and the ubuntu software store and synaptic make it more confusing because there are different files. Try this  real clear (I hope!) explanation and let me know if it works. It  just requires copying and pasting commands into the terminal. Before you start purge any wine files you have so you have no old wine files messing things up. To purge whatever wine you have in your system wine  first run


```

sudo apt-get remove wine
rm -rf $HOME/.wine
rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm

```

After deleting the files run command:

```

sudo apt-get remove –purge wine

```

Then run the following commands to correct any installation error.

```

sudo apt-get update
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove

```

after all that you should not have any residual wine files and so run which adds support for 32 bit wine apps:

```

sudo dpkg --add-architecture i386 

```

Next add WineHQ signing key and repository:

```

wget -qO- https://dl.winehq.org/wine-builds/winehq.key | sudo apt-key add -
sudo apt-add-repository 'deb http://dl.winehq.org/wine-builds/ubuntu/ bionic main'

```

Finally run

```

sudo apt-get install --install-recommends winehq-stable

```

 to check version after Wine installation:

$ wine --version
wine-3.0.3

 Here is a web explanation in case you need more info

[https://tecadmin.net/install-wine-on-ubuntu/]("https://tecadmin.net/install-wine-on-ubuntu/")

---

### Post by alvinrr on 2020-01-04
Thank you for your answer. But I have this in the first code.

```
alvin@alvin:~$ sudo apt-get remove wine
[sudo] password for alvin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'wine' can't be removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by cmcanulty on 2020-01-04
I didn't realize you had it installed in a virtual box. If so then go into the virtual box and do the commands from within it. If not please explain how you ave it installed.

---

### Post by alvinrr on 2020-01-04
I don't even know what virtual box is. by the way, I think I have it installed following your guide. But I cannot find the Wine program in my Applications.
```
alvin@alvin:~$ sudo apt-get remove wine
[sudo] password for alvin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'wine' can't be removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
alvin@alvin:~$ rm -rf $HOME/.wine
alvin@alvin:~$ rm -f $HOME/.config/menus/applications-merged/wine*
alvin@alvin:~$ rm -rf $HOME/.local/share/applications/wine
alvin@alvin:~$ rm -f $HOME/.local/share/desktop-directories/wine*
alvin@alvin:~$ rm -f $HOME/.local/share/icons/????_*.xpm
alvin@alvin:~$ sudo apt-get remove –purge wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'wine' can't be removed
E: Unable to locate package –purge
alvin@alvin:~$ sudo apt-get update
Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://dl.google.com/linux/chrome/deb stable Release                     
Hit:3 https://ocean.surfshark.com/debian stretch InRelease                     
Hit:4 https://dl.winehq.org/wine-builds/ubuntu bionic InRelease                
Hit:6 http://ph.archive.ubuntu.com/ubuntu bionic InRelease                     
Hit:7 https://packages.microsoft.com/repos/ms-teams stable InRelease           
Get:8 http://ph.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]   
Hit:9 http://archive.canonical.com/ubuntu bionic InRelease                     
Hit:10 http://ppa.launchpad.net/deluge-team/ppa/ubuntu bionic InRelease        
Get:11 http://ph.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]
Get:12 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]   
Hit:13 http://ppa.launchpad.net/kdenlive/kdenlive-stable/ubuntu bionic InRelease
Get:14 http://ph.archive.ubuntu.com/ubuntu bionic-proposed InRelease [242 kB]  
Hit:15 http://ppa.launchpad.net/oguzhaninan/stacer/ubuntu bionic InRelease     
Hit:16 http://ppa.launchpad.net/snwh/pulp/ubuntu bionic InRelease              
Fetched 494 kB in 4s (127 kB/s)
Reading package lists... Done
alvin@alvin:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alvin@alvin:~$ sudo apt-get clean
alvin@alvin:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
alvin@alvin:~$ sudo dpkg --add-architecture i386
alvin@alvin:~$ wget -qO- https://dl.winehq.org/wine-builds/winehq.key | sudo apt-key add -
OK
alvin@alvin:~$ sudo apt-add-repository 'deb http://dl.winehq.org/wine-builds/ubuntu/ bionic main'
Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://ph.archive.ubuntu.com/ubuntu bionic InRelease                     
Hit:3 http://dl.google.com/linux/chrome/deb stable Release                     
Hit:4 https://packages.microsoft.com/repos/ms-teams stable InRelease           
Get:5 http://ph.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]   
Hit:6 https://ocean.surfshark.com/debian stretch InRelease                     
Hit:7 https://dl.winehq.org/wine-builds/ubuntu bionic InRelease                
Hit:8 http://archive.canonical.com/ubuntu bionic InRelease                     
Hit:10 http://ppa.launchpad.net/deluge-team/ppa/ubuntu bionic InRelease        
Get:11 http://ph.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]
Hit:12 http://ppa.launchpad.net/kdenlive/kdenlive-stable/ubuntu bionic InRelease
Get:13 http://ph.archive.ubuntu.com/ubuntu bionic-proposed InRelease [242 kB]  
Hit:14 http://ppa.launchpad.net/oguzhaninan/stacer/ubuntu bionic InRelease     
Hit:15 http://ppa.launchpad.net/snwh/pulp/ubuntu bionic InRelease              
Get:16 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]                                    
Fetched 494 kB in 32s (15.5 kB/s)    
Reading package lists... Done
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list:56
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list:56
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list:56
W: Target Translations (main/i18n/Translation-en_PH) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list:56
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list:56
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list:56
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list:56
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list:56
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list:56
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list:56
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list:56
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list:56
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list:56
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list:56
W: Target Translations (main/i18n/Translation-en_PH) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list:56
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list:56
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list:56
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list:56
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list:56
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list:56
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list:56
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list:56
alvin@alvin:~$ sudo apt-get install --install-recommends winehq-stable
Reading package lists... Done
Building dependency tree       
Reading state information... Done
winehq-stable is already the newest version (4.0.3~bionic).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
alvin@alvin:~$ wine --version
wine-4.0.3

```

---

### Post by Dennis N on 2020-01-04
> I think I have it installed following your guide. But I cannot find the Wine program in my Applications.
Wine would show as a Category, not a program. You may need to install at least one Windows program before anything will show up in the Menu. Just like in Windows, you need a program's Windows installer to get a Windows program working. Wine should first run the installer. You can do it by right click on the installer and choose "Run with" and choose "Wine".

Try that and see what happens. There are some improved ways to work with Windows programs, like PlayOnLinux which actually has a GUI you can run.

---

### Post by richardlc on 2020-01-12
Thank you very much!  I also had a message as below on a virtual version!  It appears that it is installed, so will test it out.

---

### Post by mastablasta on 2020-01-15
if you want a graphical interface for setting up wine, then there are: Playonlinux, Proton (requires Steam) and Lutris (pulls in some new stuff, i am a bit sceptical on system stability with this, btu some people says it works well for them).

there is also Crossover, but that one is payable. 

plain old wine will work just fine thought but be prepared to communicate with it through command line. there is winetricks that will help you a bit with setup.

---

