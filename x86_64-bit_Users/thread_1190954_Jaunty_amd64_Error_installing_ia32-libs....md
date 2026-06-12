---
title: "Jaunty amd64 Error installing ia32-libs..."
date: 2009-06-18
forum: x86 64-bit Users
---

### Post by nderic77 on 2009-06-18
When I try to run the following:
sudo apt-get install ia32-libs

I get the following error message:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  ia32-libs
0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
Need to get 0B/28.0MB of archives.
After this operation, 128MB of additional disk space will be used.
(Reading database ... 101826 files and directories currently installed.)
Unpacking ia32-libs (from .../ia32-libs_2.7ubuntu6_amd64.deb) ...
lzma: Decoder error
dpkg-deb: subprocess <decompress> returned error exit status 1
dpkg: error processing /var/cache/apt/archives/ia32-libs_2.7ubuntu6_amd64.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib32/dri/i810_dri.so')
Errors were encountered while processing:
 /var/cache/apt/archives/ia32-libs_2.7ubuntu6_amd64.deb


Any idea what is causing this? I am running 64 bit Jaunty on a Dell Inspiron laptop (AMD 64 bit X2 processor). Many thanks!

---

### Post by Yellow Pasque on 2009-06-18
Perhaps a corrupt download of ia32-libs? Try using the following command to clean the local cache of downloaded .debs:
```
sudo apt-get clean
```
Then try installing again.

---

### Post by nderic77 on 2009-06-19
That solved it! Many thanks.

---

