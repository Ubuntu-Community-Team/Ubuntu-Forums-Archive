---
title: "repositorys  not updating. 8.10"
date: 2008-11-01
forum: x86 64-bit Users
---

### Post by nutpants on 2008-11-01
i added some repositorys to my new install of 8.10
for synce and conduit 


deb [http://ppa.launchpad.net/conduit/ubuntu](http://ppa.launchpad.net/conduit/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/conduit/ubuntu](http://ppa.launchpad.net/conduit/ubuntu) hardy main
(there is nothing built for intrepid but the hardy ones dont even show up)
and 

deb [http://ppa.launchpad.net/synce/ubuntu](http://ppa.launchpad.net/synce/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/synce/ubuntu](http://ppa.launchpad.net/synce/ubuntu) intrepid main


and try as i might they fail on updating my packages ( ie reload is snapanic)

what am i doing wrong
i have checked the web sites and there is information there..
but i cant seem to get it to work..

nutz

---

### Post by Yellow Pasque on 2008-11-01
The latest versions of both of those programs are available in the standard 8.10 64-bit repos. Is there a reason you want to add different repos for older versions?

---

### Post by nutpants on 2008-11-02
they dont show up on my synaptic..

so i added the repos that were to have them.

and they still dont show up..

as i said its wierd 
as a newbie i added the repos as i thought they were not officially supported.

nutz

---

### Post by Mouth on 2008-11-02
1. Remove the 2 ppa repo's you had in your first post
2. Open Software Sources and ensure teh universe repo is selected.
3. Run a Software Sources update

4. Install conduit, synce-sync-engine, synce-gnomevfs, synce-hal, and synce-trayicon (Eg. "sudo apt-get install synce-sync-engine, synce-gnomevfs, synce-hal, and synce-trayicon")

Refer [http://packages.ubuntu.com/search?suite=intrepid&searchon=names&keywords=synce](http://packages.ubuntu.com/search?suite=intrepid&searchon=names&keywords=synce)

---

