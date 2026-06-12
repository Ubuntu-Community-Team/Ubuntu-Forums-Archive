---
title: "Installing Wine"
date: 2012-12-03
forum: Wine
---

### Post by Inf3rn0666 on 2012-12-03
Been trying to install wine for the last few hours. Followed many tutorials and now all I get is this:

```
inf3rn0@ubuntu:~$ sudo add-apt-repository ppa:ubuntu-wine/ppa
You are about to add the following PPA to your system:
 Welcome to the Wine Team PPA.  Here you can get the latest available Wine betas for every supported version of Ubuntu.  This PPA is managed by Scott Ritchie and Maarten Lankhorst.
 More info: [https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpwwh7ym/secring.gpg' created
gpg: keyring `/tmp/tmpwwh7ym/pubring.gpg' created
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpwwh7ym/trustdb.gpg: trustdb created
gpg: key F9CB8DB0: public key "Launchpad PPA for Ubuntu Wine Team" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
inf3rn0@ubuntu:~$ sudo apt-get update
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal InRelease                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security InRelease            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                       
Hit [http://dl.google.com](http://dl.google.com) stable Release                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates InRelease                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                     
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release.gpg                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates Release.gpg                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main amd64 Packages  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted amd64 Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe amd64 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main amd64 Packages                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted amd64 Packages      
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe amd64 Packages        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Translation-en_US
Reading package lists... Done
inf3rn0@ubuntu:~$ sudo apt-get install wine
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

```




Any idea with what I can do??

---

### Post by Elfy on 2012-12-03
*Thread moved to **Wine**.*

---

### Post by offgridguy on 2012-12-03
I tried myself to install wine, no success.  I now have ubuntu CE, it comes with
wine installed, wine tools and wine tricks.

---

### Post by Tweak42 on 2012-12-04
> **Inf3rn0666 said:**
> Been trying to install wine for the last few hours. Followed many tutorials and now all I get is this:

```
inf3rn0@ubuntu:~$ sudo add-apt-repository ppa:ubuntu-wine/ppa
You are about to add the following PPA to your system:
 Welcome to the Wine Team PPA.  Here you can get the latest available Wine betas for every supported version of Ubuntu.  This PPA is managed by Scott Ritchie and Maarten Lankhorst.
 More info: [https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpwwh7ym/secring.gpg' created
gpg: keyring `/tmp/tmpwwh7ym/pubring.gpg' created
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpwwh7ym/trustdb.gpg: trustdb created
gpg: key F9CB8DB0: public key "Launchpad PPA for Ubuntu Wine Team" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
inf3rn0@ubuntu:~$ sudo apt-get update
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal InRelease                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security InRelease            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                       
Hit [http://dl.google.com](http://dl.google.com) stable Release                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates InRelease                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                     
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release.gpg                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates Release.gpg                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main amd64 Packages  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted amd64 Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe amd64 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main amd64 Packages                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted amd64 Packages      
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe amd64 Packages        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Translation-en_US
Reading package lists... Done
inf3rn0@ubuntu:~$ sudo apt-get install wine
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

```




Any idea with what I can do??

This doesn't appear to be a wine problem per se, but a broken packages issue.  I recommend seaching either the ubuntu forums or google for fix or repairing broken packages.  Have you had issues installing any other programs?

It hasn't happened much for me but I've used synaptic (if you have it installed) to usually straighten out issues like this but it can be done at the command line.

---

