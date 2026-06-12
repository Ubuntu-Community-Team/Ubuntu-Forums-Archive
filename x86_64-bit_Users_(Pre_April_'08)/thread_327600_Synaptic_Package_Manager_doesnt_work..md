---
title: "Synaptic Package Manager doesnt work."
date: 2006-12-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by stu_u2k on 2006-12-29
Hi guys & girls,

First of all i am a n00b to ubuntu so please be patient.

When i first install ubuntu x64 everything worked fine, then after updates my USB WiFi adapter stopped working, after trying everything i decided to do a reinstall & still the WiFi refused to connect for no aparent reason, my solution to this was to get a PCI WiFI adapter which did solve the problem. However on this new install i cant install any packages VIA the "apt-get" command & if i go "System->Administration->Synaptics Package Manager" the GUI fails to load.

I going to paste a few of the things i have tried & results so hopefully you can get an idea of what the problem is...

root@Storm:/# aptitude reinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
----------------------------------------------
root@Storm:/# aptitude install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
-----------------------------------------------
root@Storm:/# aptitude -R update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Translation-en_US
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Sources
Fetched 3B in 0s (4B/s)  
Reading package lists... Done

On another forum i saw in reply to an old post advice asking to check what files are in "/etc/apt" of which i dont seem to have much & certainly not the file they were on about thou it wasn't clear which distribution they were using so i am not sure if this is right, also "/var/lib/apt" & "/var/lib/aptitude" which most seem to contain only 1 file, "/var/lib/synaptic" contains none, i really don't want to reinstall again as it takes time i don't have.

I think i should also point out, when i tried to update ubuntu the GUI way it just refreshes (as if you click "Check" though it worked when i told it to update VIA command line. I had none of these issues on the first install so its really annoying.

Any advice would be great.

Thanks.

---

