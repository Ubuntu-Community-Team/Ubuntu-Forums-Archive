---
title: "Sytem lock up with &quot;ADD/REMOVE&quot; from the menu!"
date: 2009-08-28
forum: x86 64-bit Users
---

### Post by dBuster on 2009-08-28
Has anyone else experienced this?  When you click on Applications and go to Add/Remove and try to bring that up it just totally locks your system up.  I can move the mouse but that is it.

Could it be something to do with compiz features that may be running?  

Any ideas???  Been struggling with this for 2 months to no avail.  Oh and this is Jaunty 9.04 64 bit

---

### Post by garvinrick4 on 2009-08-29
Had problem for a while but bug was fixed a while back. 
sudo apt-get remove gnome-app-install
sudo apt-get clean
sudo apt-get install gnome-app-install

That should give you fresh install from repositorys and not App cached
that is before fix. 

sudo apt-get update
sudo apt-get dist-upgrade

Would not hurt either.

---

### Post by dBuster on 2009-08-29
Tried that and still same thing, locks up hard and the only thing I can do is move the mouse.  Even waited 5 minutes to see if anything would return to me.  Nope...

Still same lock up hard issue...  Anyone else ideas??

---

### Post by P.KO on 2009-08-29
Hi

Try to run this '/usr/bin/gnome-app-install' from the terminal and post the out put here.

Mine is looking like this and works:

> ** (gnome-app-install:10911): WARNING **: return value of custom widget handler was not a GtkWidget
/usr/lib/python2.6/dist-packages/AppInstall/AppInstall.py:1285: GtkWarning: gtk_tree_model_sort_sort: assertion `tree_model_sort->default_sort_func != NULL' failed
  item.applications.set_default_sort_func(None)
/usr/lib/python2.6/dist-packages/AppInstall/AppInstall.py:1295: GtkWarning: gtk_tree_model_sort_set_sort_column_id: assertion `tree_model_sort->default_sort_func != NULL' failed
  item.applications.set_sort_column_id(-1, sort_type)


---

### Post by dBuster on 2009-08-29
> **P.KO said:**
> Hi

Try to run this '/usr/bin/gnome-app-install' from the terminal and post the out put here.

Mine is looking like this and works:

Alrighty, after a power down and boot sequence again!  This is the output of that command as it locked up my system..

** (gnome-app-install:5464):WARNING **:return value of custom widget handler was not a GtkWidget

Had to write that down to be able to post.  I think I might break out the digital camera to take a photo of the results when I try to run add/remove...

---

### Post by P.KO on 2009-08-29
Hi,

That didn't give much info.

[LIST=1]Are you sure your system is up-to-date?
Can you install using Synaptic?
Can you install an application from terminal?
[/LIST]

To remove deprecated packages
```
sudo apt-get autoremove
```

To update your system

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by dBuster on 2009-08-29
> **P.KO said:**
> Hi,

That didn't give much info.

[LIST=1]Are you sure your system is up-to-date?
Can you install using Synaptic?
Can you install an application from terminal?
[/LIST]

To remove deprecated packages
```
sudo apt-get autoremove
```

To update your system

```
sudo apt-get update && sudo apt-get upgrade
```


No kidding it didn't give me much...

I ran those commands and this is the output

