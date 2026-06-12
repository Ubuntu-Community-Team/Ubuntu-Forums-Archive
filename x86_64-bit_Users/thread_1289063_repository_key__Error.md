---
title: "repository key  Error"
date: 2009-10-12
forum: x86 64-bit Users
---

### Post by kartook on 2009-10-12
HI 

i am using Ubuntu -9.04 -64 bit . 

I was ttry to update the packages but i got this error message . I was Addes few new repository and GPG keys also .

KIndly guide me i am bit new to ubuntu 

My error Was 
```

GPG error: http://packages.medibuntu.org jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783GPG 

error: 
http://repository.cairo-dock.org jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1392A97E41317877GPG 

error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0E494DBB2F021AC1GPG 

error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6D975C4791E7EE5EGPG 

error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7FB8BEE0A1F196A8Failed to fetch 

http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages  404 Not Found [IP: 78.141.179.2 80]
Some index files failed to download, they have been ignored, or old ones used instead.

```

Advance thanks

---

### Post by garvinrick4 on 2009-10-12
Google what keys you need and copy and paste them in terminal press enter.
type password if asks and will load key.

Do it for each one.

medibuntu for jaunty for instance.  

Then any other key you need to repeat for that repository.

---

### Post by MelDJ on 2009-10-12
as said above, you must add the gpg key for each source. add it by following the steps in the video here: [http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu](http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu)

---

