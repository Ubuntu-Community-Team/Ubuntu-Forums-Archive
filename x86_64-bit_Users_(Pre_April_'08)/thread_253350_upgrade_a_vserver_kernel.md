---
title: "upgrade a vserver kernel"
date: 2006-09-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by vdvm on 2006-09-08
Hi,

I have an ubuntu 6.06 LTS server installation with linux-vserver ( linux-image-2.6.15-26-amd64-k8 ) and 3 vservers (Debian) installed.

When i want to upgrade i get the following:

<pre>
The following packages have been kept back:
  linux-image-amd64-server
The following packages will be upgraded:
  base-files bind9-host dnsutils gnupg libbind9-0 libdns21 libisc11 libisccc0 libisccfg1 libkrb53   liblwres9 libssl0.9.8 linux-amd64-server linux-image-2.6.15-26-amd64-k8 login openssl passwd   ubuntu-minimal ubuntu-standard util-vserver
</pre>

Is it safe to upgrade? I see there is a kernel file.
I don't want my 3 vservers to have downtime. Or minimal downtime.

Please help, thank you.

If you need more information, please ask.

---

### Post by kuja on 2006-09-08
By the looks of it, it should be safe to upgrade it.

---

### Post by vdvm on 2006-09-10
Thank you for your reply.

Will a reboot be needed?
Can i expect anything else?

---

### Post by kuja on 2006-09-10
Well, for changes in most of that stuff being updated no, but there is a linux kernel update in there. It would be the only thing to require a reboot to notice.

---

