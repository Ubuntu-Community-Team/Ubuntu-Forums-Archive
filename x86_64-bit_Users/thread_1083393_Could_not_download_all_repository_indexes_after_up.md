---
title: "Could not download all repository indexes after upgrade from 8.04 to 8.10"
date: 2009-02-28
forum: x86 64-bit Users
---

### Post by par129 on 2009-02-28
I've seen a few of these floating around but with different error message following. I've been recieving this when I attempt to manually update through the Update manager. It's been happening after I upgraded from 8.04 to 8.10. The upgrade was by downloading from the server or whatever. Updates we're installed when available but on occasion the update icon will show up in the top bar saying something is outdated and I manually run the update to receive the following message:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

"GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7Failed to fetch cdrom:[Ubuntu 8.04.2 _Hardy Heron_ - Release amd64 (20090121)]/dists/hardy/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Failed to fetch cdrom:[Ubuntu 8.04.2 _Hardy Heron_ - Release amd64 (20090121)]/dists/hardy/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Some index files failed to download, they have been ignored, or old ones used instead."

I'm not exactly sure what it means but any help on a fix would be much appreciated!!!

---

### Post by arm-c on 2009-02-28
You have some PPA or repositories listed that either are no longer valid or their keys have expired.

I just went through that and removed a few that were outdated.  As I recall for me it was:  Gnome Do, Avant, and Deluge that were the culprits.  Try unchecking first and see if it makes the error go away.  Once you have found the right combination... you know what is either temporarily unavailable or is no longer valid.  I just removed them after I figured it out.

---

### Post by par129 on 2009-03-01
Thanks for the post, I apologize for not putting I am new to Ubuntu, and do not know off the top of my head what PPA or how to do what you said. It sounds to me like you did a process of elimination in the package manager. I hope I'm wrong cause theres alot of stuff in there. thanks again

---

### Post by forger on 2009-03-02
[thread=1056099]**Update your Launchpad PPA repositories and apt keys**[/thread]

---

### Post by forger on 2009-03-02
For the cdrom error, you have to disable the deb line for cdrom by editing:
```
gksu gedit /etc/apt/sources.list
```

---

### Post by sahabcse on 2009-03-02
Hi


It is not a big issue. Comment out CDROM line in "cdrom:[Ubuntu 8.04.2 _Hardy Heron_" in /etc/apt/sources.list or open synaptic manager >>>repositories>>>Third party software and uncheck the added CDrom.

---