```
david@david-laptop:~$ sudo apt-get autoremove
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ia32-libs-chromium-browser
The following packages will be REMOVED:
  ia32-libs-chromium-browser
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 32.8kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 378881 files and directories currently installed.)
Removing ia32-libs-chromium-browser ...
david@david-laptop:~$ 
david@david-laptop:~$ 
david@david-laptop:~$ sudo apt-get update && sudo apt-get upgrade
Get:1 http://dl.google.com stable Release.gpg [191B]
Hit http://security.ubuntu.com jaunty-security Release.gpg                     
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US          
Ign http://dl.google.com stable/non-free Translation-en_US                     
Hit http://us.archive.ubuntu.com jaunty Release.gpg                            
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US                 
Hit http://packages.medibuntu.org jaunty Release.gpg                           
Ign http://packages.medibuntu.org jaunty/free Translation-en_US                
Get:2 http://dl.google.com stable Release [1310B]                              
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US    
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US      
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US    
Hit http://security.ubuntu.com jaunty-security Release                         
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US             
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US           
Hit http://us.archive.ubuntu.com jaunty-updates Release.gpg                    
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US     
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US   
Hit http://us.archive.ubuntu.com jaunty-backports Release.gpg                  
Ign http://us.archive.ubuntu.com jaunty-backports/restricted Translation-en_US 
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_US            
Hit http://packages.medibuntu.org jaunty Release                               
Get:3 http://dl.google.com stable/non-free Packages [966B]                     
Ign http://us.archive.ubuntu.com jaunty-backports/main Translation-en_US       
Hit http://wine.budgetdedicated.com jaunty Release.gpg                         
Ign http://wine.budgetdedicated.com jaunty/main Translation-en_US              
Ign http://us.archive.ubuntu.com jaunty-backports/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com jaunty-backports/universe Translation-en_US   
Hit http://us.archive.ubuntu.com jaunty Release                                
Hit http://us.archive.ubuntu.com jaunty-updates Release                        
Hit http://security.ubuntu.com jaunty-security/main Packages                   
Hit http://packages.medibuntu.org jaunty/free Packages                         
Hit http://wine.budgetdedicated.com jaunty Release                             
Hit http://us.archive.ubuntu.com jaunty-backports Release                      
Hit http://security.ubuntu.com jaunty-security/restricted Packages             
Hit http://security.ubuntu.com jaunty-security/restricted Sources              
Hit http://security.ubuntu.com jaunty-security/main Sources                    
Hit http://security.ubuntu.com jaunty-security/multiverse Sources              
Hit http://us.archive.ubuntu.com jaunty/main Packages                          
Hit http://us.archive.ubuntu.com jaunty/restricted Packages                    
Hit http://us.archive.ubuntu.com jaunty/restricted Sources                     
Hit http://us.archive.ubuntu.com jaunty/main Sources                           
Hit http://us.archive.ubuntu.com jaunty/multiverse Sources                     
Hit http://us.archive.ubuntu.com jaunty/universe Sources                       
Hit http://security.ubuntu.com jaunty-security/universe Sources                
Hit http://security.ubuntu.com jaunty-security/universe Packages               
Hit http://security.ubuntu.com jaunty-security/multiverse Packages             
Ign http://wine.budgetdedicated.com jaunty/main Packages                       
Hit http://us.archive.ubuntu.com jaunty/universe Packages                      
Hit http://us.archive.ubuntu.com jaunty/multiverse Packages                    
Hit http://us.archive.ubuntu.com jaunty-updates/main Packages                  
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Packages            
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Sources             
Hit http://wine.budgetdedicated.com jaunty/main Packages                       
Hit http://us.archive.ubuntu.com jaunty-updates/main Sources                   
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Sources             
Hit http://us.archive.ubuntu.com jaunty-updates/universe Sources               
Hit http://us.archive.ubuntu.com jaunty-updates/universe Packages              
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Packages            
Hit http://us.archive.ubuntu.com jaunty-backports/main Sources                 
Hit http://us.archive.ubuntu.com jaunty-backports/restricted Sources           
Hit http://us.archive.ubuntu.com jaunty-backports/universe Sources             
Hit http://us.archive.ubuntu.com jaunty-backports/multiverse Sources           
Hit http://us.archive.ubuntu.com jaunty-backports/restricted Packages          
Hit http://us.archive.ubuntu.com jaunty-backports/main Packages                
Hit http://us.archive.ubuntu.com jaunty-backports/multiverse Packages          
Hit http://us.archive.ubuntu.com jaunty-backports/universe Packages            
Hit http://packages.medibuntu.org jaunty/non-free Packages                     
Hit http://archive.canonical.com jaunty Release.gpg                            
Ign http://archive.canonical.com jaunty/partner Translation-en_US
Hit http://ppa.launchpad.net jaunty Release.gpg
Ign http://ppa.launchpad.net jaunty/main Translation-en_US
Hit http://archive.canonical.com jaunty Release
Hit http://ppa.launchpad.net jaunty Release.gpg
Ign http://ppa.launchpad.net jaunty/main Translation-en_US
Hit http://ppa.launchpad.net jaunty Release.gpg
Ign http://ppa.launchpad.net jaunty/main Translation-en_US
Hit http://ppa.launchpad.net jaunty Release    
Hit http://archive.canonical.com jaunty/partner Packages            
Hit http://ppa.launchpad.net jaunty Release    
Hit http://ppa.launchpad.net jaunty Release                         
Hit http://archive.canonical.com jaunty/partner Sources             
Ign http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Packages
Fetched 2467B in 3s (806B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
david@david-laptop:~$ 

```

Not sure what is going on but I am up to date and I can install using Synaptic package manager just not the add/remove.  However there are times when you would need the add/remove to make things easier for install such as the oo3.1 upgrade...  The instructions I have call for one to finish off with the add/remove to make sure the install was complete.  Using synaptic I have to tell each one to reinstall.

---

### Post by dBuster on 2009-09-06
Anyone ideas???

Would really like this fixed...

---

