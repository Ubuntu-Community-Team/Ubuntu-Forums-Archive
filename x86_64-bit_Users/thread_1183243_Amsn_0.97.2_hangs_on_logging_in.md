---
title: "Amsn 0.97.2 hangs on logging in"
date: 2009-06-09
forum: x86 64-bit Users
---

### Post by SergeantOreo on 2009-06-09
Hey,

I've installed Amsn through Synaptic, and when I try to sign in, the application hangs at "logging in" and will not do anything else. 

I've Googled this issue but haven't found anything of use.

Cheers.

---

### Post by istblacken on 2009-06-10
you can use the svn version of it from this PPA;
[https://launchpad.net/~amsn-daily/+archive/ppa](https://launchpad.net/~amsn-daily/+archive/ppa)

it is because that version uses an old version of the protocol so it is not compatible with the latest protocol. Svn version is pretty good and updated frequently.

---

### Post by SergeantOreo on 2009-06-10
Thanks for replying.

I downloaded the amsn-data and amsn_amd64 .deb files. The data .deb installs correctly but when I try to install Amsn itself, it gave
the error, "Error: Dependency is not satisfiable: libgssdp-1.0-1 (>= 0.6.4)"
.
I searched in Synaptic and tried installing the current version of libgssdp
but it was still unsatisfied. Any ideas?

Cheers.

---

### Post by istblacken on 2009-06-11
You shouldn't download those packages yourself, instead you should add the source to third party repositories and then run update and it will offer it to you as updates and also that way it will take care of the dependencies itself. 

Read more from here:
[https://help.launchpad.net/Packaging/PPA#Installing%20software%20from%20a%20PPA](https://help.launchpad.net/Packaging/PPA#Installing%20software%20from%20a%20PPA)

---

### Post by SergeantOreo on 2009-06-11
It worked. ^_^

Cheers to you!

---

### Post by Triphys on 2009-06-15
I had the same problem and tried your solution, unfortunately it didn't work for me. I get the following error upon amsn crashing when logging in:

```
*****@*****:~$ amsn

(<unknown>:10127): GLib-GObject-WARNING **: IA__g_object_set_valist: object class `GstGConfAudioSrc' has no property named `blocksize'
Segmentation fault
*****@*****:~$ 

```

---

