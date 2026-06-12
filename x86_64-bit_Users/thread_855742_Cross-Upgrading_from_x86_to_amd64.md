---
title: "Cross-Upgrading from x86 to amd64 ?"
date: 2008-07-10
forum: x86 64-bit Users
---

### Post by hadmut on 2008-07-10
Hi, 

I have a running ubuntu x86 system which formerly had an old and slow mainboard. 

I replaced the mainboard with a new one with an AMD X2 CPU and 4GB RAM, but am still running the same software, i.e. x86 . 


Is there any way to automatically upgrade a given system from x86 to amd64 whithout a complete reinstallation and reconfiguration?


Are there any known issues where x86 packages are incompatible with their amd64 counterparts? E.g. do mysql and ldap servers work with the database files written with the x86 version?

regards
Hadmut

---

### Post by ch_123 on 2008-07-10
No, to go from 32 to 64, or vice versa, a complete reinstall is needed. Im not sure about the second part of your query. In theory there should be no problem, but there might be certain software specific issues.

---

### Post by ouilsen on 2008-07-10
Hello,

First off, I think there is no way around reinstalling Ubuntu. But there is an easy way. At least it worked for me.

Only binaries and libraries are incompatible between x86 and x86_64, so only those need to be replaced. 

Here's what I did:


1. Backed up my /home folder. Maybe you need other files like your log files in /var/log. In general you don't.

```
sudo rsync -r -t -p -o -g -v --progress /home /media/WHATEVERBACKUPDRIVE/home

```
Then put your installed packages list on an external drive.

```
 sudo dpkg --get-selections > /media/backup/installed_packages
```

2. Reinstall Ubuntu.

3. Install all the former packages: 
```

sudo apt-get dselect
sudo dpkg --set-selections < installed_packages
sudo dselect

```
4. Recover /home

```
sudo rsync -r -t -p -o -g -v --progress /media/WHATEVERBACKUPDRIVE/home /home
```


Most config files should also be recovered, like the ones of Pidgin, bookmarks, mails... Only changes you made manually in /etc need to be set again. You may also take a risk and backup /etc the same way as /home. 

Keep in mind that you should do this only with the exact same version. And there may be some packages which are unavailable for x86_64. Also the sources of synaptic need to be the same in case you added some third party ones.

Edit: The usernames must stay the same to stay out of right conflicts. I only had one account. If you have multiple accounts you may have some difficulties. Is this case?

---

