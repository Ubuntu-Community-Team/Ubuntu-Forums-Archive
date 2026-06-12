---
title: "ubuntu 7.04 crash. Could not open or create file &quot;null&quot; error after logging in"
date: 2008-02-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by dayanandasaraswati on 2008-02-09
Hi friends,
   I was using ubuntu 7.04 and it was working fantastic. Today morning i was trying to install matlab when it said "unable to copy the contents of some directory to the directory TMP". It told that the problem could be due to less disk space. I had only 3GB of disk space. So i went and deleted the directory TMP and all its contents. I recreated the tmp directory. I restarted the system then. Now when i start the system it says
  
> Could not open or create file "null". Cannot create /tmp/gconf_test_locking_file_HN235T permission denied(errno=2)

I then changed the session from Gnome to Failsafe Terminal mode and deleted many of my disk contents. My disk now has 10GB free space. Now again i'm getting the same error message when trying to start. 

Help me i desparately need linux now..

---

### Post by Cappy on 2008-02-09
Try
```
sudo chmod 777 /tmp
```

/tmp has to to have full permissions for every user/group =)

---

