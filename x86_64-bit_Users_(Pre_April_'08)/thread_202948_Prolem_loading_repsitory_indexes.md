---
title: "Prolem loading repsitory indexes"
date: 2006-06-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by quistive on 2006-06-24
I am a relatively new Ubuntu user and have just installed ubuntu 6.06 on a new computer of mine (64 bit amd).  Since installing it, I have never been able to Download any repository index.

Specifically, I always get the error: "Could not download all repository indexes"

My sources list is as follows:

# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release amd64 (20060531)]/ dapper main restricted

I have also tried using a different mirror for all of the repositories (ie. [http://mirror.pacific.net.au/linux/ubuntu/)](http://mirror.pacific.net.au/linux/ubuntu/)), but it didn't work either

I have a laptop and I have been able to refresh my repositories before (although that may have been at work).  However, my laptop is experiencing the same problem currently.

I have disabled the ipv6 line of my /etc/modprobe.d/aliases folder:
alias net-pf-10 ipv6 disabled
(I have tried it both ways, but it doesn't seem to make a difference).

I can use Firefox and ping to access the internet.

Does anybody have any ideas? help? please?

---

### Post by incubus on 2006-06-24
quistive,

That's pretty strange.
1. Are you behind some proxy? Or could something/somebody be blocking access to some hosts?

2. Can you also ping us.archive.ubuntu.com ? Even better, can you use Firefox to go to: [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) ?

3. Have you tried that in your laptop when you're in a different network?

incubus

---

### Post by mnault on 2006-06-24
1

---

### Post by mnault on 2006-06-24
1

---

### Post by quistive on 2006-06-25
I'm not sure what's going on.  It seems to be working now.  I thought I had problems with this type of thing in the past, but have always assumed it to be a fluke.  It seems more and more like a pattern. :confused: 

Network-wise, I have a DSL Modem (Actiontec GT701-WG) feeding into a Linksys WRTP54G.  It is off of the Linksys network where my laptop and desktop receive their network.  They both use DHCP.

It is wierd that it comes and goes, but it seems to be working now (for tonight anyways).  I'll answer y'alls questions when it isn't working again.

---

### Post by pracslipkerm on 2006-06-25
My PC tries to connect to 192.168.0.1 when running synaptic, apt-get or aptitude from user or root login. Just tried ctl-alt-F1 login as root and it worked - looked to the ftp site rather than 192.168.0.1. Came back to normal login and still doesn't work even in a root terminal.
Does anyone know what's going on? No proxy or gateway setup - This wasn't happening before the update to dapper.
Any help would be fantastic
Cheers Steve Griffiths :-)

---

### Post by incubus on 2006-06-25
Do you have anything strange in your 
```

/etc/resolv.conf

```

Seems to me it's thinking your router is a DNS server.

incubus

PS: If you have information on your internet provider there, don't post it here.

---

### Post by pracslipkerm on 2006-06-26
/etc/resolv.conf only has the ISP search address & dns ip address.
Where could synaptic, apt-get & aptitude be looking for this dummy ip address. My browser works fine...
Cheers
  Steve :-)

---

### Post by pracslipkerm on 2006-06-26
Just found the answer on another thread. Somehow during upgrade a proxy setting was added. I went to System -> Preferences -> Network Proxy and changed manual proxy to direct connection. I checked the proxy environment setting with:
```
 sudo env|grep proxy 
```
Thanks for the support guys!!!!
Hope this helps someone else too.
Off to try and solve usb and cdrom issues
Cheers 
  Steve :-)

---

