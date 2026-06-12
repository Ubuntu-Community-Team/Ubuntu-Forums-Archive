---
title: "[SOLVED] Error with 2.6.27-7-generic kernel"
date: 2008-11-05
forum: x86 64-bit Users
---

### Post by orrie on 2008-11-05
I've just updated my Hardy to Intrepid and when I try to install something I get an weird error.

I've tried to run an *sudo apt-get install -f* without positive results..

```

orrie@ubuntu ~ ;) sudo apt-get install -f
Leser pakkelister ... Ferdig
Skaper oversikt over avhengighetsforhold       
Leser tilstandsinformasjon ... Ferdig   
0 oppgraderte, 0 nylig installerte, 0 å fjerne og 1 ikke oppgradert.
5 pakker ikke fullt installert eller fjernet.
Etter denne operasjonen vil 0B ekstra diskplass bli brukt.
Setter opp linux-image-2.6.27-7-generic (2.6.27-7.16) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.27-7-generic
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: Feil ved behandling av linux-image-2.6.27-7-generic (--configure):
 underprosessen post-installation script returnerte feilstatus 2
dpkg: Kravproblem hindrer oppsettet av linux-restricted-modules-2.6.27-7-generic:
 linux-restricted-modules-2.6.27-7-generic krever linux-image-2.6.27-7-generic. Men:
  Pakke linux-image-2.6.27-7-generic er ikke satt opp enda.
dpkg: Feil ved behandling av linux-restricted-modules-2.6.27-7-generic (--configure):
 kravproblem - setter ikke opp pakken
dpkg: Kravproblem hindrer oppsettet av linux-image-generic:
 linux-image-generic krever linux-image-2.6.27-7-generic. Men:
  Pakke linux-image-2.6.27-7-generic er ikke satt opp enda.
dpkg: Feil ved behandling av linux-image-generic (--configure):
 kravproblem - setter ikke opp pakken
dpkg: Kravproblem hindrer oppsettet av linux-restricted-modules-generic:
 linux-restricted-modules-generic krever linux-restricted-modules-2.6.27-7-generic. Men:
  Pakke linux-restricted-modules-2.6.27-7-generic er ikke satt opp enda.
dpkg: Feil ved behandling av linux-restricted-modules-generic (--configure):
 kravproblem - setter ikke opp pakken
dpkg: Kravproblem hindrNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                 No apport report written because the error message indicates its a followup error from a previous failure.
                                                           No apport report written because MaxReports is reached already
                                                                                                                         No apport report written because MaxReports is reached already
       er oppsettet av linux-generic:
 linux-generic krever linux-image-generic (= 2.6.27.7.11). Men:
  Pakke linux-image-generic er ikke satt opp enda.
 linux-generic krever linux-restricted-modules-generic (= 2.6.27.7.11). Men:
  Pakke linux-restricted-modules-generic er ikke satt opp enda.
dpkg: Feil ved behandling av linux-generic (--configure):
 kravproblem - setter ikke opp pakken
Det oppsto feil ved behandling av:
 linux-image-2.6.27-7-generic
 linux-restricted-modules-2.6.27-7-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It says that *linux-restricted-modules-generic* isn't set up yet, but I tried to install the package with the same error-message...

Here's some of my system info:
```

orrie@ubuntu ~ ;) lsb_release -a ; uname -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid
Linux ubuntu 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64 GNU/Linux

```


I think this is the error whose causing all this errors:
```

Could not find postinst hook script [update-grub].

```

Can somebody please help me with this? :P

---

### Post by orrie on 2008-11-05
Lol, actually I've solved this.
I have more than one disk and I've tried to run *grub-install*, but didn't have it installed on this partition, so I just ran this code and it worked:

```
sudo apt-get install grub
```

Oh my god, how silly... :)

---

