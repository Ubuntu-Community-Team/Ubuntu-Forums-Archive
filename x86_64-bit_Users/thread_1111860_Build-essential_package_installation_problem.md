---
title: "Build-essential package installation problem"
date: 2009-03-31
forum: x86 64-bit Users
---

### Post by somepalli on 2009-03-31
[COLOR="DarkGreen"]I tried to install build essential package through Synaptic Manager On that time i got following message.
[/COLOR]
[COLOR="Red"]build-essential:
 Depends: libc6-dev but it is not going to be installed or
	libc-dev
 Depends: g++ but it is not going to be installed
[/COLOR]

---

### Post by jespdj on 2009-03-31
Which version of Ubuntu are you using?

Does it also say something about broken packages? If it does, then try to [fix this](https://help.ubuntu.com/community/SynapticHowto#How to fix broken packages) and try again.

---

### Post by somepalli on 2009-03-31
My Ubuntu version is 8.04.

I am not able to fix Broken packages its not enable the Apply Marked Changes.

---

### Post by oldos2er on 2009-03-31
Can you please post the output of
```
sudo apt-get update && sudo apt-get install -f
```
?

---

### Post by somepalli on 2009-04-01
Thank u for reply... But I got same problem....
Please tell me what kind of problem this is.... 
I did the following steps


[COLOR="DarkGreen"]somepalli@ubuntu:~$ sudo apt-get update
[sudo] password for somepalli: 

Get:1 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy Release.gpg [189B]                    
Ign [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy/main Translation-en_IN                  
Ign [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy/restricted Translation-en_IN            
Ign [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy/universe Translation-en_IN              
Ign [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy/multiverse Translation-en_IN            
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports Release.gpg [189B]          
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/main Translation-en_IN        
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/restricted Translation-en_IN  
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/universe Translation-en_IN    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_IN  
Get:3 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-updates Release.gpg [189B]            
Ign [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-updates/main Translation-en_IN          
Ign [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-updates/restricted Translation-en_IN    
Ign [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-updates/universe Translation-en_IN      
Ign [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-updates/multiverse Translation-en_IN    
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports Release [44.0kB]            
Get:5 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/main Packages [32.6kB]      
Get:6 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-security Release.gpg [189B]           
Ign [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-security/main Translation-en_IN         
Ign [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-security/restricted Translation-en_IN   
Ign [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-security/universe Translation-en_IN     
Ign [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-security/multiverse Translation-en_IN   
Get:7 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-backports Release.gpg [189B]          
Ign [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-backports/restricted Translation-en_IN  
Ign [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-backports/main Translation-en_IN        
Get:8 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/restricted Packages [14B]   
Ign [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-backports/multiverse Translation-en_IN  
Ign [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-backports/universe Translation-en_IN    
Get:9 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/universe Packages [102kB]   
Get:10 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-proposed Release.gpg [189B]          
Ign [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-proposed/restricted Translation-en_IN   
Ign [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-proposed/main Translation-en_IN         
Ign [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-proposed/multiverse Translation-en_IN   
Ign [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-proposed/universe Translation-en_IN     
Get:11 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/multiverse Packages [17.0kB]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/main Sources                  
Get:12 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/restricted Sources [14B]   
Get:13 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy Release [65.9kB]                     
Get:14 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-updates Release [58.5kB]             
Hit [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-security Release                        
Get:15 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/universe Sources [24.9kB]  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/multiverse Sources            
Get:16 [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg [189B]                   
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_IN               
Get:17 [http://archive.canonical.com](http://archive.canonical.com) hardy Release [6998B]                      
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_IN           
Get:19 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-backports Release [51.2kB]           
Hit [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-proposed Release                        
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5kB]              
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [139kB]         
Get:22 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy/main Packages [1173kB]               
Hit [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy/restricted Packages                     
Hit [http://directhex.mfgames.com](http://directhex.mfgames.com) hardy Release.gpg                   
Ign [http://directhex.mfgames.com](http://directhex.mfgames.com) hardy/main Translation-en_IN                  
Get:23 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy/main Sources [338kB]                 
Hit [http://directhex.mfgames.com](http://directhex.mfgames.com) hardy Release                                 
Get:24 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy/restricted Sources [1488B]           
Ign [http://directhex.mfgames.com](http://directhex.mfgames.com) hardy/main Packages                           
Get:25 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy/universe Packages [4254kB]           
Get:26 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy/universe Sources [1323kB]            
Get:27 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy/multiverse Packages [174kB]          
Get:28 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy/multiverse Sources [60.9kB]          
Get:29 [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages [1455B]             
Get:30 [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources [1603B]              
Get:31 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-updates/main Packages [419kB]        
Hit [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-updates/restricted Packages             
Get:32 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-updates/main Sources [111kB]         
Get:33 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-updates/restricted Sources [903B]    
Hit [http://directhex.mfgames.com](http://directhex.mfgames.com) hardy/main Packages                           
Get:34 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-updates/universe Packages [172kB]    
Get:35 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-updates/universe Sources [39.1kB]    
Get:36 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-updates/multiverse Packages [27.5kB] 
Get:37 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-updates/multiverse Sources [5212B]   
Get:38 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-security/main Packages [139kB]       
Get:39 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-security/restricted Packages [7048B] 
Get:40 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-security/main Sources [25.8kB]       
Get:41 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-security/restricted Sources [892B]   
Get:42 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-security/universe Packages [71.2kB]  
Get:43 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-security/universe Sources [10.7kB]   
Get:44 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-security/multiverse Packages [11.2kB]
Get:45 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-security/multiverse Sources [1105B]  
Get:46 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-backports/restricted Packages [14B]  
Get:47 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-backports/main Packages [112kB]      
Get:48 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-backports/multiverse Packages [13.9kB]
Get:49 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-backports/universe Packages [109kB]  
Get:50 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-proposed/restricted Packages [7422B] 
Get:51 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-proposed/main Packages [56.9kB]      
Get:52 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-proposed/multiverse Packages [5479B] 
Get:53 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) hardy-proposed/universe Packages [18.0kB]  
Fetched 9294kB in 19s (485kB/s)                                                
Reading package lists... Done

somepalli@ubuntu:~$ sudo apt-get install -f

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsm-dev libice-dev automake1.9 libxrandr-dev libxdamage-dev libusplash-dev
  libpthread-stubs0 libxfixes-dev x11proto-xinerama-dev x11proto-render-dev
  libxi-dev autoconf libpixman-1-dev libtiffxx0c2 x11proto-kb-dev
  x11proto-randr-dev libxinerama-dev skype-common xtrans-dev intltool
  libatk1.0-dev x11proto-input-dev libxcb-xlib0-dev x11proto-fixes-dev
  x11proto-xext-dev libxext-dev x11proto-damage-dev libxau-dev libbogl0
  libxcomposite-dev libxrender-dev libx11-dev x11proto-composite-dev
  autotools-dev libxcb1-dev x11proto-core-dev libxdmcp-dev
  libpthread-stubs0-dev libxcursor-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.[/COLOR]

[COLOR="Red"]somepalli@ubuntu:~$ sudo apt-get install build-essential 
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
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages
somepalli@ubuntu:~$ 
[/COLOR]

---

### Post by loomsen on 2009-04-01
Disable all other repos except the official hardy repos. 
All gutsy, game, foobar repos.

Run the update again, and install the apropriate pkg. Looks like you installed from another source causing the conflict.

---

### Post by somepalli on 2009-04-06
thank you for help but i am getting following message!!!

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
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages

---

