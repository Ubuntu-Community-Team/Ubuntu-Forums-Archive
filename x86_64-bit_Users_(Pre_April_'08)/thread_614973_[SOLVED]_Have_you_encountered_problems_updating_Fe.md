---
title: "[SOLVED] Have you encountered problems updating Feisty?"
date: 2007-11-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Udibuntu on 2007-11-16
Hi Guys,

I was trying to download the recent updates and got the following error on 3 packages (the jibrish is Hebrew for "unable to download"):


W: &#1500;&#1488; &#1497;&#1499;&#1493;&#1500; &#1500;&#1492;&#1493;&#1512;&#1497;&#1491; [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.24-2ubuntu1.3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.24-2ubuntu1.3_amd64.deb)
   403 Forbidden


W: &#1500;&#1488; &#1497;&#1499;&#1493;&#1500; &#1500;&#1492;&#1493;&#1512;&#1497;&#1491; [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.24-2ubuntu1.3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.24-2ubuntu1.3_amd64.deb)
   403 Forbidden


W: &#1500;&#1488; &#1497;&#1499;&#1493;&#1500; &#1500;&#1492;&#1493;&#1512;&#1497;&#1491; [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.24-2ubuntu1.3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.24-2ubuntu1.3_amd64.deb)
   403 Forbidden

What do you think?

Cheers,

Udi

---

### Post by LS1 Brains on 2007-11-16
I'm running into the same issue just doing normal updates on x86_64 Gutsy, on the same packages.  My i386 laptop updated fine earlier this morning though.

---

### Post by richarddevries on 2007-11-16
Confirmed. I'm running Kubuntu i386. Downloading the packages via browser or wget gives the same results, while I am able to download older packages. See for example [here]("http://security.ubuntu.com/ubuntu/pool/main/s/samba/"): can't download *smbclient_3.0.26a-1ubuntu2.1_i386.deb*.
I'm guessing whoever published the .deb's forgot to set the privileges. I don't know how to notify whoever's responsible.

Seems that changing the server you update from to 'main' solves this. It worked for me :-) [See [SOLVED] samba, smb install forbidden]("http://ubuntuforums.org/showthread.php?t=614881").

---

### Post by Udibuntu on 2007-11-16
Daag Richard, dank U veel!

Changed "software sources" to Main in administration menu and successfully downloaded the 3 errant files, plus 44 more updates that the former server never mentioned...weird...

Again, thank you and good night, I'm off to find how to mark this RESOLVED :)

Udi

---

