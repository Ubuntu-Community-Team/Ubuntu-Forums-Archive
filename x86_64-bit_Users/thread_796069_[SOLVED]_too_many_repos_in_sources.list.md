---
title: "[SOLVED] too many repos in sources.list"
date: 2008-05-16
forum: x86 64-bit Users
---

### Post by tooferson5 on 2008-05-16
Fairly new Ubuntu Hardy user.  Have been reading howto's but I am a little confused about this. This is my sources.list.  I've read to get more updates you should add more repositiories.  I found a site where a guy posted alot of repos for hardy.  This is what I have right now but I feel that it is overkill.

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates restricted main
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse


## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

deb http://archive.ubuntu.com/ubuntu hardy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu hardy universe multiverse
  
  
deb-src http://archive.ubuntu.com/ubuntu hardy-security universe multiverse
deb-src http://archive.ubuntu.com/ubuntu hardy-updates universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe
deb http://lprod.org/deb/hardy/ ./
deb-src http://lprod.org/deb/hardy/ ./
deb http://ppa.launchpad.net/do-core/ubuntu hardy main
deb http://ppa.launchpad.net/gilir/ubuntu hardy main universe
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main
deb http://ppa.launchpad.net/mvo/ubuntu hardy main
deb http://us.archive.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe

deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main

