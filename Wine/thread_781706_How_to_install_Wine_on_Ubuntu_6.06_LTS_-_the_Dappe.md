---
title: "How to install Wine on Ubuntu 6.06 LTS - the Dapper Drake?"
date: 2008-05-04
forum: Wine
---

### Post by westmatrix on 2008-05-04
How to install Wine on Ubuntu 6.06 LTS - the Dapper Drake.
The step by step version please.

I am only now starting to get into Ubuntu.

Cheers

---

### Post by Trance56k on 2008-05-04
Why are you starting out on drapper drake? Why not hardy heron?

---

### Post by westmatrix on 2008-05-04
It's the CD I got from Ubuntu.
The only version I have currently.

---

### Post by the8thstar on 2008-05-04
Download 8.04. It's much more current, unless you have some really, way-old hardware.

---

### Post by westmatrix on 2008-05-04
The only reason I am asking is due to the fact these do not seem to be working.

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)
[http://klik.atekon.de/wiki/index.php/How_to_use_klik](http://klik.atekon.de/wiki/index.php/How_to_use_klik)

---

### Post by westmatrix on 2008-05-04
> **the8thstar said:**
> Download 8.04. It's much more current, unless you have some really, way-old hardware.

Where do I get that?

---

### Post by westmatrix on 2008-05-04
I get this in the advanced dialogue of ubuntu add/remove

wine:
  Depends: libasound2 (>1.0.14) but 1.0.10-2ubuntu4 is to be installed
  Depends: libc6 (>=2.4) but 2.3.6-0ubuntu20.5 is to be installed
  Depends: libgphoto2-2 (>=2.4.0) but 2.1.6-5.2ubuntu8 is to be installed
  Depends: libgphoto2-port0 (>=2.4.0) but 2.1.6-5.2ubuntu8 is to be installed
  Depends: liblcms1 (>=1.15-1) but 1.13-1 is to be installed
 Depends: libldap-2.4-2 (>=2.4.7) but it is not installable
  Depends: libxml2 (>=2.6.27) but 2.6.24.dfsg-1ubuntu1.1 is to be installed
  Depends: libxslt1.1 (>=1.1.20) but 1.1.15-1ubuntu1 is to be installed
  PreDepends: dpkg (>=1.14.12ubuntu3) but 1.13.11ubuntu7 is to be installed

---

### Post by Trance56k on 2008-05-04
If you get Hardy Heron all you have to do is follow this guide...very easy. [http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb") It takes seconds.

---

### Post by westmatrix on 2008-05-04
The last time I installed Ubuntu, I jumoed onto an update and my Ubuntu was no more.
I hope that this wont break my Ubuntu.

---

### Post by Trance56k on 2008-05-04
Here follow this guide [https://help.ubuntu.com/community/HardyUpgrades]("https://help.ubuntu.com/community/HardyUpgrades")

---

### Post by westmatrix on 2008-05-04
Cannot install 'wine'

This application conflicts with other installed software. To install 'wine' the conflicting software must be removed before.

Switch to the advanced mode to resolve this conflict.

I get this in the advanced dialogue of ubuntu add/remove

wine:
  Depends: libasound2 (>1.0.14) but 1.0.10-2ubuntu4 is to be installed
  Depends: libc6 (>=2.4) but 2.3.6-0ubuntu20.5 is to be installed
  Depends: libgphoto2-2 (>=2.4.0) but 2.1.6-5.2ubuntu8 is to be installed
  Depends: libgphoto2-port0 (>=2.4.0) but 2.1.6-5.2ubuntu8 is to be installed
  Depends: liblcms1 (>=1.15-1) but 1.13-1 is to be installed
 Depends: libldap-2.4-2 (>=2.4.7) but it is not installable
  Depends: libxml2 (>=2.6.27) but 2.6.24.dfsg-1ubuntu1.1 is to be installed
  Depends: libxslt1.1 (>=1.1.20) but 1.1.15-1ubuntu1 is to be installed
  PreDepends: dpkg (>=1.14.12ubuntu3) but 1.13.11ubuntu7 is to be installed

---

### Post by westmatrix on 2008-05-04
> **Trance56k said:**
> Here follow this guide [https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)

[B]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[/B]

---

### Post by westmatrix on 2008-05-04
> **Trance56k said:**
> Here follow this guide [https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)


Just to make sure that we are on the same page:

admin@admin-laptop:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 6.06.2 LTS
Release:        6.06
Codename:       dapper
admin@admin-laptop:~$

---

### Post by Trance56k on 2008-05-04
Sorry thought you were going to upgrade then try.

---

### Post by the8thstar on 2008-05-04
Ubuntu 8.04 is available here: [http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")

Choose the DESKTOP version.

Download the ISO.
Burn the CD.
**[COLOR="Red"]BACKUP YOUR DOCUMENTS.[/COLOR]** on another CD or on an USB key.
Put the Ubuntu CD in the drive.
Reboot your computer.
Follow the on-screen intructions.

---

### Post by westmatrix on 2008-05-04
I have no clue how to upgrade.
The steps that are on the site will not work.

I have found a site that can do what I asked for.
[http://linuxgamingtoday.wordpress.com/2008/02/03/how-to-install-wine-in-ubuntu/](http://linuxgamingtoday.wordpress.com/2008/02/03/how-to-install-wine-in-ubuntu/)

---

### Post by westmatrix on 2008-05-04
> **the8thstar said:**
> Ubuntu 8.04 is available here.

Download the ISO.
Burn the CD.
**[COLOR=Red]BACKUP YOUR DOCUMENTS.[/COLOR]** on another CD or on an USB key.
Put the Ubuntu CD in the drive.
Reboot your computer.
Follow the on-screen intructions.


[B]admin@admin-laptop:~$ wine --version
wine-0.9.59
admin@admin-laptop:~$


Is that right?
[/B]

---

### Post by westmatrix on 2008-05-04
I am awaiting my new CD for 
Ubuntu 8.04 LTS Desktop Edition

8 to 10 weeks.
Will call then.

Cheers and Thank you all for helping me here.

---

### Post by the8thstar on 2008-05-04
> **westmatrix said:**
> [B]admin@admin-laptop:~$ wine --version
wine-0.9.59
admin@admin-laptop:~$


Is that right?
[/B]


WTF? What has it all got to do with Wine??? :confused: :confused: :confused:

---

### Post by westmatrix on 2008-05-04
That is to prove that wine is installed.
I was asking if it was right.
 
Cheers

---

### Post by the8thstar on 2008-05-04
It's correct, yes.

Don't you want to download the CD yourself instead of waiting 10 weeks?

---

### Post by westmatrix on 2008-05-05
That's cool, how do I get wine icon on the desktop?
 
I would need to buy an extra GIG of bandwidth to do that.
I have spent a ton of cash this month and it's only just started.
Will wait to get more work in first.
 
Cheers

---

