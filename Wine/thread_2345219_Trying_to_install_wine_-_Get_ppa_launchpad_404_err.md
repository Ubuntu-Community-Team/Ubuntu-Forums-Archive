---
title: "Trying to install wine - Get ppa launchpad 404 error"
date: 2016-12-01
forum: Wine
---

### Post by xoibsurferx on 2016-12-01
Hello everyone!,

 I'm trying to install Wine and I keep getting the 404 Not Found errors with the links below as what can't be found. I have already ran sudo apt-get update and sudo apt-get upgrade 
and neither fixed my issue. 

[http://ppa.launchpad.net/ondrej/php5/ubuntu/pool/main/libg/libgd2/libgd3_2.1.1-4.1+deb.sury.org~trusty+1_i386.deb](http://ppa.launchpad.net/ondrej/php5/ubuntu/pool/main/libg/libgd2/libgd3_2.1.1-4.1+deb.sury.org~trusty+1_i386.deb)
[http://ppa.launchpad.net/ondrej/php5/ubuntu/pool/main/libg/libgd2/libgd3_2.1.1-4.1+deb.sury.org~trusty+1_i386.deb](http://ppa.launchpad.net/ondrej/php5/ubuntu/pool/main/libg/libgd2/libgd3_2.1.1-4.1+deb.sury.org~trusty+1_i386.deb)

Please let me know what I need to do to fix this! I'm on Ubuntu 14.04.

---

### Post by Dennis N on 2016-12-01
The file simply doesn't exist at that URL. What is wrong with using the Wine in the Ubuntu repository?

---

### Post by xoibsurferx on 2016-12-01
When I try to download wine through the software manager it just says package dependencies cannot be resolved.

These are the "details"
 wine1.6: Depends: wine1.6-amd64 (= 1:1.6.2-0ubuntu4) but 1:1.6.2-0ubuntu4 is to be installed         Depends: wine1.6-i386 (= 1:1.6.2-0ubuntu4) but it is a virtual package

---

### Post by Bashing-om on 2016-12-01
xoibsurferx; Hello;

What returns ; posted back - between code tags - of terminal command:
```

apt-cache policy wine1.6 wine1.6-amd64

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
And let's see if there is not a PPA messing with the works.

[INDENT][INDENT]there can be only one
[/INDENT][/INDENT]

---

### Post by xoibsurferx on 2016-12-01
I ran the command you asked and below is what outputted. 
```

wine1.6:
  Installed: (none)
  Candidate: 1:1.6.2-0ubuntu4
  Version table:
     1:1.6.2-0ubuntu4 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/universe amd64 Packages
wine1.6-amd64:
  Installed: (none)
  Candidate: 1:1.6.2-0ubuntu4
  Version table:
     1:1.6.2-0ubuntu4 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/universe amd64 Packages

```

---

### Post by howefield on 2016-12-02
Moved to the "*Wine*" forum.

---

### Post by xoibsurferx on 2016-12-02
Thank you! I wasn't sure where to post this.

---

### Post by ian-weisser on 2016-12-03
Often the easiest option:

1) Delete the PPA. You don't need it for Wine 1.6.
2) Delete all PPA packages in your local cache (sudo apt-get clean)
3) Since you changed your sources, update your package database (sudo apt-get update)
4) Install Wine 1.6 from the Ubuntu repositories (sudo apt-get install wine1.6)

If you get any errors along the way, STOP. Show us the complete output leading to the error.

---

### Post by xoibsurferx on 2016-12-03
I did exactly as above (I deleted the PPAs via settings/other software. 

```

keith@Saturn1:~$ sudo apt-get clean
[sudo] password for keith: 
keith@Saturn1:~$ sudo apt-get update
Ign http://dl.google.com stable InRelease
Hit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release                                        
Ign http://archive.ubuntu.com trusty InRelease                                 
Ign http://archive.canonical.com trusty InRelease                              
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://dell.archive.canonical.com trusty-dell-biz-vivid-skl InRelease      
Ign http://oem.archive.canonical.com trusty-oem-sp1 InRelease                  
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://archive.ubuntu.com trusty-updates InRelease                         
Hit http://archive.canonical.com trusty Release.gpg                            
Ign http://dell.archive.canonical.com trusty-dell-dino2 InRelease              
Hit http://ppa.launchpad.net trusty InRelease                                  
Ign http://oem.archive.canonical.com trusty-oem InRelease                      
Ign http://toolbelt.heroku.com ./ InRelease                                    
Hit http://archive.ubuntu.com trusty-backports InRelease                       
Hit http://archive.canonical.com trusty Release                                
Ign http://dell.archive.canonical.com trusty-dell InRelease                    
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://oem.archive.canonical.com trusty-oem-sp1 Release.gpg                
Hit http://toolbelt.heroku.com ./ Release.gpg                                  
Hit http://archive.ubuntu.com trusty-security InRelease                        
Hit http://dell.archive.canonical.com trusty-dell-biz-vivid-skl Release.gpg    
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://oem.archive.canonical.com trusty-oem Release.gpg                    
Hit http://toolbelt.heroku.com ./ Release                                      
Hit http://archive.ubuntu.com trusty Release.gpg                               
Hit http://toolbelt.heroku.com ./ Packages                                     
Hit http://dell.archive.canonical.com trusty-dell-dino2 Release.gpg            
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://oem.archive.canonical.com trusty-oem-sp1 Release                    
Hit http://archive.ubuntu.com trusty-updates/main Sources                      
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://dell.archive.canonical.com trusty-dell Release.gpg                  
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://oem.archive.canonical.com trusty-oem Release                        
Ign http://dl.google.com stable/main Translation-en                            
Hit http://archive.ubuntu.com trusty-updates/restricted Sources                
Hit http://dell.archive.canonical.com trusty-dell-biz-vivid-skl Release        
Hit http://archive.canonical.com trusty/partner Translation-en                 
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://oem.archive.canonical.com trusty-oem-sp1/public Sources             
Hit http://archive.ubuntu.com trusty-updates/universe Sources                  
Hit http://dell.archive.canonical.com trusty-dell-dino2 Release                
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://oem.archive.canonical.com trusty-oem-sp1/public amd64 Packages      
Ign http://toolbelt.heroku.com ./ Translation-en_US                            
Hit http://archive.ubuntu.com trusty-updates/multiverse Sources                
Ign http://toolbelt.heroku.com ./ Translation-en                               
Hit http://dell.archive.canonical.com trusty-dell Release                      
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://oem.archive.canonical.com trusty-oem-sp1/public i386 Packages       
Hit http://archive.ubuntu.com trusty-updates/main amd64 Packages               
Hit http://dell.archive.canonical.com trusty-dell-biz-vivid-skl/public Sources 
Ign http://ppa.launchpad.net trusty Release.gpg                                
Hit http://archive.ubuntu.com trusty-updates/restricted amd64 Packages         
Hit http://dell.archive.canonical.com trusty-dell-biz-vivid-skl/public amd64 Packages
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://archive.ubuntu.com trusty-updates/universe amd64 Packages           
Hit http://dell.archive.canonical.com trusty-dell-biz-vivid-skl/public i386 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://oem.archive.canonical.com trusty-oem/public Sources                 
Hit http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://oem.archive.canonical.com trusty-oem/public amd64 Packages          
Hit http://archive.ubuntu.com trusty-updates/main i386 Packages                
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://archive.ubuntu.com trusty-updates/restricted i386 Packages          
Hit http://oem.archive.canonical.com trusty-oem/public i386 Packages           
Hit http://dell.archive.canonical.com trusty-dell-dino2/public Sources         
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://archive.ubuntu.com trusty-updates/universe i386 Packages            
Hit http://dell.archive.canonical.com trusty-dell-dino2/public amd64 Packages  
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://archive.ubuntu.com trusty-updates/multiverse i386 Packages          
Hit http://dell.archive.canonical.com trusty-dell-dino2/public i386 Packages   
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://archive.ubuntu.com trusty-updates/main Translation-en               
Ign http://ppa.launchpad.net trusty Release                                    
Hit http://archive.ubuntu.com trusty-updates/multiverse Translation-en         
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en         
Hit http://dell.archive.canonical.com trusty-dell/public Sources               
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://archive.ubuntu.com trusty-updates/universe Translation-en           
Hit http://dell.archive.canonical.com trusty-dell/public amd64 Packages        
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://archive.ubuntu.com trusty-backports/main Sources                    
Hit http://dell.archive.canonical.com trusty-dell/public i386 Packages         
Err http://ppa.launchpad.net trusty/main Sources                               
  
Hit http://archive.ubuntu.com trusty-backports/restricted Sources              
Err http://ppa.launchpad.net trusty/main Sources                               
  
Hit http://archive.ubuntu.com trusty-backports/universe Sources                
Err http://ppa.launchpad.net trusty/main Sources                               
  
Hit http://archive.ubuntu.com trusty-backports/multiverse Sources              
Err http://ppa.launchpad.net trusty/main Sources                               
  
Hit http://archive.ubuntu.com trusty-backports/main amd64 Packages             
Err http://ppa.launchpad.net trusty/main Sources                               
  404  Not Found
Hit http://archive.ubuntu.com trusty-backports/restricted amd64 Packages       
Hit http://archive.ubuntu.com trusty-backports/universe amd64 Packages         
Hit http://archive.ubuntu.com trusty-backports/multiverse amd64 Packages       
Hit http://archive.ubuntu.com trusty-backports/main i386 Packages              
Ign http://oem.archive.canonical.com trusty-oem-sp1/public Translation-en_US   
Hit http://archive.ubuntu.com trusty-backports/restricted i386 Packages
Ign http://oem.archive.canonical.com trusty-oem-sp1/public Translation-en      
Hit http://archive.ubuntu.com trusty-backports/universe i386 Packages 
Ign http://oem.archive.canonical.com trusty-oem/public Translation-en_US       
Hit http://archive.ubuntu.com trusty-backports/multiverse i386 Packages
Ign http://oem.archive.canonical.com trusty-oem/public Translation-en          
Hit http://archive.ubuntu.com trusty-backports/main Translation-en    
Hit http://archive.ubuntu.com trusty-backports/multiverse Translation-en 
Hit http://archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://archive.ubuntu.com trusty-backports/universe Translation-en
Hit http://archive.ubuntu.com trusty-security/main Sources              
Hit http://archive.ubuntu.com trusty-security/restricted Sources 
Hit http://archive.ubuntu.com trusty-security/universe Sources    
Hit http://archive.ubuntu.com trusty-security/multiverse Sources 
Hit http://archive.ubuntu.com trusty-security/main amd64 Packages 
Hit http://archive.ubuntu.com trusty-security/restricted amd64 Packages
Ign http://dell.archive.canonical.com trusty-dell-biz-vivid-skl/public Translation-en_US
Hit http://archive.ubuntu.com trusty-security/universe amd64 Packages
Ign http://dell.archive.canonical.com trusty-dell-biz-vivid-skl/public Translation-en
Hit http://archive.ubuntu.com trusty-security/multiverse amd64 Packages
Ign http://dell.archive.canonical.com trusty-dell-dino2/public Translation-en_US
Hit http://archive.ubuntu.com trusty-security/main i386 Packages
Ign http://dell.archive.canonical.com trusty-dell-dino2/public Translation-en
Hit http://archive.ubuntu.com trusty-security/restricted i386 Packages
Ign http://dell.archive.canonical.com trusty-dell/public Translation-en_US
Hit http://archive.ubuntu.com trusty-security/universe i386 Packages
Ign http://dell.archive.canonical.com trusty-dell/public Translation-en
Hit http://archive.ubuntu.com trusty-security/multiverse i386 Packages
Hit http://archive.ubuntu.com trusty-security/main Translation-en
Hit http://archive.ubuntu.com trusty-security/multiverse Translation-en
Hit http://archive.ubuntu.com trusty-security/restricted Translation-en
Hit http://archive.ubuntu.com trusty-security/universe Translation-en
Hit http://archive.ubuntu.com trusty Release      
Hit http://archive.ubuntu.com trusty/main Sources                              
Hit http://archive.ubuntu.com trusty/restricted Sources                        
Hit http://archive.ubuntu.com trusty/universe Sources                          
Hit http://archive.ubuntu.com trusty/multiverse Sources                        
Hit http://archive.ubuntu.com trusty/main amd64 Packages                       
Hit http://archive.ubuntu.com trusty/restricted amd64 Packages                 
Hit http://archive.ubuntu.com trusty/universe amd64 Packages                   
Hit http://archive.ubuntu.com trusty/multiverse amd64 Packages                 
Hit http://archive.ubuntu.com trusty/main i386 Packages                        
Hit http://archive.ubuntu.com trusty/restricted i386 Packages                  
Hit http://archive.ubuntu.com trusty/universe i386 Packages                    
Hit http://archive.ubuntu.com trusty/multiverse i386 Packages                  
Hit http://archive.ubuntu.com trusty/main Translation-en                       
Hit http://archive.ubuntu.com trusty/multiverse Translation-en                 
Hit http://archive.ubuntu.com trusty/restricted Translation-en                 
Hit http://archive.ubuntu.com trusty/universe Translation-en                   
Ign http://archive.ubuntu.com trusty/main Translation-en_US                    
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US              
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US              
Ign http://archive.ubuntu.com trusty/universe Translation-en_US                
W: Failed to fetch http://ppa.launchpad.net/ondrej/php5/ubuntu/dists/trusty/main/source/Sources  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.
keith@Saturn1:~$ sudo apt-get install wine1.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 wine1.6 : Depends: wine1.6-i386 (= 1:1.6.2-0ubuntu4)
E: Unable to correct problems, you have held broken packages.

```

---

### Post by ian-weisser on 2016-12-03
Ah, Step 1.5) Delete all packaged from that PPA.

Follow the rabbit down the hole. The following should produce an error. Please show us the complete output.
```
sudo apt-get install wine1.6-i386
```

---

### Post by xoibsurferx on 2016-12-03
Output from command above is: 

```

keith@Saturn1:~$ sudo apt-get install wine1.6-i386
[sudo] password for keith: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 wine1.6-i386:i386 : Depends: libgphoto2-6:i386 (>= 2.5.2) but it is not going to be installed
                     Depends: libpulse0:i386 (>= 1:0.99.1) but it is not going to be installed
                     Recommends: libasound2-plugins:i386 but it is not going to be installed
                     Recommends: libsane:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
keith@Saturn1:~$
```

---

### Post by Bashing-om on 2016-12-03
xoibsurferx; Hey;

As we chase down this rabbit hole;
Show us your sources lists files:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
to make sure we take care of this error condition:
> 
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources


And then we address the dependency issue.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]together we can
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mc4man on 2016-12-03
libgphoto2-6 depends on libgd3 so for wine you'd need libgd3:i386 of the same version that's already installed (the amd64 one.
You might want to check on that for *starters*

---

### Post by xoibsurferx on 2016-12-03
Here's the output for the commands you posted. 

```

keith@Saturn1:~$ cat -n /etc/apt/sources.list
     1	
     2	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     3	# newer versions of the distribution.
     4	deb http://archive.ubuntu.com/ubuntu trusty main restricted
     5	deb-src http://archive.ubuntu.com/ubuntu trusty main restricted
     6	
     7	## Major bug fix updates produced after the final release of the
     8	## distribution.
     9	deb http://archive.ubuntu.com/ubuntu trusty-updates main restricted
    10	deb-src http://archive.ubuntu.com/ubuntu trusty-updates main restricted
    11	
    12	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    13	## team. Also, please note that software in universe WILL NOT receive any
    14	## review or updates from the Ubuntu security team.
    15	deb http://archive.ubuntu.com/ubuntu trusty universe
    16	deb-src http://archive.ubuntu.com/ubuntu trusty universe
    17	deb http://archive.ubuntu.com/ubuntu trusty-updates universe
    18	deb-src http://archive.ubuntu.com/ubuntu trusty-updates universe
    19	
    20	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    21	## team, and may not be under a free licence. Please satisfy yourself as to
    22	## your rights to use the software. Also, please note that software in
    23	## multiverse WILL NOT receive any review or updates from the Ubuntu
    24	## security team.
    25	deb http://archive.ubuntu.com/ubuntu trusty multiverse
    26	deb-src http://archive.ubuntu.com/ubuntu trusty multiverse
    27	deb http://archive.ubuntu.com/ubuntu trusty-updates multiverse
    28	deb-src http://archive.ubuntu.com/ubuntu trusty-updates multiverse
    29	
    30	## N.B. software from this repository may not have been tested as
    31	## extensively as that contained in the main release, although it includes
    32	## newer versions of some applications which may provide useful features.
    33	## Also, please note that software in backports WILL NOT receive any review
    34	## or updates from the Ubuntu security team.
    35	deb http://archive.ubuntu.com/ubuntu trusty-backports main restricted universe multiverse
    36	deb-src http://archive.ubuntu.com/ubuntu trusty-backports main restricted universe multiverse
    37	
    38	deb http://archive.ubuntu.com/ubuntu trusty-security main restricted
    39	deb-src http://archive.ubuntu.com/ubuntu trusty-security main restricted
    40	deb http://archive.ubuntu.com/ubuntu trusty-security universe
    41	deb-src http://archive.ubuntu.com/ubuntu trusty-security universe
    42	deb http://archive.ubuntu.com/ubuntu trusty-security multiverse
    43	deb-src http://archive.ubuntu.com/ubuntu trusty-security multiverse
    44	
    45	## This software is not part of Ubuntu, but is offered by Canonical and the
    46	## respective vendors as a service to Ubuntu users.
    47	deb http://archive.canonical.com/ubuntu trusty partner
    48	deb-src http://archive.canonical.com/ubuntu trusty partner
    49	
    50	## Uncomment the following two lines to add software from Ubuntu's
    51	## 'extras' repository.
    52	## This software is not part of Ubuntu, but is offered by third-party
    53	## developers who want to ship their latest software.
    54	# deb http://extras.ubuntu.com/ubuntu trusty main
    55	# deb-src http://extras.ubuntu.com/ubuntu trusty main
    56	
keith@Saturn1:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/chris-lea-node_js-trusty.list <==
deb http://ppa.launchpad.net/chris-lea/node.js/ubuntu trusty main
# deb-src http://ppa.launchpad.net/chris-lea/node.js/ubuntu trusty main


==> /etc/apt/sources.list.d/chris-lea-node_js-trusty.list.save <==
deb http://ppa.launchpad.net/chris-lea/node.js/ubuntu trusty main
# deb-src http://ppa.launchpad.net/chris-lea/node.js/ubuntu trusty main


==> /etc/apt/sources.list.d/git-core-ppa-trusty.list <==
deb http://ppa.launchpad.net/git-core/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/git-core/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/git-core-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/git-core/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/git-core/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main


==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main


==> /etc/apt/sources.list.d/heroku.list <==
deb http://toolbelt.heroku.com/ubuntu ./


==> /etc/apt/sources.list.d/heroku.list.save <==
deb http://toolbelt.heroku.com/ubuntu ./


==> /etc/apt/sources.list.d/ondrej-php5-trusty.list <==
# deb http://ppa.launchpad.net/ondrej/php5/ubuntu trusty main
deb-src http://ppa.launchpad.net/ondrej/php5/ubuntu trusty main


==> /etc/apt/sources.list.d/ondrej-php5-trusty.list.save <==
# deb http://ppa.launchpad.net/ondrej/php5/ubuntu trusty main
deb-src http://ppa.launchpad.net/ondrej/php5/ubuntu trusty main


==> /etc/apt/sources.list.d/remmina-ppa-team-remmina-next-trusty.list <==
deb http://ppa.launchpad.net/remmina-ppa-team/remmina-next/ubuntu trusty main
# deb-src http://ppa.launchpad.net/remmina-ppa-team/remmina-next/ubuntu trusty main


==> /etc/apt/sources.list.d/remmina-ppa-team-remmina-next-trusty.list.save <==
deb http://ppa.launchpad.net/remmina-ppa-team/remmina-next/ubuntu trusty main
# deb-src http://ppa.launchpad.net/remmina-ppa-team/remmina-next/ubuntu trusty main


==> /etc/apt/sources.list.d/sources-backup.list <==




==> /etc/apt/sources.list.d/sources-backup.list.save <==




==> /etc/apt/sources.list.d/trusty-dell-biz-vivid-skl.list <==
deb http://dell.archive.canonical.com/updates/ trusty-dell-biz-vivid-skl public
deb-src http://dell.archive.canonical.com/updates/ trusty-dell-biz-vivid-skl public


==> /etc/apt/sources.list.d/trusty-dell-biz-vivid-skl.list.save <==
deb http://dell.archive.canonical.com/updates/ trusty-dell-biz-vivid-skl public
deb-src http://dell.archive.canonical.com/updates/ trusty-dell-biz-vivid-skl public


==> /etc/apt/sources.list.d/trusty-dell-dino2.list <==
deb http://dell.archive.canonical.com/updates/ trusty-dell-dino2 public
deb-src http://dell.archive.canonical.com/updates/ trusty-dell-dino2 public


==> /etc/apt/sources.list.d/trusty-dell-dino2.list.save <==
deb http://dell.archive.canonical.com/updates/ trusty-dell-dino2 public
deb-src http://dell.archive.canonical.com/updates/ trusty-dell-dino2 public


==> /etc/apt/sources.list.d/trusty-dell.list <==
deb http://dell.archive.canonical.com/updates/ trusty-dell public
deb-src http://dell.archive.canonical.com/updates/ trusty-dell public


==> /etc/apt/sources.list.d/trusty-dell.list.save <==
deb http://dell.archive.canonical.com/updates/ trusty-dell public
deb-src http://dell.archive.canonical.com/updates/ trusty-dell public


==> /etc/apt/sources.list.d/trusty-oem.list <==
deb http://oem.archive.canonical.com/updates/ trusty-oem public
deb-src http://oem.archive.canonical.com/updates/ trusty-oem public


==> /etc/apt/sources.list.d/trusty-oem.list.save <==
deb http://oem.archive.canonical.com/updates/ trusty-oem public
deb-src http://oem.archive.canonical.com/updates/ trusty-oem public


==> /etc/apt/sources.list.d/trusty-oem-sp1.list <==
deb http://oem.archive.canonical.com/updates/ trusty-oem-sp1 public
deb-src http://oem.archive.canonical.com/updates/ trusty-oem-sp1 public


==> /etc/apt/sources.list.d/trusty-oem-sp1.list.save <==
deb http://oem.archive.canonical.com/updates/ trusty-oem-sp1 public
deb-src http://oem.archive.canonical.com/updates/ trusty-oem-sp1 public


==> /etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list <==


==> /etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list.save <==


==> /etc/apt/sources.list.d/webupd8team-sublime-text-3-trusty.list <==
deb http://ppa.launchpad.net/webupd8team/sublime-text-3/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/sublime-text-3/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/sublime-text-3/ubuntu trusty main


==> /etc/apt/sources.list.d/webupd8team-sublime-text-3-trusty.list.save <==
deb http://ppa.launchpad.net/webupd8team/sublime-text-3/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/sublime-text-3/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/sublime-text-3/ubuntu trusty main
keith@Saturn1:~$ 

```

---

### Post by Bashing-om on 2016-12-03
xoibsurferx; Well,

As the package manager advises:
Looks to be this PPA:
[http://ppa.launchpad.net/ondrej/php5/ubuntu](http://ppa.launchpad.net/ondrej/php5/ubuntu)

on checking I get 
> 
The requested URL /ondrej/php5/ubuntu was not found on this server.

Disable this PPA and try again:
```

sudo apt update
sudo apt upgrade

```

When these run clean, it is back to the dependency issue.

[INDENT][INDENT]one more for the road
[/INDENT][/INDENT]

---

### Post by mc4man on 2016-12-03
run & post
```
apt-cache policy libgd3
```

---

### Post by xoibsurferx on 2016-12-03
I did these two and this was the output after disabling the php5/ubuntu ppa. 

```

keith@Saturn1:~$ sudo apt update
[sudo] password for keith: 
Ign http://dl.google.com stable InRelease
Hit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release                                        
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://archive.ubuntu.com trusty InRelease                                 
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.ubuntu.com trusty-updates InRelease                         
Ign http://dell.archive.canonical.com trusty-dell-biz-vivid-skl InRelease      
Ign http://archive.canonical.com trusty InRelease                              
Ign http://oem.archive.canonical.com trusty-oem-sp1 InRelease                  
Hit http://archive.ubuntu.com trusty-backports InRelease                       
Hit http://ppa.launchpad.net trusty InRelease                                  
Ign http://dell.archive.canonical.com trusty-dell-dino2 InRelease              
Ign http://toolbelt.heroku.com ./ InRelease                                    
Hit http://archive.canonical.com trusty Release.gpg                            
Ign http://oem.archive.canonical.com trusty-oem InRelease                      
Hit http://toolbelt.heroku.com ./ Release.gpg                                  
Hit http://archive.ubuntu.com trusty-security InRelease                        
Hit http://ppa.launchpad.net trusty InRelease                                  
Ign http://dell.archive.canonical.com trusty-dell InRelease                    
Hit http://archive.canonical.com trusty Release                                
Hit http://oem.archive.canonical.com trusty-oem-sp1 Release.gpg                
Hit http://toolbelt.heroku.com ./ Release                                      
Hit http://archive.ubuntu.com trusty Release.gpg                               
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://dell.archive.canonical.com trusty-dell-biz-vivid-skl Release.gpg    
Hit http://toolbelt.heroku.com ./ Packages                                     
Hit http://oem.archive.canonical.com trusty-oem Release.gpg                    
Hit http://archive.canonical.com trusty/partner Sources                        
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://archive.ubuntu.com trusty-updates/main Sources                      
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Ign http://dl.google.com stable/main Translation-en                            
Hit http://dell.archive.canonical.com trusty-dell-dino2 Release.gpg            
Hit http://oem.archive.canonical.com trusty-oem-sp1 Release                    
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://archive.ubuntu.com trusty-updates/restricted Sources                
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://dell.archive.canonical.com trusty-dell Release.gpg                  
Hit http://oem.archive.canonical.com trusty-oem Release                        
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://archive.ubuntu.com trusty-updates/universe Sources                  
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://dell.archive.canonical.com trusty-dell-biz-vivid-skl Release        
Ign http://toolbelt.heroku.com ./ Translation-en_US                            
Hit http://oem.archive.canonical.com trusty-oem-sp1/public Sources             
Hit http://archive.canonical.com trusty/partner Translation-en                 
Hit http://archive.ubuntu.com trusty-updates/multiverse Sources                
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://dell.archive.canonical.com trusty-dell-dino2 Release                
Ign http://toolbelt.heroku.com ./ Translation-en                               
Hit http://archive.ubuntu.com trusty-updates/main amd64 Packages               
Hit http://oem.archive.canonical.com trusty-oem-sp1/public amd64 Packages      
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://dell.archive.canonical.com trusty-dell Release                      
Hit http://archive.ubuntu.com trusty-updates/restricted amd64 Packages         
Hit http://oem.archive.canonical.com trusty-oem-sp1/public i386 Packages       
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://dell.archive.canonical.com trusty-dell-biz-vivid-skl/public Sources 
Hit http://archive.ubuntu.com trusty-updates/universe amd64 Packages           
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://dell.archive.canonical.com trusty-dell-biz-vivid-skl/public amd64 Packages
Hit http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages         
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://dell.archive.canonical.com trusty-dell-biz-vivid-skl/public i386 Packages
Hit http://archive.ubuntu.com trusty-updates/main i386 Packages                
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://oem.archive.canonical.com trusty-oem/public Sources                 
Hit http://archive.ubuntu.com trusty-updates/restricted i386 Packages          
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://oem.archive.canonical.com trusty-oem/public amd64 Packages          
Hit http://archive.ubuntu.com trusty-updates/universe i386 Packages            
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://oem.archive.canonical.com trusty-oem/public i386 Packages           
Hit http://dell.archive.canonical.com trusty-dell-dino2/public Sources         
Hit http://archive.ubuntu.com trusty-updates/multiverse i386 Packages          
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://dell.archive.canonical.com trusty-dell-dino2/public amd64 Packages  
Hit http://archive.ubuntu.com trusty-updates/main Translation-en               
Hit http://dell.archive.canonical.com trusty-dell-dino2/public i386 Packages   
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://archive.ubuntu.com trusty-updates/multiverse Translation-en         
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en         
Hit http://archive.ubuntu.com trusty-updates/universe Translation-en           
Hit http://dell.archive.canonical.com trusty-dell/public Sources               
Hit http://archive.ubuntu.com trusty-backports/main Sources                    
Hit http://dell.archive.canonical.com trusty-dell/public amd64 Packages        
Hit http://archive.ubuntu.com trusty-backports/restricted Sources     
Hit http://archive.ubuntu.com trusty-backports/universe Sources                
Hit http://dell.archive.canonical.com trusty-dell/public i386 Packages         
Hit http://archive.ubuntu.com trusty-backports/multiverse Sources              
Hit http://archive.ubuntu.com trusty-backports/main amd64 Packages             
Hit http://archive.ubuntu.com trusty-backports/restricted amd64 Packages       
Hit http://archive.ubuntu.com trusty-backports/universe amd64 Packages         
Hit http://archive.ubuntu.com trusty-backports/multiverse amd64 Packages       
Hit http://archive.ubuntu.com trusty-backports/main i386 Packages              
Hit http://archive.ubuntu.com trusty-backports/restricted i386 Packages        
Hit http://archive.ubuntu.com trusty-backports/universe i386 Packages          
Ign http://oem.archive.canonical.com trusty-oem-sp1/public Translation-en_US   
Hit http://archive.ubuntu.com trusty-backports/multiverse i386 Packages
Ign http://oem.archive.canonical.com trusty-oem-sp1/public Translation-en      
Hit http://archive.ubuntu.com trusty-backports/main Translation-en    
Ign http://oem.archive.canonical.com trusty-oem/public Translation-en_US       
Hit http://archive.ubuntu.com trusty-backports/multiverse Translation-en
Ign http://oem.archive.canonical.com trusty-oem/public Translation-en          
Hit http://archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://archive.ubuntu.com trusty-backports/universe Translation-en
Hit http://archive.ubuntu.com trusty-security/main Sources              
Hit http://archive.ubuntu.com trusty-security/restricted Sources 
Hit http://archive.ubuntu.com trusty-security/universe Sources    
Hit http://archive.ubuntu.com trusty-security/multiverse Sources 
Hit http://archive.ubuntu.com trusty-security/main amd64 Packages 
Hit http://archive.ubuntu.com trusty-security/restricted amd64 Packages
Hit http://archive.ubuntu.com trusty-security/universe amd64 Packages
Hit http://archive.ubuntu.com trusty-security/multiverse amd64 Packages
Hit http://archive.ubuntu.com trusty-security/main i386 Packages   
Ign http://dell.archive.canonical.com trusty-dell-biz-vivid-skl/public Translation-en_US
Hit http://archive.ubuntu.com trusty-security/restricted i386 Packages
Ign http://dell.archive.canonical.com trusty-dell-biz-vivid-skl/public Translation-en
Hit http://archive.ubuntu.com trusty-security/universe i386 Packages
Hit http://archive.ubuntu.com trusty-security/multiverse i386 Packages
Ign http://dell.archive.canonical.com trusty-dell-dino2/public Translation-en_US
Hit http://archive.ubuntu.com trusty-security/main Translation-en  
Ign http://dell.archive.canonical.com trusty-dell-dino2/public Translation-en
Hit http://archive.ubuntu.com trusty-security/multiverse Translation-en        
Ign http://dell.archive.canonical.com trusty-dell/public Translation-en_US     
Hit http://archive.ubuntu.com trusty-security/restricted Translation-en        
Ign http://dell.archive.canonical.com trusty-dell/public Translation-en        
Hit http://archive.ubuntu.com trusty-security/universe Translation-en          
Hit http://archive.ubuntu.com trusty Release                                   
Hit http://archive.ubuntu.com trusty/main Sources                              
Hit http://archive.ubuntu.com trusty/restricted Sources                        
Hit http://archive.ubuntu.com trusty/universe Sources                          
Hit http://archive.ubuntu.com trusty/multiverse Sources                        
Hit http://archive.ubuntu.com trusty/main amd64 Packages                       
Hit http://archive.ubuntu.com trusty/restricted amd64 Packages                 
Hit http://archive.ubuntu.com trusty/universe amd64 Packages                   
Hit http://archive.ubuntu.com trusty/multiverse amd64 Packages                 
Hit http://archive.ubuntu.com trusty/main i386 Packages                        
Hit http://archive.ubuntu.com trusty/restricted i386 Packages                  
Hit http://archive.ubuntu.com trusty/universe i386 Packages                    
Hit http://archive.ubuntu.com trusty/multiverse i386 Packages                  
Hit http://archive.ubuntu.com trusty/main Translation-en                       
Hit http://archive.ubuntu.com trusty/multiverse Translation-en                 
Hit http://archive.ubuntu.com trusty/restricted Translation-en                 
Hit http://archive.ubuntu.com trusty/universe Translation-en                   
Ign http://archive.ubuntu.com trusty/main Translation-en_US                    
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US              
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US              
Ign http://archive.ubuntu.com trusty/universe Translation-en_US                
Reading package lists... Done 
keith@Saturn1:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
keith@Saturn1:~$ 

```

m4man,

 I ran that command and got the below output. 

```

keith@Saturn1:~$ apt-cache policy libgd3
libgd3:
  Installed: 2.1.1-4.1+deb.sury.org~trusty+1
  Candidate: 2.1.1-4.1+deb.sury.org~trusty+1
  Version table:
 *** 2.1.1-4.1+deb.sury.org~trusty+1 0
        100 /var/lib/dpkg/status
     2.1.0-3ubuntu0.5 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     2.1.0-3 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
keith@Saturn1:~$ 

```

---

### Post by mc4man on 2016-12-03
You need to get back on that php ppa then either keep up with it or use ppa-purge on.
It now appears to be here - 
[https://launchpad.net/~ondrej/+archive/ubuntu/php](https://launchpad.net/~ondrej/+archive/ubuntu/php)

(your packages are dated, ex - [https://launchpad.net/~ondrej/+archive/ubuntu/php/+build/9629524](https://launchpad.net/~ondrej/+archive/ubuntu/php/+build/9629524)

So add the above ppa, update your sources & then decide what you want. If going the ppa-purge route you may need to upgrade to latest ppa packages, then use ppa-purge.
Or just upgrade & keep the ppa 
After that there's a good chance wine will install though not guaranteed.. (yet

---

### Post by cariboo on 2016-12-03
You may want to use:

```
sudo ppa-purge ppa:ondrej/php
```

to get rid of any files that were installed by trying to use the ppa, this will revert back to the packages in the regular repositories.

---

### Post by xoibsurferx on 2016-12-03
cariboo,

 I tried that command and below is the output I received. 

```

keith@Saturn1:~$ sudo ppa-purge ppa:ondrej/php
[sudo] password for keith: 
sudo: ppa-purge: command not found
keith@Saturn1:~$ 

```

I forgot I needed to install ppa-purge to do this so I installed it and below is the output. The first attempt I didn't have the ppa checked in "other software" under settings. 

```

keith@Saturn1:~$ sudo apt-get install ppa-purge
[sudo] password for keith: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  ppa-purge
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 5,704 B of archives.
After this operation, 45.1 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ trusty/universe ppa-purge all 0.2.8+bzr57 [5,704 B]
Fetched 5,704 B in 0s (18.0 kB/s)      
Selecting previously unselected package ppa-purge.
(Reading database ... 601487 files and directories currently installed.)
Preparing to unpack .../ppa-purge_0.2.8+bzr57_all.deb ...
Unpacking ppa-purge (0.2.8+bzr57) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up ppa-purge (0.2.8+bzr57) ...
keith@Saturn1:~$ sudo ppa-purge ppa:ondrej/php
Updating packages lists
PPA to be removed: ondrej php
Warning:  Could not find package list for PPA: ondrej php
keith@Saturn1:~$ sudo ppa-purge ppa:ondrej/php
Updating packages lists
W: Failed to fetch http://ppa.launchpad.net/ondrej/php5/ubuntu/dists/trusty/main/source/Sources  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/ondrej/php5/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/ondrej/php5/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.
Warning:  apt-get update failed for some reason
PPA to be removed: ondrej php
Warning:  Could not find package list for PPA: ondrej php
keith@Saturn1:~$ 

```

---

### Post by xoibsurferx on 2016-12-04
I did some digging and found out that ondrej/php5 ppa wasn't going to work anymore and was replaced with ondrej/php so I deleted the ondrej/php5 ppa from the "other software" in settings and replaced it with the new ppa ondrej/php and I also upgraded to php7. I did all of this by running the below commands. 

```

sudo apt-add-repository ppa:ondrej/php
sudo apt-get update
sudo apt-get install php7.0

```

I'm still getting errors when trying to install wine. Is there more I need to do to get rid of the old ondrej/php5 ppa besides what I did? I'm a web developer and so didn't mind upgrading to php7. I did check the version and its now php7.

---

### Post by mc4man on 2016-12-04
> I'm still getting errors when trying to install wine. 
Post them.
```
Is there more I need to do to get rid of the old ondrej/php5 ppa
```
With you removing it from your sources & the ppa itself *apparently* being deleted, hard to say.

---

### Post by xoibsurferx on 2016-12-04
Its the same error when I try to install wine. BUT good news is the sudo apt-get update and sudo apt-get upgrade are error free since changing to php PPA. 

Here's the error when install wine: 

```

keith@Saturn1:~$ sudo apt-get install wine
[sudo] password for keith: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 wine : Depends: wine1.6 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
keith@Saturn1:~$ 

```

---

### Post by mc4man on 2016-12-04
It's the same error in that apt-get tells you nothing, use aptitude. If it lists packages that won't install then try one of them specially to see why (with aptitude

---

