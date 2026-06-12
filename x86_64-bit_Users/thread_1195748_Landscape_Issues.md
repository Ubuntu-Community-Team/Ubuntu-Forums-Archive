---
title: "Landscape Issues"
date: 2009-06-24
forum: x86 64-bit Users
---

### Post by danbriant on 2009-06-24
Basically whenever i login via SSH i am getting two landscape status reports.
 

>  
Linux WOPR 2.6.28-13-server #44-Ubuntu SMP Tue Jun 2 08:40:28 UTC 2009 x86_64
The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.
Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)
  System information as of Wed Jun 24 10:30:01 BST 2009
  System load: 0.17               Memory usage: 7%   Processes:       104
  Usage of /:  3.2% of 105.29GB   Swap usage:   0%   Users logged in: 0
  => There are 4 zombie processes.
  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)
0 packages can be updated.
0 updates are security updates.
 
Last login: Wed Jun 24 10:21:34 2009 from IP REMOVED
Linux WOPR 2.6.28-13-server #44-Ubuntu SMP Tue Jun 2 08:40:28 UTC 2009 x86_64
The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.
Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)
  System information as of Wed Jun 24 10:30:01 BST 2009
  System load: 0.17               Memory usage: 7%   Processes:       104
  Usage of /:  3.2% of 105.29GB   Swap usage:   0%   Users logged in: 0
  => There are 4 zombie processes.
  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)
0 packages can be updated.
0 updates are security updates.


 
Now idealy i only want the one to just display.
I am running a clean linux install fully updated, no other 3rd party app installs

---

### Post by michael_1234 on 2009-07-05
Hi there, 
  I just came across your post while researching what this new 'landscape' thing is when I login.  So I thought I'd post a quick reply:

The login message for the new ubuntu (commercial) "landscape" package is coming from the motd (message of the day) program; take a look at the current file,

> $ more  /etc/motd

Don't edit this file, it's updated automatically. But see if there are TWO message here, like you see when you login.. if so, then the problem is the motd file generation.  But it could also be that your .profile (or bashrc) is also generating output when a new shell is created.  

The motd file is generated from the files up in /etc/update-motd.d/, eg., here's mine,

> $ more  /etc/update-motd.d/50-landscape-sysinfo 
#!/bin/sh
echo
echo -n "  System information as of "
/bin/date
echo
/usr/bin/landscape-sysinfo


See what other programs up there might be generating this for you... 

Also, as an after-thought, make sure your .profile (or .bashrc) isn't doing a "cat /etc/motd" .  Likewise for /etc/profile or /etc/bash.bashrc.

---

