---
title: "install wine in edgy 64-bit"
date: 2006-11-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by myname on 2006-11-01
Hello all.

I finally made the move to Edgy 64-bit yesterday, went from Dapper 32 to Edgy 64.  Tinkered around and got the ATI drivers to recognize themselves as ATI and not MESA, with the glxgears speeds the same as they were in Dapper.

Now my next challenge, is to get Wine running in Edgy 64-bit.  Has anyone done this yet?  Can they post directions?  I am a fairly new Ubuntu user, and not that familiar with tinkering with things to get them to work, as I hate to re-install if I muck something up.

If someone could point me to an article (i've searched but only found them for Dapper, or non 64-bit), that would be great.

I look forward to getting wine up and running so I can get back to WoW.

--Kevin

---

### Post by IanW on 2006-11-01
AFAIK Wine uses certain 32-bit libraries, so cannot currently be compiled as a native 64-bit application.
(Of course, I would _love_ to be wrong about this!)

---

### Post by RoyArne on 2006-11-01
> **IanW said:**
> AFAIK Wine uses certain 32-bit libraries, so cannot currently be compiled as a native 64-bit application.
(Of course, I would _love_ to be wrong about this!)

Wine can be built on 64-bit platforms. I followed the instructions [here]("http://wiki.winehq.org/WineOn64bit") to install wine on dapper. It took some time though, and you will have to install a lot of development libraries to get it running. 

I have not tried to install it on Edgy yet, and unfortunately I don't remember the package names. If you want to give it a try, you will have to examine the output of ./configure closely, and install all of the required libraries.

---

### Post by uniko on 2006-11-01
Or you could just use the 32-bit wine package and install it. Download the .deb from packages.ubuntu.com and install it:

sudo dpkg -i --force-architecture wine-package.deb

Sure it's not pretty but it works, for me at least. On the plus side, if it doesn't work for you, it can be uninstalled easily using 

sudo dkpg -r wine

---

### Post by Kilz on 2006-11-01
The Dapper 32bit wine howto works on Edgy. Link in my signature.

---

