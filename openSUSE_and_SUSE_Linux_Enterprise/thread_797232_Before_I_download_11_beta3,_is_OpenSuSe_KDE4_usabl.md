---
title: "Before I download 11 beta3, is OpenSuSe KDE4 usable"
date: 2008-05-17
forum: openSUSE and SUSE Linux Enterprise
---

### Post by shuttleworthwannabe on 2008-05-17
Hi there
just heard that OpenSuSe 11beta3 has been released for testing. cliams to have squashed 700 odd bugs; this is great, I thought I would give it a try; beta1 did not even go beyond loading the desktop. I guess what I asking is:

1. Is the KDE4 desktop usable; no hanging menus etc
2. Does the OpenSuSe version come with built-in ATI fglrx drivers? If not is there a way to get this installed?

Thanks
S

---

### Post by Fatec on 2008-05-17
Was very fast and very useable for me, which i found suprising.

So far OpenSuse 11 is exceeding all my expectations, fast, stable.

---

### Post by shuttleworthwannabe on 2008-05-17
as i suspected, there are no ATI drivers ready for the 2.6.25 kernel, as far as I can see. Does anyone know how to get these installed in 11 beta 3; I have it running but screen is wavy and not clear.

thnaks

---

### Post by Erunno on 2008-05-17
> **shuttleworthwannabe said:**
> 
1. Is the KDE4 desktop usable; no hanging menus etc


Let me put it this way: It's as good as a KDE 4.0 based desktop can get. openSUSE developers backported some stuff from the 4.1 development branch but in the end it's still KDE 4.0 from january minus some bugs and plus some openSUSE specific branding. I'd probably wait for the final release of 4.1 though.

> 2. Does the OpenSuSe version come with built-in ATI fglrx drivers? If not is there a way to get this installed?

openSUSE does not ship closed source binary drivers by default, so no fglrx by default. You can easily enable the ATI repository in Yast and get the latest driver though.

---

### Post by shuttleworthwannabe on 2008-05-18
erunnoo, thanks. could u show me how to enable the 'restricted' repo's in 11 beta3? as it stands, YaST has 3 repo's listed and none are about 'non-free'. there are guides for 10.3 but they do not work for 11beta3.
much appreciated,
S

---

### Post by Incense on 2008-05-18
> **shuttleworthwannabe said:**
> erunnoo, thanks. could u show me how to enable the 'restricted' repo's in 11 beta3? as it stands, YaST has 3 repo's listed and none are about 'non-free'. there are guides for 10.3 but they do not work for 11beta3.
much appreciated,
S

Have you tried the one click install for ATI? [http://opensuse-community.org/1-click-collection#Drivers]("http://opensuse-community.org/1-click-collection#Drivers").

---

### Post by RedDwarf on 2008-05-18
[http://www2.ati.com/suse/11.0/repodata/repomd.xml](http://www2.ati.com/suse/11.0/repodata/repomd.xml) -> File not found
[http://http.download.nvidia.com/opensuse/11.0/repodata/repomd.xml](http://http.download.nvidia.com/opensuse/11.0/repodata/repomd.xml) -> File not found

Don't expect ATI/NVIDIA to publish repositories before the final version.

---

### Post by shuttleworthwannabe on 2008-05-18
RedDwarf is correct, nothing on 1-click owrks, and all those links are truly dead. I thought ATI funds SUSE development, so why would one want to to try SUSE and report bugs, when hardware is not even supported (by same manufacturers that support suse??) am i missing something?

---

### Post by Erunno on 2008-05-22
> **shuttleworthwannabe said:**
> I thought ATI funds SUSE development, so why would one want to to try SUSE and report bugs, when hardware is not even supported (by same manufacturers that support suse??) am i missing something?

Novell is funding the development of radeonhd, a free driver for newer ATI cards which was started after ATI/AMD released the specifications for various cards. ATI is helping with the development. Novell has nothing to do with fglrx.

---

### Post by trmiv on 2008-05-22
Wow I just tried beta 3 today myself, very very very nice!  Does anyone know if I go ahead and install it now, will I need to reinstall when final comes out, or can I just download updates and have final like how it works with Ubuntu?

---

### Post by CM Xtasy on 2008-05-22
> **trmiv said:**
> Wow I just tried beta 3 today myself, very very very nice!  Does anyone know if I go ahead and install it now, will I need to reinstall when final comes out, or can I just download updates and have final like how it works with Ubuntu?

You should be able to update, but it's recommended to do a clean install for the final.

---

### Post by ingvildr on 2008-06-02
This is strange because apart from kde4 not having all the functionality I expect, it also looks ugly, yast2 qt4 port also looks ugly compared to its qt3 counterpart and also that plasma crashes regularly and just in general feels unpolished.

---

### Post by quickshade on 2008-06-02
People state that it's not usable but never list why......figures.

---

