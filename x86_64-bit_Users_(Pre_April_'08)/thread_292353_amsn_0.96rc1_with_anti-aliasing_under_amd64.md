---
title: "amsn 0.96rc1 with anti-aliasing under amd64"
date: 2006-11-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by diego_sza on 2006-11-03
[FONT="Arial"][SIZE="4"]Hi! I created packages of tcl8.5a5, tk8.5a5, tls1.5 and amsn0.96rc1 in order to have an easy installation of amsn with anti-aliased fonts.

The thing is that i can't log in because I can't pass the tls part. Amsn  cannot download it automatically, and if i do it manually and configure it properly it doesn't work.

Why do I have to download it, if I already made a package? 
Before creating a package I downloaded the tls file from the same server that amsn attemps to download the file, so the server is working.

I'm running on ubuntu edgy, with an amd64 athlon X2 processor. Any ideas?[/SIZE][/FONT]

---

### Post by Princey on 2006-11-03
> **diego_sza said:**
> [FONT="Arial"][SIZE="4"]Hi! I created packages of tcl8.5a5, tk8.5a5, tls1.5 and amsn0.96rc1 in order to have an easy installation of amsn with anti-aliased fonts.

The thing is that i can't log in because I can't pass the tls part. Amsn  cannot download it automatically, and if i do it manually and configure it properly it doesn't work.

Why do I have to download it, if I already made a package? 
Before creating a package I downloaded the tls file from the same server that amsn attemps to download the file, so the server is working.

I'm running on ubuntu edgy, with an amd64 athlon X2 processor. Any ideas?[/SIZE][/FONT]


I'm not sure if you're using Ubuntu or Kubuntu, but whichever makes no difference. Fire up Synaptic or Adept, whichever you have and do a search for tcltls in there. It should give you 1.5 as the latest version. Install it, and all will be well.

---

### Post by diego_sza on 2006-11-03
I thought the same, but then I have dependency problems. Tcltls only wants to have tcl8.3 or tcl8.4 I think...

---

### Post by Princey on 2006-11-03
I'm still running dapper, not yet on edgy (still contemplating whether to upgrade) but that's how I got my problem with the tls prompt solved. I had to install it via adept although I'm not sure which version, I'll have to check and see.

---

### Post by diego_sza on 2006-11-04
If someone wants to help, post your email address and I send you the already compiled packages. I had success in dapper, but now I can't run amsn 0.96 on edgy. The packages are for amd64 architecture.

---

### Post by toaster.waffle on 2006-12-18
> **diego_sza said:**
> If someone wants to help, post your email address and I send you the already compiled packages. I had success in dapper, but now I can't run amsn 0.96 on edgy. The packages are for amd64 architecture.


Does this help?

[http://permalink.gmane.org/gmane.network.instant-messaging.amsn.devel/4402](http://permalink.gmane.org/gmane.network.instant-messaging.amsn.devel/4402)

---

### Post by JRaz on 2006-12-26
Tried the auto installer from the website but I got this error,

```
The installation of this software requires some additional support
code to be installed.

A] If the support code is found in a local directory, it will be used.
   The file containing the support code will be called:

      "autopackage.tar.bz2"

 or

B] If there is an active Internet connection, the support code will be
   downloaded from:

      "http://autopackage.org/downloads/latest/autopackage.tar.bz2"

   Proxy users should ensure the http_proxy environment variable is
   set, otherwise the download may fail.


Selection B --> OK to download and install support code now? (Y/n): 

Attempting download of http://autopackage.org/downloads/latest/x86_64/auto
e.tar.bz2 ... 

--03:18:27--  http://autopackage.org/downloads/latest/x86_64/autopackage.t
           => `autopackage.tar.bz2'
Resolving autopackage.org... 130.225.247.90
Connecting to autopackage.org|130.225.247.90|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
03:18:28 ERROR 404: Not Found.

Download failed.


Attempting download of http://www.wildgardenseed.com/autopackage/latest/x8
utopackage.tar.bz2 ... 

--03:18:28--  http://www.wildgardenseed.com/autopackage/latest/x86_64/auto
e.tar.bz2
           => `autopackage.tar.bz2'
Resolving www.wildgardenseed.com... 209.25.170.201
Connecting to www.wildgardenseed.com|209.25.170.201|:80... connected.
HTTP request sent, awaiting response... 404 
03:18:30 ERROR 404: (no description).

Download failed.


Attempting download of http://www.allaboutgames.co.uk/autopackage/latest/xautopackage.tar.bz2 ... 

--03:18:30--  http://www.allaboutgames.co.uk/autopackage/latest/x86_64/autge.tar.bz2
           => `autopackage.tar.bz2'
Resolving www.allaboutgames.co.uk... 82.165.123.208
Connecting to www.allaboutgames.co.uk|82.165.123.208|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
03:18:30 ERROR 404: Not Found.

Download failed.



Please check your Internet connection, or try again later.
The autopackage support code could not be installed.

It can be manually downloaded and installed by running the
installation script located in the downloaded archive.

```

any help would be greatly appreciated

---

