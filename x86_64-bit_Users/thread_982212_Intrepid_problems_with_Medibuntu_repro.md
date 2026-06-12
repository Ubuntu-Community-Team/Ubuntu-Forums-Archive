---
title: "Intrepid problems with Medibuntu repro"
date: 2008-11-14
forum: x86 64-bit Users
---

### Post by Terry S on 2008-11-14
I am using Intrepid AMD64 and I installed the medibuntu repros using the following:-

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

but I now get the message below when I reload.

GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch [http://archive.canonical.com/ubuntu/dists/interpid/partner/binary-amd64/Packages.gz](http://archive.canonical.com/ubuntu/dists/interpid/partner/binary-amd64/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Can anyone help?

---

### Post by cariboo on 2008-11-14
You also have to run this command:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

This will install the correct Public key.

Jim

---

### Post by Terry S on 2008-11-14
> **cariboo907 said:**
> You also have to run this command:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

This will install the correct Public key.

Jim

Thanks Jim that did the trick.

---

### Post by cariboo on 2008-11-18
If you have an exisiting Medibuntu key you may want to remove it, and try again. See screenshot  for my setup.

Jim

---

### Post by Terry S on 2008-11-18
Hi cariboo907

I do not have an existing key. I would show a screen shot but I do not know how to insert the png file into this message. (Well what do you know it appears I do know how to insert an image) :-)

The only entries in the Authentication tab are 

Ubuntu Archives Automatic signing Key
Ubuntu CD Image Automatic signing key

---

