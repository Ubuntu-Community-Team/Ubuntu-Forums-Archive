---
title: "error messages in package manager"
date: 2006-01-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by crhooker on 2006-01-14
My package manager seems to be a bit messy and I get the following whenever I start it or go to add packages. I can add the ones I want - at least I think so, but I am not sure what all this means. I am sure it is a setup thing in settings but not sure how to resolve it. So if someone could please tell me what all this means AND how to fix it I would be grateful!

Thanks,

carl

W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)

---

### Post by ice60 on 2006-01-14
i have the same problem. all i do to fix it for a day or so is reload it in synaptic or do this in terminal
```
sudo apt-get update
```
but the error comes back again within about 24/48 hours :( 
[http://ubuntuforums.org/showthread.php?t=110844](http://ubuntuforums.org/showthread.php?t=110844)

can you think of anything you might have done to cause it? the only thing i can think of is i manually cleared a directory, although i can't remember which one lol

---

### Post by crhooker on 2006-01-14
I cannot think of anything I did, I did try to turn on the various other areas in the settings tab but it seems to me the errors have been there since I did the install last week.

---

### Post by ice60 on 2006-01-17
hi, are you in the same kind of loop i described [here](http://ubuntuforums.org/showpost.php?p=650614&postcount=6)? i just wanted to check we have the same problem.

at the moment i am error free, however, the time before last when i updated i used synaptic, i selected the option to "show progress of single files" which showed afew of the servers failed. i'm a linux novice but i think the two things it could be are some kind of network error or where all the information which the source lists downloads is kept is being cleared out somehow.

---

### Post by FluffyElmo on 2006-01-17
You may have added a repository to Synaptic that is no longer available. Try commenting out the lines relating to [http://antesis.freecontrib.org](http://antesis.freecontrib.org) in your sources list and then do an *apt-get update* to fix it.

```
sudo gedit /etc/apt/sources.list
```

You may prefer to go to *Settings->Repositories* in Synaptic and remove them from there followed by a refresh.

---

