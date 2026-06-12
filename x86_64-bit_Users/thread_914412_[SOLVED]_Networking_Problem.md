---
title: "[SOLVED] Networking Problem"
date: 2008-09-08
forum: x86 64-bit Users
---

### Post by aquatone282 on 2008-09-08
Hi,

I'm unable to connect to certain addresses on the internet using Firefox 3.0, Pidgin, or even apt-get.  This is on a fresh install of 8.0.4 Hardy on an ASUS M2A-VM motherboard with an AMD Phenom 9550 and 4GB of RAM.

I can connect to some addresses, such as [www.google.com](www.google.com), but can't connect to these forums.  No errors - just a never-ending spinner showing the page loading.

I am unable to connect to the ubuntu irc channel using Pidgin - again just a message that it is connecting but it never does.

When I try to run apt-get update, it hangs at the following location:

```
jacoulter@amd64:~$ sudo apt-get update
[sudo] password for jacoulter: 
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_US     
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US  
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release                     
Hit http://security.ubuntu.com hardy-security/main Packages               
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/main Sources                
Hit http://security.ubuntu.com hardy-security/restricted Sources          
Hit http://security.ubuntu.com hardy-security/universe Packages           
Hit http://security.ubuntu.com hardy-security/universe Sources            
Hit http://security.ubuntu.com hardy-security/multiverse Packages         
Hit http://security.ubuntu.com hardy-security/multiverse Sources          
Err http://us.archive.ubuntu.com hardy Release.gpg                        
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.2.0.4 80]
Err http://us.archive.ubuntu.com hardy/main Translation-en_US
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.2.0.4 80]
Err http://us.archive.ubuntu.com hardy/restricted Translation-en_US
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.2.0.4 80]
Err http://us.archive.ubuntu.com hardy/universe Translation-en_US
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.2.0.4 80]
Err http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.2.0.4 80]
Err http://us.archive.ubuntu.com hardy-updates Release.gpg
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.2.0.4 80]
Err http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.2.0.4 80]
Err http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.2.0.4 80]
Err http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.2.0.4 80]
Err http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.2.0.4 80]
Reading package lists... Done                       
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  Unable to connect to us.archive.ubuntu.com http: [IP: 91.2.0.4 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2  Unable to connect to us.archive.ubuntu.com http: [IP: 91.2.0.4 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2  Unable to connect to us.archive.ubuntu.com http: [IP: 91.2.0.4 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2  Unable to connect to us.archive.ubuntu.com http: [IP: 91.2.0.4 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2  Unable to connect to us.archive.ubuntu.com http: [IP: 91.2.0.4 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg  Unable to connect to us.archive.ubuntu.com http: [IP: 91.2.0.4 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2  Unable to connect to us.archive.ubuntu.com http: [IP: 91.2.0.4 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2  Unable to connect to us.archive.ubuntu.com http: [IP: 91.2.0.4 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2  Unable to connect to us.archive.ubuntu.com http: [IP: 91.2.0.4 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2  Unable to connect to us.archive.ubuntu.com http: [IP: 91.2.0.4 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
jacoulter@amd64:~$ 
```

I disabled IPv6 in /etc/modprobe.d/aliases, but the problem persists.  

I have 32-bit Hardy running on my old Pentium IV box and everything works just fine, so I don't believe I have any problems with my router.

Any suggestions or troubleshooting tips most welcome.

Cheers,

Jim

---

