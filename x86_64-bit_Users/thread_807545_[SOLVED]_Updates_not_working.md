---
title: "[SOLVED] Updates not working"
date: 2008-05-25
forum: x86 64-bit Users
---

### Post by gibsonsimswilson on 2008-05-25
Hi

I am new and I have some updates not working I get an error message every time the update manager tries to do the updates.

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) hardy Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: NODATA 1 NODATA 2

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://cn.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://cn.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://cn.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://cn.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://cn.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://cn.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://cn.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/hardy/Release](http://cn.archive.ubuntu.com/ubuntu/dists/hardy/Release)  

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://cn.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
 
It then tries to download and just "hangs" on Downloading file 18 of 26 :-(
Anyone have a problem too? Do you know what is wrong?
Many thanks, Gibby

---

### Post by tamoneya on 2008-05-25
try using a different mirror.  It seems like you just cant connect.

---

### Post by gibsonsimswilson on 2008-05-25
When using the "update Manager" how do I select a different mirror ?

Thanks

Gibby

---

### Post by tamoneya on 2008-05-25
you have to change it in synaptic (system -> admin -> synaptic package manager) Then go to the settings menu and select repositories.  There is a drop down menu there that lets you select the server.

---

### Post by gibsonsimswilson on 2008-05-25
Great 
Thanks you
Works now
Gibby

---

