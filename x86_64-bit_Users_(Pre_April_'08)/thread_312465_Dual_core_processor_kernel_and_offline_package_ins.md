---
title: "Dual core processor kernel and offline package installs"
date: 2006-12-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by alyczak on 2006-12-04
I am doing the LAMP server install on a server with 2 AMD-opteron 64 bit dual core processors.  Will the install automatically use a kernel capable of taking advantage of the dual core processors?  Or should I install a separate kernel?  If I should install a separate kernel, how do I do it?

In my case, is there any reason for me to use Edgy instead of Dapper?

Is it possible to burn a CD with any extra Ubuntu packages I want to install (including a kernel) so that I can also install to servers not currently connected to the Internet?  If so, what files do I burn to the CD, and then how do I configure Ubuntu to look for the files on my CD rather than in an online repository?

---

### Post by hainesr on 2006-12-04
> **alyczak said:**
> I am doing the LAMP server install on a server with 2 AMD-opteron 64 bit dual core processors.  Will the install automatically use a kernel capable of taking advantage of the dual core processors?  Or should I install a separate kernel?  If I should install a separate kernel, how do I do it?

It will get it right! If you have a dual core an SMP kernel will be installed by default.

> **alyczak said:**
> In my case, is there any reason for me to use Edgy instead of Dapper?

Dapper has long-term support so will be updated with bugfixes and security fixes for longer than Edgy. I went for Edgy at home (I don't mind re-installing) and Dapper at work (I don't have time to re-install too often) and have been equally happy with both!

> **alyczak said:**
> Is it possible to burn a CD with any extra Ubuntu packages I want to install (including a kernel) so that I can also install to servers not currently connected to the Internet?  If so, what files do I burn to the CD, and then how do I configure Ubuntu to look for the files on my CD rather than in an online repository?

Here's where Dapper might have an advantage: You can download a DVD of the entire package set for Dapper so you would have pretty much all you need right there. I've not seen a DVD download for Edgy. You can tell Synaptic to treat a DVD as a repository via the options menu - if I remember correctly this was done automatically for me.

If you want to install other packages or some of the stuff in the "universe" that may not be on the DVD the best bet would be to download the things you want, then see what their dependencies are. I've looked and looked for how to do this and come up short. You can list the dependencies of an installed package:
```
apt-cache depends zip
```
But I can't see how to list the dependencies of a .deb file. It **must** be possible though - anyone have the answer? ](*,) 

Hope some of that was of some use...

Cheers,
Rob

---

### Post by alyczak on 2006-12-04
Thanks.  The only bad news is that the server doesn't have a DVD-ROM drive... just CD-ROM.  Is there a way I can burn selected packages to my own CD?

---

### Post by hainesr on 2006-12-04
If you mean burn them to a CD so it can be used as a repository; I'm sure there is but I'm not sure of the details. I've just had a quick look at my Edgy CD:
[LIST]Packages appear to be in directories pool/main and pool/restricted and then split up by first letter (ie. a, b, c, and so on).[/LIST]
[LIST]There seems to be quite a lot of important stuff in the dists directory, such as package lists and so on.[/LIST]
[LIST]There's plenty of other stuff on there that looks like it might be important, but I don't know what it does![/LIST]

You can install packages without using Synaptic: check out dpkg. If you don't have the dependencies it'll list what you need.

But if you can, I really would recommend installing via Synaptic via the web as you'll get all the latest versions and updates and so on.

Someone else may know more about this than me, of course!

Cheers,
Rob

---

