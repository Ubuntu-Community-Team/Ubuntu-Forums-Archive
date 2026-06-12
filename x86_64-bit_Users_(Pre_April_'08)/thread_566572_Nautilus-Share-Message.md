---
title: "Nautilus-Share-Message"
date: 2007-10-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by misterfixit on 2007-10-03
When reviewing my /root/.xsesson-errors log I see the following many times:

Nautilus-Share-Message:  Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: usershares are currently disabled.

This ubuntu box is a stand-alone machine and is not connected to a net, SMB or otherwise.

Ideas?

---

### Post by Damiox on 2008-06-13
i have the same problem on fully updated ubuntu studio originally gutsy then hardy  here is the whole thing......
```
damiox@Home-Ubuntu-Main:~$ sudo nautilus
seahorse nautilus module initialized
Initializing nautilus-image-converter extension
Initializing nautilus-share extension

** (nautilus:18315): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


--- Hash table keys for warning below:
--> file:///

(nautilus:18315): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:18315): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
Shutting down nautilus-image-converter extension
seahorse nautilus module shutdown

```

of course the shut down code is when i close nautilus......it continues to run that code every time i change folders

---

### Post by RavanH on 2008-07-03
Try and install Samba ```
sudo apt-get install samba smbfs
``` and the messages will probably be gone (as on my system) ... 

You might find samba usefull to share folders with any windows system on your home network, if you have any M$ needs left ;) 

Find documentation on how to configure and use samba anywhere on the internet but a good place to start is [http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/)

Cheers!
--ravan

---

