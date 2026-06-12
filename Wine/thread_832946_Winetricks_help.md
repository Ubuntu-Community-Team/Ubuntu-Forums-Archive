---
title: "Winetricks help"
date: 2008-06-18
forum: Wine
---

### Post by NiksaVel on 2008-06-18
Hi,

I'm having a problem using winetricks...   I've made a clean install of gutsy and have the latest wine installed from the winehq repos...

I have winetricks installed and can start it, but when I try to install anything I get the following:

```
niksavel@darth:~$ ./winetricks
Executing wget -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate http://internap.dl.sourceforge.net/sourceforge/corefonts/arial32.exe
--12:40:04--  http://internap.dl.sourceforge.net/sourceforge/corefonts/arial32.exe
           => `arial32.exe'
Resolving internap.dl.sourceforge.net... 70.42.27.131
Connecting to internap.dl.sourceforge.net|70.42.27.131|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 554,208 (541K) [application/octet-stream]
arial32.exe: Permission denied

Cannot write to `arial32.exe' (Permission denied).
Note: command 'wget -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate http://internap.dl.sourceforge.net/sourceforge/corefonts/arial32.exe' returned status 1.  Aborting.
niksavel@darth:~$                       
```

If I try to run 
```
wget -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate http://internap.dl.sourceforge.net/sourceforge/corefonts/arial32.exe
```

manually than it works normally...   it's some kind of a permissions issue.  I was under the impression that I was supposed to run winetricks as a user, not with sudo...   in fact if I try to run it with sudo than the download works but it fails at install saying that I'm not the owner of the directory...   the owner is me (niksavel) and not root...  so I should have permissions...

I've tried deleting the entire .wine and reinstalling everything to make sure I didn't mess up any directories but it's always the same...   for some reason I couldn't find anyone else having this issue....  

help pls...

---

### Post by tehownt on 2008-10-12
Hi,

I had the same problem and found the solution.

It's only because instead of running winetricks in usermode first, you did it in sudo (root) hence before telling you that you weren't the owner of .wine all the temporarily created folders are now owned by root.

At the beginning of the script you can see that 2 folders are created:
~/.wine/drive_c/winetrickstmp/ (or drive_<whatever>
~/.winetrickscache/  or ~/winetrickscache

All the .exe fonts will be downloaded into the "cache" folder, check its access permission, mine was owned by root, hence the "Acces Denied" message when using wget.

Let your user re-take ownership of those directories and everything should run fine.

The problem is that the output of the winetricks script lacks the destination of the downloaded .exe files.

---

### Post by david_kt on 2008-10-12
> **NiksaVel said:**
> 

I've tried deleting the entire .wine and reinstalling everything to make sure I didn't mess up any directories but it's always the same...   for some reason I couldn't find anyone else having this issue....  

help pls...

Open terminal and run:

```
sudo rm -rf .winetrickscache
```

And then try to run winetricks again as normal user.

DK

---

### Post by admiraljkb on 2010-09-25
I just ran into this again in Maverick 10.10, and stumbled into this admittedly old thread via Google.  The solution below for the older version was the hint I needed to fix the issue for the Maverick.  Thanks!  After poking through the winetricks script, I noticed the cache location changed though.  Once accomodated that - it works again:

```
sudo chown -R *userid:userid* ~/.wine/drive_c/winetrickstmp/
sudo chown -R *userid:userid* ~/.cache/winetricks
```



> **tehownt said:**
> Hi,

I had the same problem and found the solution.

It's only because instead of running winetricks in usermode first, you did it in sudo (root) hence before telling you that you weren't the owner of .wine all the temporarily created folders are now owned by root.

At the beginning of the script you can see that 2 folders are created:
~/.wine/drive_c/winetrickstmp/ (or drive_<whatever>
~/.winetrickscache/  or ~/winetrickscache

All the .exe fonts will be downloaded into the "cache" folder, check its access permission, mine was owned by root, hence the "Acces Denied" message when using wget.

Let your user re-take ownership of those directories and everything should run fine.

The problem is that the output of the winetricks script lacks the destination of the downloaded .exe files.

---

### Post by Lefke123 on 2010-10-27
> **admiraljkb said:**
> I just ran into this again in Maverick 10.10, and stumbled into this admittedly old thread via Google.  The solution below for the older version was the hint I needed to fix the issue for the Maverick.  Thanks!  After poking through the winetricks script, I noticed the cache location changed though.  Once accomodated that - it works again:

```
sudo chown -R *userid:userid* ~/.wine/drive_c/winetrickstmp/
sudo chown -R *userid:userid* ~/.cache/winetricks
```

Thanks a lot! Was first on top of Google for me too; your solution fixed it for me. :)

---

