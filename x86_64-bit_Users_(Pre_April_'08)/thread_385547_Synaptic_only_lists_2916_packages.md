---
title: "Synaptic only lists 2916 packages"
date: 2007-03-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by patslap on 2007-03-15
I seem to be having problems accessing all repositories. Synaptic only lists 2916 available packages, but it should list 19,000 or so.

I can;t seem to find a fix for this. Does anyone have any ideas how I can fix this?

Thanks

---

### Post by kerry_s on 2007-03-15
Do you got all the repos turned on? also there might not be that many 64bit packages.

---

### Post by patslap on 2007-03-15
All repos are turned on. And I believe that there should be around 19000 64-bit packages in total.

---

### Post by kerry_s on 2007-03-15
Can you post your sources.list?

gedit /etc/apt/sources.list

---

### Post by patslap on 2007-03-16
Here is my sources list:
```
deb http://archive.canonical.com/ubuntu dapper-commercial main 
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu Dapper main restricted 
deb-src http://archive.ubuntu.com/ubuntu Dapper main restricted 

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu Dapper-updates main restricted 
deb-src http://archive.ubuntu.com/ubuntu Dapper-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu Dapper universe 
deb-src http://archive.ubuntu.com/ubuntu Dapper universe 

deb http://security.ubuntu.com/ubuntu Dapper-security main restricted 
deb-src http://security.ubuntu.com/ubuntu Dapper-security main restricted 

deb http://security.ubuntu.com/ubuntu Dapper-security universe 
deb-src http://security.ubuntu.com/ubuntu Dapper-security universe 

deb http://archive.ubuntu.com/ubuntu Dapper multiverse 
deb-src http://archive.ubuntu.com/ubuntu Dapper multiverse 

deb http://archive.ubuntu.com/ubuntu Dapper-backports main restricted universe multiverse 

deb http://archive.canonical.com/ubuntu Dapper-commercial main 

deb http://packages.freecontrib.org/plf/ Dapper free non-free 
deb-src http://packages.freecontrib.org/plf/ Dapper free non-free
```

---

### Post by kerry_s on 2007-03-16
So strange, you should have heck of alot more app's.
Have you clicked the reload button?
Do you get any repo errors?

I'm on feisty and it shows 21471 packages. So there must be something wrong.

I cleaned up your sources.list, try renaming yours to sources.list.old and make a new 1 with this->

```

deb http://archive.ubuntu.com/ubuntu Dapper main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu Dapper main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu Dapper-updates main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu Dapper-updates main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu Dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu Dapper-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu Dapper-backports main restricted universe multiverse 

deb http://packages.freecontrib.org/plf/ Dapper free non-free 
deb-src http://packages.freecontrib.org/plf/ Dapper free non-free
deb http://archive.canonical.com/ubuntu dapper-commercial main 
deb http://archive.canonical.com/ubuntu Dapper-commercial main 

```

---

### Post by patslap on 2007-03-16
ok - I backed up my sources.list and replaced it with the sources.list you posted. Now all that happens when i click 'reload' is that a pop-up window appears and says 'Downloading Package Information' and gets to 27 of 52 files, pauses for about 3 minutes then says 'Could not download all packages' and something about something may be broken. Output looks like this:
```
http://security.ubuntu.com/ubuntu/dists/Dapper-security/Release.gpg: Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out
http://packages.freecontrib.org/plf/dists/Dapper/Release.gpg: Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg: Could not connect to archive.canonical.com:80 (82.211.81.142), connection timed out
http://archive.canonical.com/ubuntu/dists/Dapper-commercial/Release.gpg: Could not connect to archive.canonical.com:80 (82.211.81.142), connection timed out
http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg: Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out
http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg: Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10), connection timed out
http://archive.ubuntu.com/ubuntu/dists/Dapper/main/binary-amd64/Packages.gz: 404 Not Found [IP: 91.189.89.6 80]
http://archive.ubuntu.com/ubuntu/dists/Dapper/restricted/binary-amd64/Packages.gz: 404 Not Found [IP: 91.189.89.6 80]
http://archive.ubuntu.com/ubuntu/dists/Dapper/universe/binary-amd64/Packages.gz: 404 Not Found [IP: 91.189.89.6 80]
http://archive.ubuntu.com/ubuntu/dists/Dapper/multiverse/binary-amd64/Packages.gz: 404 Not Found [IP: 91.189.89.6 80]
http://archive.ubuntu.com/ubuntu/dists/Dapper/main/source/Sources.gz: 404 Not Found [IP: 91.189.89.6 80]
http://archive.ubuntu.com/ubuntu/dists/Dapper/restricted/source/Sources.gz: 404 Not Found [IP: 91.189.89.6 80]
http://archive.ubuntu.com/ubuntu/dists/Dapper/universe/source/Sources.gz: 404 Not Found [IP: 91.189.89.6 80]
http://archive.ubuntu.com/ubuntu/dists/Dapper/multiverse/source/Sources.gz: 404 Not Found [IP: 91.189.89.6 80]
http://archive.ubuntu.com/ubuntu/dists/Dapper-updates/main/binary-amd64/Packages.gz: 404 Not Found [IP: 91.189.89.6 80]
http://archive.ubuntu.com/ubuntu/dists/Dapper-updates/restricted/binary-amd64/Packages.gz: 404 Not Found [IP: 91.189.89.6 80]
http://archive.ubuntu.com/ubuntu/dists/Dapper-updates/universe/binary-amd64/Packages.gz: 404 Not Found [IP: 91.189.89.6 80]
http://archive.ubuntu.com/ubuntu/dists/Dapper-updates/multiverse/binary-amd64/Packages.gz: 404 Not Found [IP: 91.189.89.6 80]
http://archive.ubuntu.com/ubuntu/dists/Dapper-updates/main/source/Sources.gz: 404 Not Found [IP: 91.189.89.6 80]
http://archive.ubuntu.com/ubuntu/dists/Dapper-updates/restricted/source/Sources.gz: 404 Not Found [IP: 91.189.89.6 80]
http://archive.ubuntu.com/ubuntu/dists/Dapper-updates/universe/source/Sources.gz: 404 Not Found [IP: 91.189.89.6 80]
http://archive.ubuntu.com/ubuntu/dists/Dapper-updates/multiverse/source/Sources.gz: 404 Not Found [IP: 91.189.89.6 80]
http://archive.ubuntu.com/ubuntu/dists/Dapper-backports/main/binary-amd64/Packages.gz: 404 Not Found [IP: 91.189.89.6 80]
http://archive.ubuntu.com/ubuntu/dists/Dapper-backports/restricted/binary-amd64/Packages.gz: 404 Not Found [IP: 91.189.89.6 80]
http://archive.ubuntu.com/ubuntu/dists/Dapper-backports/universe/binary-amd64/Packages.gz: 404 Not Found [IP: 91.189.89.6 80]
http://archive.ubuntu.com/ubuntu/dists/Dapper-backports/multiverse/binary-amd64/Packages.gz: 404 Not Found [IP: 91.189.89.6 80]
```


I've posted a screenshot below.

What is happening here? My internet connection appears to be fine as I can browse web, email, use skype etc.

I wonder if it is because I'm using AMD64 Kubuntu 6.06. Would this make a difference to how respositories work?

Thanks for your help so far.

---

### Post by kerry_s on 2007-03-16
It's saying the amd64 don't exist and the rest are just timing out, meaning the server is taking to long to respond.

Let's try changing to different repositores. Add a "us." to all the archive
Example:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) Dapper main restricted universe multiverse 
to
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) Dapper main restricted universe multiverse

