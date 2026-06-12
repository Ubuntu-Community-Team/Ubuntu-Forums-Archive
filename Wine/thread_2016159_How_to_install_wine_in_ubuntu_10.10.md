---
title: "How to install wine in ubuntu 10.10 ?"
date: 2012-07-04
forum: Wine
---

### Post by honey_bee on 2012-07-04
hi,
      I am using Ubuntu 10.10 on my desktop pc. I want to install office 2007 on my ubuntu box. Just right now i have downloaded "wine -1.3.13.tar.bz2 " (It is compatible with ubuntu 10.10) on my pc. I does not know how to install it . Please guide me how can I installed it.

Note:Ubuntu 12.04 does not install on my system due to old hardware that is why i am using ubuntu 10.10 and it is working fine.

thanks
honey.

---

### Post by raja.genupula on 2012-07-04
```
tar -xvf /pathto/wine -1.3.13.tar.bz2
```

then **cd to wine** directory .

now do these steps one by one

```
./configure
make
sudo make install 
```

but any way its a large process , why dont you use apt-get to get the wine . But on 10 April 2012 Ubuntu dropped 10.10 , i suggest you to get upgrade .

---

### Post by honey_bee on 2012-07-04
thanks for the reply. Well it the command ./configure works fine the the command make not work .

please see the screenshort (attachment) for guidance .

thanks
honey

---

### Post by sanderj on 2012-07-04
> **honey_bee said:**
> hi,
      I am using Ubuntu 10.10 on my desktop pc. I want to install office 2007 on my ubuntu box. Just right now i have downloaded "wine -1.3.13.tar.bz2 " (It is compatible with ubuntu 10.10) on my pc. I does not know how to install it . Please guide me how can I installed it.

Note:Ubuntu 12.04 does not install on my system due to old hardware that is why i am using ubuntu 10.10 and it is working fine.

thanks
honey.

"sudo apt-get install wine" should do.

HTH

---

### Post by msammels on 2012-07-04
I second sanderj, installing it from the repos should suffice.

---

### Post by honey_bee on 2012-07-05
still no success. First guide me for ubuntu 10.10 which version of wine is compatible so I may download it .
thanks

---

### Post by raja.genupula on 2012-07-05
> **honey_bee said:**
> still no success. First guide me for ubuntu 10.10 which version of wine is compatible so I may download it .
thanks

tell me one thing , you have internet connection ? 

if yes 

then do this 
```
sudo apt-get install wine
``` in your terminal and it will install wine for you .

doing source compilation is a large process and this type of installaion wont get any type of updates from Ubuntu also .

---

### Post by Elfy on 2012-07-05
*Thread moved to **Wine**.*

---

### Post by honey_bee on 2012-07-05
please see the attachment .I am upset it is not working.

---

### Post by Elfy on 2012-07-05
try

```
sudo apt-get install wine1.3
```

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)


Run 

```
apt-cache search wine 
```

in a terminal to tell you what wine packages you have available.

---

### Post by raja.genupula on 2012-07-05
Ok , in your terminal type as 

```
sudo apt-get update 
sudo apt-get install wine
```

post the output of it .

---

### Post by sanderj on 2012-07-05
> **honey_bee said:**
> please see the attachment .I am upset it is not working.

Ah. "wine" is in the repository "universe". Probably universe is not yet added.

Easy solution:
Start the Software Center, and type "wine". Then install.

---

### Post by prshah on 2012-07-05
> **honey_bee said:**
> I am using Ubuntu 10.10 on my desktop pc. 

Note:Ubuntu 12.04 does not install on my system due to old hardware that is why i am using ubuntu 10.10 and it is working fine.

10.10 has reached EOL (End of Life) and repositories are closed. You will not have access to repositories, and so any amount of apt-get will not help.

If you find that 12.04 is not installing because it requires a PAE capable processor (Pentium M from ThinkPad T41 pre-2005 does not have PAE capability), then please install Lubuntu (or Xubuntu?) 12.04 first. You can then install the unity desktop (sudo apt-get install ubuntu-desktop) and use it in classic mode if you prefer the original gnome (gnome 2) interface.

