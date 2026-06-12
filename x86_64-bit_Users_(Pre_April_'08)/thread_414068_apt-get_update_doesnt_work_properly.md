---
title: "apt-get update doesnt work properly"
date: 2007-04-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by 9a3eedi on 2007-04-19
I'm a normal ubuntu user, and like any other ubuntu user, I want to get Fiesty ASAP and am really excited for it.. :guitar: 

but sudo apt-get update doesnt work too well.. I get some wierd errors which I have no idea how to resolve.. and when I go on update manager and check for updates.. I also get wierd errors.. and the button which allows me to upgrade to fiesty as shown on [the official howto by ubuntu]("http://www.ubuntu.com/getubuntu/upgrading") doesn't appear

here's a sample from an apt-get update command I just issued right now

```

the9a3eedi@the9a3eedi-desktop:~$ sudo apt-get update
Password:
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release amd64 (20061025) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release amd64 (20061025) edgy/restricted Translation-en_US
Get:1 http://www.getautomatix.com edgy Release.gpg [189B]                      
Ign http://www.getautomatix.com edgy/main Translation-en_US                    
Ign http://www.albertomilone.com binary/ Release.gpg                           
Hit http://www.getautomatix.com edgy Release                                   
Err http://www.getautomatix.com edgy Release                                   
  
Ign http://www.albertomilone.com binary/ Translation-en_US                     
Ign http://www.albertomilone.com binary/ Release                               
Get:2 http://www.getautomatix.com edgy Release [6733B]                         
Hit http://www.albertomilone.com binary/ Packages                              
Ign http://www.getautomatix.com edgy Release                                   
Hit http://www.getautomatix.com edgy/main Packages                             
Get:3 http://security.ubuntu.com edgy-security Release.gpg [191B]              
Get:4 http://archive.ubuntu.com edgy Release.gpg [191B]                        
Get:5 http://ae.archive.ubuntu.com edgy Release.gpg [191B]                     
Get:6 http://ubuntu.beryl-project.org edgy Release.gpg [191B]                  
Ign http://ubuntu.beryl-project.org edgy/main Translation-en_US                
Hit http://ubuntu.beryl-project.org edgy Release                               
Ign http://security.ubuntu.com edgy-security/main Translation-en_US            
Ign http://archive.ubuntu.com edgy/universe Translation-en_US                  
Ign http://archive.ubuntu.com edgy/multiverse Translation-en_US                
Ign http://archive.ubuntu.com edgy/universe Translation-en_US                  
Ign http://archive.ubuntu.com edgy/multiverse Translation-en_US                
Ign http://archive.ubuntu.com edgy/universe Translation-en_US                  
Ign http://archive.ubuntu.com edgy/multiverse Translation-en_US                
Get:7 http://archive.ubuntu.com edgy-updates Release.gpg [191B]                
Ign http://archive.ubuntu.com edgy-updates/universe Translation-en_US          
Ign http://archive.ubuntu.com edgy-updates/multiverse Translation-en_US        
Get:8 http://archive.ubuntu.com edgy-security Release.gpg [191B]               
Ign http://archive.ubuntu.com edgy-security/main Translation-en_US             
Ign http://archive.ubuntu.com edgy-security/restricted Translation-en_US       
Ign http://archive.ubuntu.com edgy-security/universe Translation-en_US         
Hit http://ubuntu.beryl-project.org edgy/main Packages                         
Ign http://archive.ubuntu.com edgy-security/multiverse Translation-en_US
Hit http://archive.ubuntu.com edgy Release                                     
Hit http://archive.ubuntu.com edgy-updates Release                             
Hit http://archive.ubuntu.com edgy-security Release                            
Hit http://archive.ubuntu.com edgy/universe Packages                           
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US      
Ign http://ae.archive.ubuntu.com edgy/main Translation-en_US                   
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US
Hit http://security.ubuntu.com edgy-security Release                 
Err http://security.ubuntu.com edgy-security Release                 
  
Get:9 http://security.ubuntu.com edgy-security Release [50.9kB]                
Ign http://ae.archive.ubuntu.com edgy/restricted Translation-en_US             
Ign http://security.ubuntu.com edgy-security Release                           
Ign http://ae.archive.ubuntu.com edgy/universe Translation-en_US               
Get:10 http://ae.archive.ubuntu.com edgy-updates Release.gpg [191B]  
Ign http://ae.archive.ubuntu.com edgy-updates/main Translation-en_US          
Ign http://ae.archive.ubuntu.com edgy-updates/restricted Translation-en_US
Get:11 http://ae.archive.ubuntu.com edgy-backports Release.gpg [191B]
Ign http://ae.archive.ubuntu.com edgy-backports/main Translation-en_US         
Ign http://security.ubuntu.com edgy-security/main Packages           
Ign http://ae.archive.ubuntu.com edgy-backports/restricted Translation-en_US   
Ign http://ae.archive.ubuntu.com edgy-backports/universe Translation-en_US
Ign http://ae.archive.ubuntu.com edgy-backports/multiverse Translation-en_US
Hit http://ae.archive.ubuntu.com edgy Release  
Hit http://security.ubuntu.com edgy-security/restricted Packages               
Hit http://security.ubuntu.com edgy-security/main Sources                      
Hit http://security.ubuntu.com edgy-security/restricted Sources                
Hit http://security.ubuntu.com edgy-security/universe Packages                 
Hit http://security.ubuntu.com edgy-security/universe Sources                  
Get:12 http://ae.archive.ubuntu.com edgy-updates Release [38.4kB]              
Hit http://archive.ubuntu.com edgy/multiverse Packages                      
Err http://security.ubuntu.com edgy-security/main Packages                  
  503 Service Unavailable
Hit http://archive.ubuntu.com edgy/universe Packages                           
Hit http://archive.ubuntu.com edgy/multiverse Packages                         
Ign http://ae.archive.ubuntu.com edgy-updates Release 
Hit http://ae.archive.ubuntu.com edgy-backports Release                      
Hit http://ae.archive.ubuntu.com edgy/main Packages                            
Hit http://ae.archive.ubuntu.com edgy/restricted Packages                    
Hit http://ae.archive.ubuntu.com edgy/main Sources                           
Hit http://ae.archive.ubuntu.com edgy/restricted Sources                     
Hit http://archive.ubuntu.com edgy/universe Packages                         
Hit http://ae.archive.ubuntu.com edgy/universe Packages                   
Hit http://archive.ubuntu.com edgy/multiverse Packages                       
Hit http://archive.ubuntu.com edgy-updates/universe Packages              
Hit http://archive.ubuntu.com edgy-updates/multiverse Packages            
Hit http://ae.archive.ubuntu.com edgy/universe Sources                    
Hit http://archive.ubuntu.com edgy-security/main Packages                    
Hit http://ae.archive.ubuntu.com edgy-updates/main Packages               
Hit http://ae.archive.ubuntu.com edgy-updates/restricted Packages            
Hit http://ae.archive.ubuntu.com edgy-updates/main Sources                   
Hit http://ae.archive.ubuntu.com edgy-updates/restricted Sources
Hit http://archive.ubuntu.com edgy-security/restricted Packages
Hit http://archive.ubuntu.com edgy-security/universe Packages
Hit http://archive.ubuntu.com edgy-security/multiverse Packages
Hit http://ae.archive.ubuntu.com edgy-backports/main Packages
Hit http://ae.archive.ubuntu.com edgy-backports/restricted Packages
Hit http://ae.archive.ubuntu.com edgy-backports/universe Packages
Hit http://ae.archive.ubuntu.com edgy-backports/multiverse Packages
Hit http://ae.archive.ubuntu.com edgy-backports/main Sources
Hit http://ae.archive.ubuntu.com edgy-backports/restricted Sources
Hit http://ae.archive.ubuntu.com edgy-backports/universe Sources
Hit http://ae.archive.ubuntu.com edgy-backports/multiverse Sources
Fetched 58.2kB in 10m50s (89B/s)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-amd64/Packages.gz  503 Service Unavailable
Reading package lists... Done
W: GPG error: http://www.getautomatix.com edgy Release: The following signatures were invalid: BADSIG CC919A31E23C5FC3 Arnav Ghosh (Automatix Team Lead) <greyrod@gmail.com>
W: GPG error: http://security.ubuntu.com edgy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.



```

This may be relevant: sources.list

```


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release amd64 (20061025)]/ edgy main restricted

deb http://ae.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://ae.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ae.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://ae.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ae.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://ae.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ae.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://ae.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://www.albertomilone.com/drivers/edgy/latest/32bit binary/
deb http://ubuntu.beryl-project.org/ edgy main
deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse
deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse
deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt edgy main

deb http://archive.ubuntu.com/ubuntu edgy-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END



```

yes I did install automatix :P

---

### Post by eentonig on 2007-04-19
Be patient. I'm not ugrading today, because I know the servers will be killed with millions of people trying to upgrade at the same time.

Imagine you're giving a free drink for you entire village in your own home. And then, when already 16.000 people are drinking,  some morons start complaining they can't get into the house to claim their drink.

---

### Post by maestrobwh1 on 2007-04-19
Oh, that is why I can't install anything.  I have been using feisty for a while, but today, I got an error on nearly half of the sources.  No biggie... there is next week:-)

---

### Post by 9a3eedi on 2007-04-19
I see.. so the servers are overloaded, I assume, which is why I'm getting these errors? 

Well, I've been getting these errors before fiesty got  out, so..

I guess the better method at this time would be to download the alternate CD via bittorrent, and then upgrade to fiesty using that, huh?

I see that there are more seeds than peers.. strange.. I'd think that there's an overload of peers, since it's just released

all for the better :D

---

### Post by projektdotnet on 2007-04-19
that is why everything takes so long today huh? :lolflag: 

I guess I will wait until tomorrow to reinstall with 64bit

edit: I just couldn't wait, boy I'm an idiot *sigh* this reminds me of dialup days

---

