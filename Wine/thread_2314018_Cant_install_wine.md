---
title: "Cant install wine"
date: 2016-02-17
forum: Wine
---

### Post by serpentiazeus on 2016-02-17
tried to install wine using the terminal and here is the process i did

```
sudo dpkg --add-architecture i386 
```

then

```
sudo add-apt-repository ppa:wine/wine-builds
```

```
gpg: keyring `/tmp/tmpko0hng5v/secring.gpg' created
gpg: keyring `/tmp/tmpko0hng5v/pubring.gpg' created
gpg: requesting key 77C899CB from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpko0hng5v/trustdb.gpg: trustdb created
gpg: key 77C899CB: public key "Launchpad PPA for Wine" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK


```

then

```
sudo apt-get update
```


```
Ign http://ppa.launchpad.net trusty InRelease
Hit http://repository.spotify.com stable InRelease                             
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://ppa.launchpad.net trusty InRelease                                  
Get:1 http://security.ubuntu.com trusty-security InRelease [65.9 kB]           
Hit http://ppa.launchpad.net trusty Release.gpg                                
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://repository.spotify.com stable/non-free amd64 Packages               
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://repository.spotify.com stable/non-free i386 Packages                
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://extras.ubuntu.com trusty Release                                    
Get:2 http://security.ubuntu.com trusty-security/main Sources [105 kB]         
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:3 http://security.ubuntu.com trusty-security/restricted Sources [4035 B]   
Ign http://pt.archive.ubuntu.com trusty InRelease                              
Hit http://pt.archive.ubuntu.com trusty-updates InRelease                      
Hit http://pt.archive.ubuntu.com trusty-backports InRelease                    
Get:4 http://security.ubuntu.com trusty-security/universe Sources [33.0 kB]    
Hit http://pt.archive.ubuntu.com trusty Release.gpg                            
Hit http://pt.archive.ubuntu.com trusty-updates/main Sources                   
Hit http://pt.archive.ubuntu.com trusty-updates/restricted Sources             
Hit http://pt.archive.ubuntu.com trusty-updates/universe Sources               
Hit http://pt.archive.ubuntu.com trusty-updates/multiverse Sources             
Hit http://pt.archive.ubuntu.com trusty-updates/main amd64 Packages            
Hit http://pt.archive.ubuntu.com trusty-updates/restricted amd64 Packages      
Get:5 http://security.ubuntu.com trusty-security/multiverse Sources [2767 B]   
Hit http://pt.archive.ubuntu.com trusty-updates/universe amd64 Packages        
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://pt.archive.ubuntu.com trusty-updates/multiverse amd64 Packages      
Hit http://pt.archive.ubuntu.com trusty-updates/main i386 Packages             
Hit http://pt.archive.ubuntu.com trusty-updates/restricted i386 Packages       
Hit http://pt.archive.ubuntu.com trusty-updates/universe i386 Packages         
Hit http://pt.archive.ubuntu.com trusty-updates/multiverse i386 Packages       
Ign http://repository.spotify.com stable/non-free Translation-en               
Hit http://pt.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://pt.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Get:6 http://security.ubuntu.com trusty-security/main amd64 Packages [421 kB]  
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Ign http://repository.spotify.com stable/non-free Translation-pt               
Hit http://pt.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://pt.archive.ubuntu.com trusty-updates/universe Translation-en        
Ign http://repository.spotify.com stable/non-free Translation-pt_BR            
Hit http://pt.archive.ubuntu.com trusty Release                                
Hit http://pt.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://pt.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://pt.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://pt.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://pt.archive.ubuntu.com trusty-backports/main amd64 Packages          
Hit http://pt.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Hit http://pt.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Hit http://pt.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://pt.archive.ubuntu.com trusty-backports/main i386 Packages           
Ign http://ppa.launchpad.net trusty/main Translation-pt                        
Hit http://pt.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://pt.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://pt.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://pt.archive.ubuntu.com trusty-backports/main Translation-en          
Ign http://ppa.launchpad.net trusty/main Translation-pt_BR                     
Hit http://pt.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Get:7 http://security.ubuntu.com trusty-security/restricted amd64 Packages [13.0 kB]
Hit http://pt.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://pt.archive.ubuntu.com trusty-backports/universe Translation-en      
Get:8 http://security.ubuntu.com trusty-security/universe amd64 Packages [124 kB]
Hit http://pt.archive.ubuntu.com trusty/main Sources                           
Get:9 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [4990 B]
Hit http://pt.archive.ubuntu.com trusty/restricted Sources                     
Hit http://pt.archive.ubuntu.com trusty/universe Sources                       
Hit http://pt.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://pt.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://pt.archive.ubuntu.com trusty/restricted amd64 Packages 
Get:10 http://security.ubuntu.com trusty-security/main i386 Packages [393 kB]  
Hit http://pt.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://pt.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://pt.archive.ubuntu.com trusty/main i386 Packages                 
Hit http://pt.archive.ubuntu.com trusty/restricted i386 Packages           
Hit http://pt.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://pt.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://pt.archive.ubuntu.com trusty/main Translation-en                    
Hit http://pt.archive.ubuntu.com trusty/main Translation-pt                    
Hit http://pt.archive.ubuntu.com trusty/main Translation-pt_BR                 
Hit http://pt.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://pt.archive.ubuntu.com trusty/multiverse Translation-pt              
Get:11 http://security.ubuntu.com trusty-security/restricted i386 Packages [12.7 kB]
Hit http://pt.archive.ubuntu.com trusty/multiverse Translation-pt_BR           
Hit http://pt.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://pt.archive.ubuntu.com trusty/restricted Translation-pt              
Hit http://pt.archive.ubuntu.com trusty/restricted Translation-pt_BR           
Hit http://pt.archive.ubuntu.com trusty/universe Translation-en                
Hit http://pt.archive.ubuntu.com trusty/universe Translation-pt                
Hit http://pt.archive.ubuntu.com trusty/universe Translation-pt_BR             
Get:12 http://security.ubuntu.com trusty-security/universe i386 Packages [124 kB]
Get:13 http://security.ubuntu.com trusty-security/multiverse i386 Packages [5164 B]
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Ign http://extras.ubuntu.com trusty/main Translation-en
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Ign http://extras.ubuntu.com trusty/main Translation-pt
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Ign http://extras.ubuntu.com trusty/main Translation-pt_BR
Fetched 1307 kB in 9s (133 kB/s)                                               
Reading package lists... Done
```

```
sudo apt-get install --install-recommends winehq-devel
```

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 winehq-devel : Depends: wine-devel
E: Unable to correct problems, you have held broken packages.
```

dont know what to do

---

### Post by serpentiazeus on 2016-02-18
Anyone?

---

