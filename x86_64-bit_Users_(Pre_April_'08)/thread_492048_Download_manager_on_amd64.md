---
title: "Download manager on amd64?"
date: 2007-07-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by shafin on 2007-07-04
Is there any 64 bit download manager for linux that supports resuming after I've rebooted?

---

### Post by xen on 2007-07-04
I know its not ideal for some people but I find that WGET is fine, you should already have it.

wget -c [www.lol.com/whatever.zip](www.lol.com/whatever.zip)

The -c flag allows you to resume the download, just remember it next time you restart the download.

---

### Post by shafin on 2007-07-04
Is there any GUI for Wget?

---

### Post by jamesford on 2007-07-04
gwget

---

### Post by shafin on 2007-07-04
> **jamesford said:**
> gwget
available on synaptic?

---

### Post by jamesford on 2007-07-04
believe so. why dont u check

---

### Post by CyberAngel on 2007-07-05
I use WebDownloader for X and I am very pleased with it ;)

sudo apt-get install d4x

---

### Post by psoulocybe on 2007-07-05
Been using Freeloader.  It handles torrents as well which i find handy.  In fact it's all I use for torrents now.   Usually use wget for regular downloads.

---

