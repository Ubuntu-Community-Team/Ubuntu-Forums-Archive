---
title: "E: Couldn't find package ia32-libs"
date: 2009-04-14
forum: x86 64-bit Users
---

### Post by Magnimus84 on 2009-04-14
I'm a new user of Ubuntu 8.04. Running it on Vmware server 2 for the purpose of folding@home and to be able to do that i need ia32-libs.
This is what i get in the terminal:

magnus@Ubuntu1:~$ sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32-libs

Have tried to find an answer in the forums but unfortunately i couldn't...

Appreciate every bit of help!

---

### Post by stoneage on 2009-04-14
It is possible you don't have the appropriate repository enabled on /etc/apt/sources.list.
 I'm not sure which repo it is in though.....

If all else fails you can get it here - 
[http://packages.ubuntu.com/intrepid/ia32-libs](http://packages.ubuntu.com/intrepid/ia32-libs)

---

### Post by Magnimus84 on 2009-04-14
Thanks for answering!
I manually added "se.archive.ubuntu.com/ubuntu intrepid main universe! to my source list, but it didn't help...
When running sudo apt-get update in my terminal i get this:

```
magnus@Ubuntu1:~$ sudo apt-get update
Hit http://se.archive.ubuntu.com hardy Release.gpg
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://se.archive.ubuntu.com hardy/main Translation-en_US
Hit http://archive.canonical.com hardy Release.gpg                   
Ign http://archive.canonical.com hardy/partner Translation-en_US     
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release                
Ign http://se.archive.ubuntu.com hardy/restricted Translation-en_US  
Ign http://se.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://se.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://se.archive.ubuntu.com hardy-updates Release.gpg
Ign http://se.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://se.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://se.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://se.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://archive.canonical.com hardy Release                      
Hit http://se.archive.ubuntu.com intrepid Release.gpg               
Ign http://se.archive.ubuntu.com intrepid/main Translation-en_US   
Ign http://se.archive.ubuntu.com intrepid/universe Translation-en_US
Hit http://se.archive.ubuntu.com hardy Release                     
Hit http://se.archive.ubuntu.com hardy-updates Release             
Hit http://security.ubuntu.com hardy-security/main Packages        
Hit http://se.archive.ubuntu.com intrepid Release                              
Hit http://security.ubuntu.com hardy-security/restricted Packages    
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Ign http://archive.canonical.com hardy/partner Packages                        
Hit http://security.ubuntu.com hardy-security/universe Sources                 
Hit http://security.ubuntu.com hardy-security/multiverse Packages    
Hit http://security.ubuntu.com hardy-security/multiverse Sources     
Hit http://se.archive.ubuntu.com hardy/main Packages                 
Hit http://se.archive.ubuntu.com hardy/restricted Packages
Hit http://se.archive.ubuntu.com hardy/main Sources
Hit http://se.archive.ubuntu.com hardy/restricted Sources
Ign http://archive.canonical.com hardy/partner Sources
Hit http://se.archive.ubuntu.com hardy/universe Packages
Hit http://se.archive.ubuntu.com hardy/universe Sources                        
Hit http://se.archive.ubuntu.com hardy/multiverse Packages                     
Hit http://se.archive.ubuntu.com hardy/multiverse Sources                      
Hit http://se.archive.ubuntu.com hardy-updates/main Packages                   
Hit http://se.archive.ubuntu.com hardy-updates/restricted Packages             
Hit http://se.archive.ubuntu.com hardy-updates/main Sources                    
Hit http://se.archive.ubuntu.com hardy-updates/restricted Sources              
Hit http://se.archive.ubuntu.com hardy-updates/universe Packages               
Hit http://se.archive.ubuntu.com hardy-updates/universe Sources                
Hit http://se.archive.ubuntu.com hardy-updates/multiverse Packages             
Hit http://se.archive.ubuntu.com hardy-updates/multiverse Sources              
Hit http://se.archive.ubuntu.com intrepid/main Packages                        
Hit http://se.archive.ubuntu.com intrepid/universe Packages
Hit http://archive.canonical.com hardy/partner Packages
Hit http://archive.canonical.com hardy/partner Sources
Reading package lists... Done
```

After that i tried to install ia32-libs again and got the same error as before...

Another question: Why are some sources "Ign" instead of "Hit" in the above list?

I'm running Ubuntu 8.04 64bit as guest system on VMware server 2. Host system is Win XP pro 32bit...

---

### Post by Magnimus84 on 2009-04-14
Well... I finally found out wy it wasn't working...
Turns out i installed the 32bit version of Ubuntu! *Slaps self*
Lets hope everything works the other time around!

---

### Post by Yellow Pasque on 2009-04-15
Generally, it's a bad idea to mix ubuntu intrepid and hardy repos that offer the same packages. It rarely ends well for the user. Use the hardy repos.

---

### Post by stoneage on 2009-04-15
> **Temüjin said:**
> Generally, it's a bad idea to mix ubuntu intrepid and hardy repos that offer the same packages. It rarely ends well for the user. Use the hardy repos.

Whoops, I wasn't paying attention.

I should have you can get it here - [http://packages.ubuntu.com/hardy/ia32-libs](http://packages.ubuntu.com/hardy/ia32-libs)

---