If you want to remain with 10.10, you can install the WINE PPA ( see [http://www.ubuntuupdates.org/ppa/wine?dist=maverick](http://www.ubuntuupdates.org/ppa/wine?dist=maverick) ) but I don't know how you will apt-update, since the closed repositories will throw errors. 

Building from the source tar is also pointless, since you need to install build-essential, which is in the closed repos.

If you insist on moving backwards, then please use 10.04.4, it will be supported for about 3 more years.

Summary: Upgrade to 12.04 (via Lubuntu, if required), then install WINE from the repos.

12.04 uses lightdm in place of gdm, so performance should be adequate, especially with the "classic (no effects)" interface.

Please post back if you need more information.

---

### Post by honey_bee on 2012-07-05
see the output when i use this command

sudo apt-get update
 
```
  p { margin-bottom: 0.08in; }a:link {  }  : xxxxxxxx 
  
 W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2)  Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
  
 W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
  
 W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2)  Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
  
 W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
  
 W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2)  Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
  
 W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
  
 W: Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/maverick/Release.gpg)  Could not connect to ppa.launchpad.net:80 (91.189.90.217). - connect (110: Connection timed out) 
  
 W: Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Unable to connect to ppa.launchpad.net:http: 
  
 W: Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Unable to connect to ppa.launchpad.net:http: 
  
 W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  Unable to connect to extras.ubuntu.com:http: 
  
 W: Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  Unable to connect to ppa.launchpad.net:http: 
  
 W: Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  Unable to connect to ppa.launchpad.net:http: 
  
 W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  Unable to connect to extras.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz)  Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
  
 W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz)  Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
  
 W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz)  Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
  
 W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz)  Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
  
 W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz)  Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
  
 W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz)  Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
  
 W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz)  Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
  
 W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz)  Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
  
 E: Some index files failed to download, they have been ignored, or old ones xyzed instead. 
 tic@tic-ThinkPad-T41:~$ sudo apt-get update 
 [sudo] password for tic:  
 Err [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick Release.gpg                                             
   Could not connect to ppa.launchpad.net:80 (91.189.90.217). - connect (110: Connection timed out) 
 Err [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) maverick/main Translation-en             
   Unable to connect to ppa.launchpad.net:http: 
 Err [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) maverick/main Translation-en_US          
   Unable to connect to ppa.launchpad.net:http: 
 Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick Release                                                 
 Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main Sources                                            
 Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main i386 Packages                                      
 Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main Sources                                            
 Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main i386 Packages                                      
 Err [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main Sources                                            
   Unable to connect to ppa.launchpad.net:http: 
 Err [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main i386 Packages                                      
   Unable to connect to ppa.launchpad.net:http: 
 Err [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick Release.gpg                                         
   Could not connect to xyz.archive.ubuntu.com:80 (58.65.218.244). - connect (110: Connection timed out) 
 Err [http://xyz.archive.ubuntu.com/ubuntu/](http://xyz.archive.ubuntu.com/ubuntu/) maverick/main Translation-en                         
   Unable to connect to xyz.archive.ubuntu.com:http: 
 Err [http://xyz.archive.ubuntu.com/ubuntu/](http://xyz.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US                      
   Unable to connect to xyz.archive.ubuntu.com:http: 
 Err [http://xyz.archive.ubuntu.com/ubuntu/](http://xyz.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en                   
   Unable to connect to xyz.archive.ubuntu.com:http: 
 Err [http://xyz.archive.ubuntu.com/ubuntu/](http://xyz.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US                
   Unable to connect to xyz.archive.ubuntu.com:http: 
 Err [http://xyz.archive.ubuntu.com/ubuntu/](http://xyz.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en                   
   Unable to connect to xyz.archive.ubuntu.com:http: 
 Err [http://xyz.archive.ubuntu.com/ubuntu/](http://xyz.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US                
   Unable to connect to xyz.archive.ubuntu.com:http: 
 Err [http://xyz.archive.ubuntu.com/ubuntu/](http://xyz.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en                     
   Unable to connect to xyz.archive.ubuntu.com:http: 
 Err [http://xyz.archive.ubuntu.com/ubuntu/](http://xyz.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US                  
   Unable to connect to xyz.archive.ubuntu.com:http: 
 Err [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick-updates Release.gpg                                 
   Unable to connect to xyz.archive.ubuntu.com:http: 
 Err [http://xyz.archive.ubuntu.com/ubuntu/](http://xyz.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en                 
   Unable to connect to xyz.archive.ubuntu.com:http: 
 Err [http://xyz.archive.ubuntu.com/ubuntu/](http://xyz.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US              
   Unable to connect to xyz.archive.ubuntu.com:http: 
 Err [http://xyz.archive.ubuntu.com/ubuntu/](http://xyz.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en           
   Unable to connect to xyz.archive.ubuntu.com:http: 
 Err [http://xyz.archive.ubuntu.com/ubuntu/](http://xyz.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US        
   Unable to connect to xyz.archive.ubuntu.com:http: 
 Err [http://xyz.archive.ubuntu.com/ubuntu/](http://xyz.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en           
   Unable to connect to xyz.archive.ubuntu.com:http: 
 Err [http://xyz.archive.ubuntu.com/ubuntu/](http://xyz.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US        
   Unable to connect to xyz.archive.ubuntu.com:http: 
 Err [http://xyz.archive.ubuntu.com/ubuntu/](http://xyz.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en             
   Unable to connect to xyz.archive.ubuntu.com:http: 
 Err [http://xyz.archive.ubuntu.com/ubuntu/](http://xyz.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US          
   Unable to connect to xyz.archive.ubuntu.com:http: 
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick Release                                             
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick-updates Release                                     
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick/main Sources                                        
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick/restricted Sources                                  
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick/universe Sources                                    
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick/multiverse Sources                                  
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick/main i386 Packages                                  
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick/restricted i386 Packages                            
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick/universe i386 Packages                              
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick/multiverse i386 Packages                            
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick-updates/main Sources                                
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick-updates/restricted Sources                          
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick-updates/universe Sources                            
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick-updates/multiverse Sources                          
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick-updates/main i386 Packages                          
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick-updates/restricted i386 Packages                    
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick-updates/universe i386 Packages                      
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick-updates/multiverse i386 Packages                    
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick/main Sources                                        
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick/restricted Sources                                  
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick/universe Sources                                    
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick/multiverse Sources                                  
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick/main i386 Packages                                  
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick/restricted i386 Packages                            
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick/universe i386 Packages                              
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick/multiverse i386 Packages                            
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick-updates/main Sources                                
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick-updates/restricted Sources                          
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick-updates/universe Sources                            
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick-updates/multiverse Sources                          
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick-updates/main i386 Packages                          
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick-updates/restricted i386 Packages                    
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick-updates/universe i386 Packages                      
 Ign [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick-updates/multiverse i386 Packages                    
 Err [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick/main Sources                                        
   Unable to connect to xyz.archive.ubuntu.com:http: 
 Err [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick/restricted Sources                                  
   Unable to connect to xyz.archive.ubuntu.com:http: 
 Err [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick/universe Sources                                    
   Unable to connect to xyz.archive.ubuntu.com:http: 
 Err [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick/multiverse Sources                                  
   Unable to connect to xyz.archive.ubuntu.com:http: 
 Err [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick/main i386 Packages                                  
   Unable to connect to xyz.archive.ubuntu.com:http: 
 Err [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick/restricted i386 Packages                            
   Unable to connect to xyz.archive.ubuntu.com:http: 
 Err [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick/universe i386 Packages                              
   Unable to connect to xyz.archive.ubuntu.com:http: 
 Err [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick/multiverse i386 Packages                            
   Unable to connect to xyz.archive.ubuntu.com:http: 
 Err [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick-updates/main Sources                                
   Unable to connect to xyz.archive.ubuntu.com:http: 
 Err [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick-updates/restricted Sources                          
   Unable to connect to xyz.archive.ubuntu.com:http: 
 Err [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick-updates/universe Sources                            
   Unable to connect to xyz.archive.ubuntu.com:http: 
 Err [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick-updates/multiverse Sources                          
   Unable to connect to xyz.archive.ubuntu.com:http: 
 Err [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick-updates/main i386 Packages                          
   Unable to connect to xyz.archive.ubuntu.com:http: 
 Err [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick-updates/restricted i386 Packages                    
   Unable to connect to xyz.archive.ubuntu.com:http: 
 Err [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick-updates/universe i386 Packages                      
   Unable to connect to xyz.archive.ubuntu.com:http: 
 Err [http://xyz.archive.ubuntu.com]("http://xyz.archive.ubuntu.com/") maverick-updates/multiverse i386 Packages                    
   Unable to connect to xyz.archive.ubuntu.com:http: 
 Err [http://extras.ubuntu.com]("http://extras.ubuntu.com/") maverick Release.gpg                                             
   Could not connect to extras.ubuntu.com:80 (91.189.88.33). - connect (110: Connection timed out) 
 Err [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en                             
   Unable to connect to extras.ubuntu.com:http: 
 Err [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US                          
   Unable to connect to extras.ubuntu.com:http: 
 Ign [http://extras.ubuntu.com]("http://extras.ubuntu.com/") maverick Release                                                 
 Ign [http://extras.ubuntu.com]("http://extras.ubuntu.com/") maverick/main Sources      
 Ign [http://extras.ubuntu.com]("http://extras.ubuntu.com/") maverick/main i386 Packages 
 Ign [http://extras.ubuntu.com]("http://extras.ubuntu.com/") maverick/main Sources      
 Ign [http://extras.ubuntu.com]("http://extras.ubuntu.com/") maverick/main i386 Packages 
 Err [http://extras.ubuntu.com]("http://extras.ubuntu.com/") maverick/main Sources      
   Unable to connect to extras.ubuntu.com:http: 
 Err [http://extras.ubuntu.com]("http://extras.ubuntu.com/") maverick/main i386 Packages 
   Unable to connect to extras.ubuntu.com:http: 
 Err [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security Release.gpg 
   Could not connect to security.ubuntu.com:80 (91.189.92.184). - connect (110: Connection timed out) [IP: xxxxxxxx 
 Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en 
   Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
 Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US 
   Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
 Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en 
   Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
 Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US 
   Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
 Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en 
   Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
 Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US 
   Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
 Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en 
   Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
 Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US 
   Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
 Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security Release 
 Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/main Sources/DiffIndex 
 Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/restricted Sources/DiffIndex 
 Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/universe Sources 
 Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/multiverse Sources 
 Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/main i386 Packages/DiffIndex 
 Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/restricted i386 Packages/DiffIndex 
 Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/universe i386 Packages 
 Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/multiverse i386 Packages 
 Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/main Sources 
 Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/restricted Sources 
 Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/universe Sources 
 Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/multiverse Sources 
 Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/main i386 Packages 
 Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/restricted i386 Packages 
 Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/universe i386 Packages 
 Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/multiverse i386 Packages 
 Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/main Sources 
 Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/restricted Sources 
 Err [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/universe Sources 
   Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
 Err [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/multiverse Sources 
   Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
 Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/main i386 Packages 
 Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/restricted i386 Packages 
 Err [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/universe i386 Packages 
   Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
 Err [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/multiverse i386 Packages 
   Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
 Err [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/main Sources 
   Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
 Err [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/restricted Sources 
   Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
 Err [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/main i386 Packages 
   Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
 Err [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/restricted i386 Packages 
   Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Could not connect to xyz.archive.ubuntu.com:80 (58.65.218.244). - connect (110: Connection timed out) 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_US.bz2](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_US.bz2](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_US.bz2)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_US.bz2](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_US.bz2)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_US.bz2](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_US.bz2)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_US.bz2](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_US.bz2](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_US.bz2)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Could not connect to extras.ubuntu.com:80 (91.189.88.33). - connect (110: Connection timed out) 
  
 W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Unable to connect to extras.ubuntu.com:http: 
  
 W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Unable to connect to extras.ubuntu.com:http: 
  
 W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (91.189.92.184). - connect (110: Connection timed out) [IP: xxxxxxxx 
  
 W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2)  Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
  
 W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
  
 W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2)  Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
  
 W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
  
 W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2)  Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
  
 W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
  
 W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2)  Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
  
 W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
  
 W: Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/maverick/Release.gpg)  Could not connect to ppa.launchpad.net:80 (91.189.90.217). - connect (110: Connection timed out) 
  
 W: Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Unable to connect to ppa.launchpad.net:http: 
  
 W: Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Unable to connect to ppa.launchpad.net:http: 
  
 W: Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  Unable to connect to ppa.launchpad.net:http: 
  
 W: Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  Unable to connect to ppa.launchpad.net:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz](http://xyz.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz)  Unable to connect to xyz.archive.ubuntu.com:http: 
  
 W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  Unable to connect to extras.ubuntu.com:http: 
  
 W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  Unable to connect to extras.ubuntu.com:http: 
  
 W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz)  Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
  
 W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz)  Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
  
 W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz)  Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
  
 W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz)  Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
  
 W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz)  Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
  
 W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz)  Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
  
 W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz)  Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
  
 W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz)  Unable to connect to security.ubuntu.com:http: [IP: xxxxxxxx 
  
 E: Some index files fail
```please please guide me.

---

### Post by honey_bee on 2012-07-05
Thanks [prshah]("http://ubuntuforums.org/member.php?u=394709") for your valuable guidance.  I shall come back on my post after installing lbuntu and will again try my luck to install wine :-k

honey

---

