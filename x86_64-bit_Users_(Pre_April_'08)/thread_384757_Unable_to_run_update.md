---
title: "Unable to run update"
date: 2007-03-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by brwatters on 2007-03-14
Hello all,

We are unable to run "sudo apt-get update" on our Ubuntu v6.10 64BIT install? .. this from a fresh today ISO install .. Looks like something is pooched .. 

:~$ sudo apt-get update
Password:
Ign cdrom://Ubuntu-Server 6.10 _Edgy Eft_ - Release amd64 (20061025.1) edgy/main Translation-en_US
Ign cdrom://Ubuntu-Server 6.10 _Edgy Eft_ - Release amd64 (20061025.1) edgy/restricted Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources              
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg                                                                                  
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.8), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.8), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.8), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.8), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.8), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.8), connection timed out
Fetched 1B in 24m0s (0B/s)                             
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg)  Could not connect to us.archive.ubuntu.com:80 (91.189.89.8), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2)  Could not connect to us.archive.ubuntu.com:80 (91.189.89.8), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_US.bz2)  Could not connect to us.archive.ubuntu.com:80 (91.189.89.8), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg)  Could not connect to us.archive.ubuntu.com:80 (91.189.89.8), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_US.bz2)  Could not connect to us.archive.ubuntu.com:80 (91.189.89.8), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to us.archive.ubuntu.com:80 (91.189.89.8), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
brwatters@voipmonitor:~$ ping [www.yahoo.com](www.yahoo.com)
PING [www.yahoo-ht2.akadns.net](www.yahoo-ht2.akadns.net) (209.131.36.158) 56(84) bytes of data.
64 bytes from f1.[www.vip.sp1.yahoo.com](www.vip.sp1.yahoo.com) (209.131.36.158): icmp_seq=1 ttl=52 time=21.0 ms
64 bytes from f1.[www.vip.sp1.yahoo.com](www.vip.sp1.yahoo.com) (209.131.36.158): icmp_seq=2 ttl=52 time=22.0 ms
64 bytes from f1.[www.vip.sp1.yahoo.com](www.vip.sp1.yahoo.com) (209.131.36.158): icmp_seq=3 ttl=53 time=21.5 ms



Anyone have any ideas how to resolve this issue ??

BRW

---

### Post by Kilz on 2007-03-14
Are you sure you have internet access with Ubuntu?

---

### Post by brwatters on 2007-03-15
In the above you will note that I have 

brwatters@voipmonitor:~$ ping [www.yahoo.com](www.yahoo.com)
PING [www.yahoo-ht2.akadns.net](www.yahoo-ht2.akadns.net) (209.131.36.158) 56(84) bytes of data.
64 bytes from f1.[www.vip.sp1.yahoo.com](www.vip.sp1.yahoo.com) (209.131.36.158): icmp_seq=1 ttl=52 time=21.0 ms
64 bytes from f1.[www.vip.sp1.yahoo.com](www.vip.sp1.yahoo.com) (209.131.36.158): icmp_seq=2 ttl=52 time=22.0 ms
64 bytes from f1.[www.vip.sp1.yahoo.com](www.vip.sp1.yahoo.com) (209.131.36.158): icmp_seq=3 ttl=53 time=21.5 ms


I put that there to show that indeed I do have Internet access .. Realy I have an OC-12 .. 

ANy ideas???

BRW

---

### Post by John.Michael.Kane on 2007-03-15
Judging from your errors it seems the us. repo was down. you can try replacing your sources with one below.

Heres a clean sources list 

First:
```
gksudo gedit /etc/apt/sources.list
```

Replace with this:
```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu edgy universe
deb-src http://archive.ubuntu.com/ubuntu edgy universe

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted

deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

deb http://archive.ubuntu.com/ubuntu edgy multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy multiverse

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
```

Run:
```
gksudo aptitude update
```

---

