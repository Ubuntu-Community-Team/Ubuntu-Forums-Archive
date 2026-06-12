---
title: "Wine Won't install!"
date: 2013-01-23
forum: Wine
---

### Post by Hinrikz on 2013-01-23
Everytime I try to install wine or update via terminal it gives me this message.

```
hinrikz@Hinrikz:~$ sudo -s
[sudo] password for hinrikz: 
root@Hinrikz:~# sudo apt-get install wine1.5
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@Hinrikz:~# sudo apt-get install wine-gecko1.4
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

I just installed Ubuntu onto this computer and wiped the hard drive so there shouldn't be any problems any help would be widely appreciated.

---

### Post by dmallion on 2013-01-23
Some other program is using apt. Make sure you close softcentre, synaptic, etc. If you 100% sure nothing is running just delete the lock and try again

```
sudo rm -r /var/lib/dpkg/lock
```

---

### Post by Hinrikz on 2013-01-23
I tried that thing you told me but only managed to update than when I tried installing wine it said it couldnt and it needed this below but again the lock thing came :(

By the way this is the first time im properly using Ubuntu as my main operating system.

```
sudo apt-get install ttf-mscorefonts-installer
```

---

### Post by Lightning Dragon on 2013-01-23
Hello,

Did you make sure Synaptic Manager or the Software Center was not running? If you closed it off and the problem persists, try rebooting (restarting should do it) and try to install WINE through the Software Center instead of the terminal.

---

### Post by Hinrikz on 2013-01-23
Even when I try it on the store with everything closed it says

Wine Windows Program Loader
Waiting for apt-get to exit

---

### Post by Lightning Dragon on 2013-01-23
Hello,

Did you try rebooting the system and then going to Software Center before anything else?

EDIT:

Solved? What solved the issue for you? Could you please make a post or edit your main post with details on what fixed it for you? It is in case another has this issue and runs upon this thread. :)

---

### Post by Hinrikz on 2013-01-24
I thought I already made a follow up post but I was wrong well I couldn't bother with terminal anymore so I rebooted the machine from terminal tried the software center and it worked right away.

---

