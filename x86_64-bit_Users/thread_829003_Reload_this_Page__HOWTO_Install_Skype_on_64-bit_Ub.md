---
title: "Reload this Page  HOWTO: Install Skype on 64-bit Ubuntu .PROPER"
date: 2008-06-14
forum: x86 64-bit Users
---

### Post by mark.kristos on 2008-06-14
> **mhenriday said:**
> I should mention that for 64-bit users who, for whatever reason, do not find it appropriate to force the architecture of i386 deb packages, can install what seems to be a 64-bit version of **Skype** (??) direct from Synaptic, if they add the [_Medibuntu repositories_]("https://help.ubuntu.com/community/Medibuntu") to their 3rd party list. Alas, doing so didn't help me with my audio problems in **Skype**, but those with a less refractory audio card than **Creative**'s **Soundblaster X-Fi** might like to give it a whirl....

Henri

Installed great following instruction on the link given. Heres what a successful install should look like:

mark@ubuntu-laptop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
[sudo] password for mark: 
--07:10:36--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.10
Connecting to [www.medibuntu.org|87.98.242.10|:80](www.medibuntu.org|87.98.242.10|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 226 [text/plain]

100%[====================================>] 226           --.--K/s             

07:10:52 (37.63 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [226/226]

mark@ubuntu-laptop:~$ sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
Get:1 [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Get:3 [http://archive.canonical.com](http://archive.canonical.com) hardy Release [6998B]                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5kB]               
Get:5 [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages [14B]                
Get:6 [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources [666B]                
Get:7 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [189B]                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US        
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages [6022B]
Get:9 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release [5590B]                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                                
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg [191B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US    
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [22.9kB]        
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages [3457B]   
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages [13.0kB]    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                              
Get:14 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages [5721B]               
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release [58.5kB]             
Get:16 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages [7726B]           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources                      
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages [209kB]        
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages [6022B]  
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources [70.1kB]        
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources [906B]    
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages [40.4kB]   
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources [7036B]     
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages [7696B]  
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources [1433B]   
Fetched 532kB in 12s (42.7kB/s)                                                
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  medibuntu-keyring
0 upgraded, 1 newly installed, 0 to remove and 9 not upgraded.
Need to get 3448B of archives.
After this operation, 49.2kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  medibuntu-keyring
Install these packages without verification [y/N]? y
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free medibuntu-keyring 2008.04.20 [3448B]
Fetched 3448B in 1s (3432B/s)                            
Selecting previously deselected package medibuntu-keyring.
(Reading database ... 126914 files and directories currently installed.)
Unpacking medibuntu-keyring (from .../medibuntu-keyring_2008.04.20_all.deb) ...
Setting up medibuntu-keyring (2008.04.20) ...
OK

Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                  
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [189B]    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US             
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release [5590B]                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages                      
Fetched 190B in 6s (28B/s)                                                     
Reading package lists... Done
mark@ubuntu-laptop:~$ sudo synaptic

Then, open synaptic and search for skype, mark skype package for install. Click apply. Boom, boom, bang it even installs the launcher icon in the applications menu.

I made a test call successfully.

Now we are jammin!  :guitar:

---

### Post by biocyberman on 2008-06-16
Worked like a charm for my Optiplex GX620 with Hardy Heron! Thanks :)

---

