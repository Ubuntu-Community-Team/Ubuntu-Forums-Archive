---
title: "amd64 - Compiz broke with update (again)"
date: 2006-09-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by emid on 2006-09-11
I just wanted to see if this is happening to anyone else out there with an amd64 based system.  It broke right after the last update and is still not working right now.  I haven't seen any mention of it, so if you know what's up please let me know.  Maybe I just have the wrong repos or something.  Thanks.

---

### Post by kuja on 2006-09-11
I think compiz just explained to you the meaning of the word "experimental". Just a thought.

---

### Post by emid on 2006-09-11
So I guess that means I can't ask if someone is having the same problem as me?

---

### Post by kuja on 2006-09-11
Of course you can. I'm just saying that breakage should be expected.

ps... My response to the post was likely a result of lack of sleep and boredom intermingling. Blame my cat, she stole my bed.

---

### Post by emid on 2006-09-11
No problem. I'm just trying to figure out if I inadvertently messed something up or if others have the same issue.  Since I'm running the 64bit Dapper I know I'm going to hit more bumps than usual.

---

### Post by xopher on 2006-09-11
What repository are you using? The newest compiz on the official repository is starting to get really outdated. Ive compiled compiz and put the newest ones up on my repo. Ive been getting some replies that it doesnt work (302 error), and Im looking into it. Works fine when installing manually though. Use the dpkg -i --force-depends option, should do the trick.

---

### Post by xopher on 2006-09-11
I updated the repo, it should work fine now.

```
deb http://koti.mbnet.fi/xopher/ dapper main-amd64
```

Comments appreciated.

Edit: It works.

---

### Post by blindluck48 on 2006-09-11
> **xopher said:**
> I updated the repo, it should work fine now.

```
deb http://koti.mbnet.fi/xopher/ dapper main-amd64
```

Comments appreciated.

Edit: It works.



```
Fetched 11B in 3s (3B/s)
Failed to fetch http://koti.mbnet.fi/xopher/dists/dapper/main-amd64/binary-amd64/Packages.gz  302 Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

I'm still getting a 302 error trying to retrieve the repo.

Also, when trying to install compiz/compiz-gnome I get the following error:
```
mollyj@theparthenon:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  compiz-core
The following packages have been kept back:
  compiz
The following packages will be upgraded:
  compiz-gnome
1 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/335kB of archives.
After unpacking 751kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 88145 files and directories currently installed.)
Unpacking compiz-core (from .../compiz-core_0.0.13.45-0ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-core_0.0.13.45-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite `/usr/bin/compiz', which is also in package compiz
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace compiz-gnome 0.0.2-4ubuntu2 (using .../compiz-gnome_0.0.13.45-0ubuntu1_amd64.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_0.0.13.45-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite `/usr/share/gnome/wm-properties/compiz.desktop', which is also in package compiz
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-core_0.0.13.45-0ubuntu1_amd64.deb
 /var/cache/apt/archives/compiz-gnome_0.0.13.45-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

There is another fellow with the same problem [here](http://ubuntuforums.org/showthread.php?p=1478979)

Anyone have any ideas?

---

### Post by emid on 2006-09-11
I get a 302 as well when I try to update from your repo.

---

### Post by emid on 2006-09-12
My problem is solved for now.  It turns out that I just needed to change the script in the sessions window from "/usr/bin/startcompiz %" to "/usr/bin/compiz-start %".  Anyways, thanks for the assistance guys.

emid

---

### Post by TripleE on 2006-09-13
> **xopher said:**
> I updated the repo, it should work fine now.

```
deb http://koti.mbnet.fi/xopher/ dapper main-amd64
``` 
Comments appreciated.

Edit: It works.


I am getting the same:
```
Ign http://koti.mbnet.fi dapper Release
Ign http://koti.mbnet.fi dapper/main-amd64 Packages
Err http://koti.mbnet.fi dapper/main-amd64 Packages
  302 Found
Failed to fetch http://koti.mbnet.fi/xopher/dists/dapper/main-amd64/binary-amd64/Packages.gz  302 Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

I did a google search and found this URL:
[http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html)

---

### Post by xopher on 2006-09-13
I have no idea what caused that, worked for some, and for some well.. It didnt :/ But this is solved now, Ive started uploading packages directly to quinns repos. So the official repo's are up2date again. So my repo isnt maintained anymore.

---

