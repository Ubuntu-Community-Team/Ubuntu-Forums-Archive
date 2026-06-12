---
title: "apt-get update problem"
date: 2006-03-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by DarBarf on 2006-03-01
this just started happening yesterday sometime..
i'm sorta baffled.. but i've only been using linux for about 3 or 4 months now, so it's not too surprising..

can any one tell me why i'm timing out while updating apt?

i get this:

darbarf@ubuntu:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]            
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [27.0kB]              
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [40.5kB]        
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4130B]   
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [12.3kB]         
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]     
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages [28.0kB]    
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages [1192B]   
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources [4747B]      
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy Release.gpg                            
  Could not connect to ca.archive.ubuntu.com:80 (206.75.218.52), connection timed out
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates Release.gpg
  Could not connect to ca.archive.ubuntu.com:80 (206.75.218.52), connection timed out
99% [Connecting to ca.archive.ubuntu.com (206.75.218.53)]


then it spews out some crap which i'll post later when it happens again, about how i should do apt-get update to solve this problem, when that's what i did in the first place...

and my network is up and working great... i don't get it.

thank ya
:)

---

### Post by DarBarf on 2006-03-01
so this is what i get after what i already posted..
sorry.. it takes up a lot of room.

here it is:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports Release.gpg
  Could not connect to ca.archive.ubuntu.com:80 (206.75.218.52), connection timed out
Fetched 119kB in 12m0s (165B/s)                          
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Could not connect to ca.archive.ubuntu.com:80 (206.75.218.52), connection timed out
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg)  Could not connect to ca.archive.ubuntu.com:80 (206.75.218.52), connection timed out
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg)  Could not connect to ca.archive.ubuntu.com:80 (206.75.218.52), connection timed out
Reading package lists... Done
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


i think i fudged up somewhere, but i can't think of where..
someone please help the n00b :)

---

### Post by DarBarf on 2006-03-02
ok.. so.. problem solved.. i guess... on a whim i just threw in my kubuntu cd and tried again... it worked.. i've never had to do this before though... could that be, because i just added new sources to apt?

---

### Post by amd-64 on 2006-03-03
The ubuntu repo mirror server, in this case in Canada, was down. It is nothing that you have done or added. It happens sometimes, try updating apt-get a day or two later, it usually works then.

---

### Post by jamesr on 2006-03-03
The Canadian archive failed a couple of days ago see a thread started jamesr. Sorry but I am not sure how to find a thread reference nor how to insert it. 
I solved the problem then by removing the "ca." references in the file /etc/apt/sources.list thereby going to the main archives. Since then I have re-installed a copy  of Kubuntu 5.04 which still references the canadian archives but when I try to

sudo apt-get install gparted 

errors are generated about uninstallable. It then suggests to submit a bug report to where? to whom ? at what address?

---