---

### Post by patslap on 2007-03-16
ok - changed to 'us' and didn't work. Here is the code output:

```
http://us.security.ubuntu.com/ubuntu/dists/Dapper-security/Release.gpg: Could not resolve ‘us.security.ubuntu.com’
http://us.packages.freecontrib.org/plf/dists/Dapper/Release.gpg: Could not resolve ‘us.packages.freecontrib.org’
http://us.archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg: Could not resolve ‘us.archive.canonical.com’
http://us.archive.canonical.com/ubuntu/dists/Dapper-commercial/Release.gpg: Could not resolve ‘us.archive.canonical.com’
http://us.packages.freecontrib.org/plf/dists/Dapper/free/binary-amd64/Packages.gz: Could not resolve ‘us.packages.freecontrib.org’
http://us.packages.freecontrib.org/plf/dists/Dapper/non-free/binary-amd64/Packages.gz: Could not resolve ‘us.packages.freecontrib.org’
http://us.archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-amd64/Packages.gz: Could not resolve ‘us.archive.canonical.com’
http://us.packages.freecontrib.org/plf/dists/Dapper/free/source/Sources.gz: Could not resolve ‘us.packages.freecontrib.org’
http://us.archive.canonical.com/ubuntu/dists/Dapper-commercial/main/binary-amd64/Packages.gz: Could not resolve ‘us.archive.canonical.com’
http://us.packages.freecontrib.org/plf/dists/Dapper/non-free/source/Sources.gz: Could not resolve ‘us.packages.freecontrib.org’
http://us.security.ubuntu.com/ubuntu/dists/Dapper-security/main/binary-amd64/Packages.gz: Could not resolve ‘us.security.ubuntu.com’
http://us.security.ubuntu.com/ubuntu/dists/Dapper-security/restricted/binary-amd64/Packages.gz: Could not resolve ‘us.security.ubuntu.com’
http://us.security.ubuntu.com/ubuntu/dists/Dapper-security/universe/binary-amd64/Packages.gz: Could not resolve ‘us.security.ubuntu.com’
http://us.security.ubuntu.com/ubuntu/dists/Dapper-security/multiverse/binary-amd64/Packages.gz: Could not resolve ‘us.security.ubuntu.com’
http://us.security.ubuntu.com/ubuntu/dists/Dapper-security/main/source/Sources.gz: Could not resolve ‘us.security.ubuntu.com’
http://us.security.ubuntu.com/ubuntu/dists/Dapper-security/restricted/source/Sources.gz: Could not resolve ‘us.security.ubuntu.com’
http://us.security.ubuntu.com/ubuntu/dists/Dapper-security/universe/source/Sources.gz: Could not resolve ‘us.security.ubuntu.com’
http://us.security.ubuntu.com/ubuntu/dists/Dapper-security/multiverse/source/Sources.gz: Could not resolve ‘us.security.ubuntu.com’
http://us.archive.ubuntu.com/ubuntu/dists/Dapper/main/binary-amd64/Packages.gz: 404 Not Found [IP: 91.189.89.8 80]
http://us.archive.ubuntu.com/ubuntu/dists/Dapper/restricted/binary-amd64/Packages.gz: 404 Not Found [IP: 91.189.89.8 80]
http://us.archive.ubuntu.com/ubuntu/dists/Dapper/universe/binary-amd64/Packages.gz: 404 Not Found [IP: 91.189.89.8 80]
http://us.archive.ubuntu.com/ubuntu/dists/Dapper/multiverse/binary-amd64/Packages.gz: 404 Not Found [IP: 91.189.89.8 80]
http://us.archive.ubuntu.com/ubuntu/dists/Dapper/main/source/Sources.gz: 404 Not Found [IP: 91.189.89.8 80]
http://us.archive.ubuntu.com/ubuntu/dists/Dapper/restricted/source/Sources.gz: 404 Not Found [IP: 91.189.89.8 80]
http://us.archive.ubuntu.com/ubuntu/dists/Dapper/universe/source/Sources.gz: 404 Not Found [IP: 91.189.89.8 80]
http://us.archive.ubuntu.com/ubuntu/dists/Dapper/multiverse/source/Sources.gz: 404 Not Found [IP: 91.189.89.8 80]
http://us.archive.ubuntu.com/ubuntu/dists/Dapper-updates/main/binary-amd64/Packages.gz: 404 Not Found [IP: 91.189.89.8 80]
http://us.archive.ubuntu.com/ubuntu/dists/Dapper-updates/restricted/binary-amd64/Packages.gz: 404 Not Found [IP: 91.189.89.8 80]
http://us.archive.ubuntu.com/ubuntu/dists/Dapper-updates/universe/binary-amd64/Packages.gz: 404 Not Found [IP: 91.189.89.8 80]
http://us.archive.ubuntu.com/ubuntu/dists/Dapper-updates/multiverse/binary-amd64/Packages.gz: 404 Not Found [IP: 91.189.89.8 80]
http://us.archive.ubuntu.com/ubuntu/dists/Dapper-updates/main/source/Sources.gz: 404 Not Found [IP: 91.189.89.8 80]
http://us.archive.ubuntu.com/ubuntu/dists/Dapper-updates/restricted/source/Sources.gz: 404 Not Found [IP: 91.189.89.8 80]
http://us.archive.ubuntu.com/ubuntu/dists/Dapper-updates/universe/source/Sources.gz: 404 Not Found [IP: 91.189.89.8 80]
http://us.archive.ubuntu.com/ubuntu/dists/Dapper-updates/multiverse/source/Sources.gz: 404 Not Found [IP: 91.189.89.8 80]
http://us.archive.ubuntu.com/ubuntu/dists/Dapper-backports/main/binary-amd64/Packages.gz: 404 Not Found [IP: 91.189.89.8 80]
http://us.archive.ubuntu.com/ubuntu/dists/Dapper-backports/restricted/binary-amd64/Packages.gz: 404 Not Found [IP: 91.189.89.8 80]
http://us.archive.ubuntu.com/ubuntu/dists/Dapper-backports/universe/binary-amd64/Packages.gz: 404 Not Found [IP: 91.189.89.8 80]
http://us.archive.ubuntu.com/ubuntu/dists/Dapper-backports/multiverse/binary-amd64/Packages.gz: 404 Not Found [IP: 91.189.89.8 80]

```

---

### Post by kerry_s on 2007-03-17
Okay, i'm all out of ideas. I have no experience with the 64version.

I suggest you start a new thread but pick a better title so you can get help from 64bit users. Something like "AMD-64bit repositories not working".

Sorry, i got to bail on this one, I have zero experience with 64bit installs.

---

### Post by patslap on 2007-03-18
Okay - I'll retitle and repost the query.

Thanks for your efforts, though. ;)

---

### Post by patslap on 2007-03-18
Hi - I managed to fix the repositories problem using the walkthrough on this page: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

I had to follow the instructions in the 'Troublehooting' section at the botoom of the page.

I now ahve acces to over 18,000 repositories.

:KS

---

