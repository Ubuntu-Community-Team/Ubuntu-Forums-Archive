---
title: "[SOLVED] This question will make me sound dumb."
date: 2008-01-03
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Pogeymanz on 2008-01-03
I just installed openSUSE 10.3-gnome and I have no idea how to uninstall some of the programs that came with it. Like Konqueror: it's here; I can open it and use it, but I can't find it in YaST software manager to remove it. What gives?

Also, I don't know how to add Packman repository to YaST. What do I enter for the URL? I tried looking at another thread called "To all new openSUSE users" and it said [http://packman.links2linux.org/](http://packman.links2linux.org/) but YaST doesn't accept that.

Help?

Thanks.

---

### Post by Incense on 2008-01-03
I have not used gnome in a while, but I seem to recall you being able to right click on the application while in the app browser and you'd have an option to uninstall it. I'll have to check when I have my SUSE machine in front of me. 

To add packman, open YaST2, select community repos, and just check the box next to packman, then click next or finish (whatever is showing down there). 

BTW: There are no dumb questions. That's one thing I love about the ubuntu forums. 

Cheers!

---

### Post by Pogeymanz on 2008-01-03
When I clicked community repos I get an error. "Unable to download list of repositories or no repositories defined"

---

### Post by Incense on 2008-01-03
You installed from the live CD I take it. There is a bug on that one. 

To correct do the following.

Open up the terminal  

gain root access 

```
su
```

edit the YaST control file

```
gedit /etc/YaST2/control.xml
```

find the line starting with 

```
external_sources_link
```

Changed the URL after external_sources_link to 

```
http://download.opensuse.org/YaST/Repos/openSUSE_103_Servers.xml
```

save and close. Then try to access the community repos again and you shouldn't have any problems. I'm surprised they have not fixed that one yet.

---

### Post by Pogeymanz on 2008-01-03
Awesome. That worked out well.

---