deb http://ppa.launchpad.net/cornelius-maihoefer/ubuntu hardy main
```

and this is my output in terminal when i sudo apt-get update

```
USER@USER-laptop:~$ sudo apt-get update
Hit http://archive.canonical.com hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Hit http://archive.ubuntu.com hardy Release.gpg                                
Ign http://archive.ubuntu.com hardy/universe Translation-en_US                 
Hit http://security.ubuntu.com hardy-security Release.gpg                      
Ign http://security.ubuntu.com hardy-security/main Translation-en_US           
Hit http://us.archive.ubuntu.com hardy Release.gpg                             
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US                  
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_US               
Ign http://archive.ubuntu.com hardy/restricted Translation-en_US               
Ign http://archive.ubuntu.com hardy/main Translation-en_US                     
Hit http://archive.ubuntu.com hardy-security Release.gpg                       
Ign http://archive.ubuntu.com hardy-security/restricted Translation-en_US      
Ign http://archive.ubuntu.com hardy-security/main Translation-en_US            
Ign http://archive.ubuntu.com hardy-security/multiverse Translation-en_US      
Hit http://archive.canonical.com hardy Release                                 
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US              
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US            
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US       
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US     
Hit http://security.ubuntu.com hardy-security Release                          
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Ign http://ppa.launchpad.net hardy/universe Translation-en_US                  
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg                     
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US      
Ign http://archive.ubuntu.com hardy-security/universe Translation-en_US        
Hit http://archive.ubuntu.com hardy-updates Release.gpg                        
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_US       
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_US             
Hit http://us.archive.ubuntu.com hardy-security Release.gpg                    
Ign http://us.archive.ubuntu.com hardy-security/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com hardy-security/main Translation-en_US         
Hit http://archive.canonical.com hardy/partner Packages                        
Hit http://security.ubuntu.com hardy-security/main Packages                    
Hit http://packages.medibuntu.org hardy Release.gpg                            
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Ign http://lprod.org ./ Release.gpg                                            
Ign http://lprod.org ./ Translation-en_US                                      
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en_US       
Ign http://us.archive.ubuntu.com hardy-security/multiverse Translation-en_US   
Ign http://us.archive.ubuntu.com hardy-security/universe Translation-en_US     
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_US         
Hit http://archive.ubuntu.com hardy Release                                    
Hit http://archive.ubuntu.com hardy-security Release                           
Get:1 http://ppa.launchpad.net hardy Release [27.6kB]                          
Hit http://archive.canonical.com hardy/partner Sources                         
Hit http://security.ubuntu.com hardy-security/restricted Packages              
Hit http://security.ubuntu.com hardy-security/main Sources                     
Hit http://security.ubuntu.com hardy-security/restricted Sources               
Get:2 http://ppa.launchpad.net hardy Release [27.6kB]                          
Get:3 http://ppa.launchpad.net hardy Release [27.6kB]                          
Ign http://packages.medibuntu.org hardy/free Translation-en_US                 
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US             
Hit http://us.archive.ubuntu.com hardy Release                                 
Hit http://archive.ubuntu.com hardy-updates Release                            
Hit http://us.archive.ubuntu.com hardy-updates Release                         
Hit http://us.archive.ubuntu.com hardy-security Release                        
Ign http://lprod.org ./ Release                                                
Get:4 http://ppa.launchpad.net hardy Release [27.6kB]                          
Get:5 http://ppa.launchpad.net hardy Release [27.6kB]                          
Get:6 http://ppa.launchpad.net hardy Release [27.6kB]                          
Hit http://security.ubuntu.com hardy-security/universe Packages                
Hit http://security.ubuntu.com hardy-security/universe Sources                 
Hit http://security.ubuntu.com hardy-security/multiverse Packages              
Hit http://security.ubuntu.com hardy-security/multiverse Sources               
Hit http://packages.medibuntu.org hardy Release                                
Hit http://archive.ubuntu.com hardy/universe Packages                          
Hit http://archive.ubuntu.com hardy/multiverse Packages                        
Hit http://archive.ubuntu.com hardy/universe Sources                           
Hit http://archive.ubuntu.com hardy/multiverse Sources                         
Hit http://us.archive.ubuntu.com hardy/main Packages                           
Hit http://us.archive.ubuntu.com hardy/restricted Packages                     
Hit http://us.archive.ubuntu.com hardy/main Sources                            
Hit http://us.archive.ubuntu.com hardy/restricted Sources                      
Ign http://ppa.launchpad.net hardy/main Packages                               
Ign http://ppa.launchpad.net hardy/main Packages                               
Ign http://ppa.launchpad.net hardy/universe Packages                           
Hit http://lprod.org ./ Packages                                               
Hit http://archive.ubuntu.com hardy/restricted Packages                        
Hit http://archive.ubuntu.com hardy/main Packages                              
Hit http://archive.ubuntu.com hardy-security/universe Sources                  
Hit http://archive.ubuntu.com hardy-security/multiverse Sources                
Hit http://archive.ubuntu.com hardy-security/restricted Packages               
Hit http://archive.ubuntu.com hardy-security/main Packages                     
Hit http://archive.ubuntu.com hardy-security/multiverse Packages               
Hit http://us.archive.ubuntu.com hardy/universe Packages                       
Hit http://us.archive.ubuntu.com hardy/universe Sources                        
Hit http://us.archive.ubuntu.com hardy/multiverse Packages                     
Hit http://us.archive.ubuntu.com hardy/multiverse Sources                      
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages             
Hit http://us.archive.ubuntu.com hardy-updates/main Packages                   
Ign http://ppa.launchpad.net hardy/main Packages                               
Ign http://ppa.launchpad.net hardy/main Packages                               
Ign http://ppa.launchpad.net hardy/main Packages                               
Ign http://ppa.launchpad.net hardy/main Sources                                
Hit http://lprod.org ./ Sources                                                
Hit http://archive.ubuntu.com hardy-security/universe Packages                 
Hit http://archive.ubuntu.com hardy-updates/universe Sources                   
Hit http://archive.ubuntu.com hardy-updates/multiverse Sources                 
Hit http://archive.ubuntu.com hardy-updates/restricted Packages                
Hit http://us.archive.ubuntu.com hardy-updates/main Sources                    
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources              
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages               
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources                
Hit http://us.archive.ubuntu.com hardy-security/restricted Packages            
Ign http://ppa.launchpad.net hardy/main Packages                               
Hit http://ppa.launchpad.net hardy/main Packages                               
Hit http://ppa.launchpad.net hardy/main Packages                               
Hit http://archive.ubuntu.com hardy-updates/main Packages                      
Hit http://archive.ubuntu.com hardy-updates/multiverse Packages                
Hit http://archive.ubuntu.com hardy-updates/universe Packages                  
Hit http://us.archive.ubuntu.com hardy-security/main Packages                  
Hit http://us.archive.ubuntu.com hardy-security/multiverse Packages  
Hit http://us.archive.ubuntu.com hardy-security/universe Packages    
Hit http://ppa.launchpad.net hardy/universe Packages                 
Hit http://ppa.launchpad.net hardy/main Packages
Hit http://ppa.launchpad.net hardy/main Packages
Hit http://ppa.launchpad.net hardy/main Packages
Hit http://ppa.launchpad.net hardy/main Sources
Hit http://ppa.launchpad.net hardy/main Packages
Hit http://packages.medibuntu.org hardy/free Packages
Hit http://packages.medibuntu.org hardy/non-free Packages
Hit http://packages.mnksedibuntu.org hardy/free Sources
Hit http://packages.medibuntu.org hardy/non-free Sources
Fetched 6B in 1s (4B/s)  
Reading package lists... Done
USER@USER-laptop:~$ 
```

i am really hoping if anyone can look this over and tell me if i have repo listed that i dont need or if i am missing repos that i should have.  maybe i should go back to the default sources.list but being the noob i am i did not make a backup so maybe someone can post one for me.  thanks in advance.

---

### Post by EXCiD3 on 2008-05-16
Yes this is probably overkill. As a general rule you should only add repositories that you are actually using software from. For example if you wanted to use the latest wine, then it would follow suite that you would add the wine repository. The regular sources.list + repositores you use software from is how you should have it. There isnt really a need to have extra repositories in your sources.list unless you use software from it.

Here is the default sources.list for you:

```

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Alpha i386 (20080222)]/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://us.archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe #Added by software-properties
deb http://us.archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-security multiverse
```

---

### Post by tooferson5 on 2008-05-16
Thanks for the quick reply and the source.list but I am on a AMD64 system.  I need those repos.

---

### Post by EXCiD3 on 2008-05-16
They are the same. The repositories hold the packages for each version of ubuntu whether it is i686, x64 or a ppc install. It just knows where to look when you install them. The i386 mentioned in the file just means the name of the Ubuntu disc that was burned off as it was not the 64 bit version. That sources.list should work just fine.

---

### Post by Yellow Pasque on 2008-05-16
It doesn't look like a problem with sources.list; it just looks like you have incorrect URL's for those repos or that they're down at the moment you try to update.

> I need those repos.
I doubt it.. Do you even know what half of them are? This is a good way to break your install. You just copied them from a list...
> I've read to get more updates you should add more repositiories. I found a site where a guy posted alot of repos for hardy.

---

### Post by EXCiD3 on 2008-05-16
> **Temüjin said:**
> It doesn't look like a problem with sources.list; it just looks like you have incorrect URL's for those repos or that they're down at the moment you try to update.

Incorrect, none of the text outputted by his apt-get update command failed downloading the package list. Everything downloaded successfully. Your extra repositories are fine, you just dont need them.

---

### Post by Yellow Pasque on 2008-05-16
Ah, good call. (Ign = Ignored). He looks to have a lot of duplicates though (if not the actual URL, then overlapping/backup repos), which will cause some extra wait time when retrieving updates. I still believe that it's best to stick with the Ubuntu repo when possible and build from source otherwise.

---

### Post by EXCiD3 on 2008-05-16
> **Temüjin said:**
> I still believe that it's best to stick with the Ubuntu repo when possible and build from source otherwise.

Agreed, either build from source or only add the repositories if you dont want to have to build from source and use precompiled binaries, but check the ubuntu repositories first before adding extra ones, sometimes there is already a current build in there. ;) Don't add it unless you absolutely need it!

---

### Post by tooferson5 on 2008-05-16
Thanks again.  I really appreciated it.  I was searching for the default repo list all over the net and couldnt find it.  Now there is one posted for everyone, and an answer for anyone else who makes my noob mistake and adds too many repos to their sources.list.

---

