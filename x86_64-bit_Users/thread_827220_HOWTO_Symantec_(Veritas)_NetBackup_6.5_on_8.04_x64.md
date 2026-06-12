---
title: "HOWTO Symantec (Veritas) NetBackup 6.5 on 8.04 x64 Server"
date: 2008-06-12
forum: x86 64-bit Users
---

### Post by joesapo on 2008-06-12
This is a quick howto on getting Symantec NetBackup 6.5 client installed on 64bit Ubuntu 8.04 LTS Server Edition.

```
sudo apt-get install xinetd
sudo apt-get install ia32-libs
sudo tar -xvf NetBackup_6.5_CLIENTS2.tar
sudo ./NB_65_CLIENTS2_20070723/install
```

Choose RedHat 2.6 as OS...  There will be a few errors generated, but most are simply due to the inability to create files in a rc.d structure...

```
sudo cp /usr/openv/netbackup/bin/goodies/nbclient /etc/init.d/
sudo /etc/init.d/nbclient start
sudo /etc/init.d/xinetd restart
```

I'll keep this post updated with any further info I find, but for the base client install that's all you gotta do!

Peace

---

### Post by vitalyb on 2009-01-07
This works great, you have saved me a headache.  Thanks.

---

### Post by vitalyb on 2009-01-28
Symantec has finally put this information along with other install details for NetBackup 6.5.2 on Ubuntu 8.04 on their support site.  You can find it here:

[http://support.veritas.com/docs/308593](http://support.veritas.com/docs/308593)

---

### Post by TurcoJC on 2009-04-30
Many thanks from Argentina. It wokrs great on Ubuntu Desktop i386 (32 bits)
Regards!!

---

