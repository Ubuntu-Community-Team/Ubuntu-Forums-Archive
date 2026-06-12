---
title: "Tapioca VoIP packages for AMD64"
date: 2006-06-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by jbrnd on 2006-06-16
I looked around for AMD64 packages for the Tapioca VoIP client but couldn't find any, so I built my own (for Dapper).

Just in case they might be useful for someone, I've put up a tarball of them at [http://nullinfinity.org/tapioca_debs.tar](http://nullinfinity.org/tapioca_debs.tar) . To use them:

1. Download the file.
2. In a suitable directory, extract the contents with "tar xf tapioca_debs.tar"
3. Do "sudo dpkg -i *.deb" to install all the packages. This will also get you some development packages, but they're not very big.
4. That's it.

If you get some dependency errors in the dpkg step, install the packages that dpkg complains about.

Enjoy!

- Johan

---

### Post by jbrnd on 2006-06-16
I also built some debs for Landell, which is a nicer UI than the original Tapioca interface. That's available as [http://nullinfinity.org/landell_debs.tar](http://nullinfinity.org/landell_debs.tar) , installation procedure as above.

---

### Post by ntgooroo on 2006-09-14
This Tapioca AMD64 package installs just fine with no errors.

I can chat with it with out any problems.

However, when I initiate or receive and voice call, it hangs up the instant I hit accept, or the other party hits accept.


Also, Landell complains about some lib?????-sharp dependency, yet it appears to be installed on my PC already.

I would try installing both of these from source, but I am a newbie and people often forget there are still newbies out there and they do not provide detailed instructions on how to do it.

---

### Post by katana2k on 2006-10-13
does anyone know how to get landell for edgy 32bit?

---

