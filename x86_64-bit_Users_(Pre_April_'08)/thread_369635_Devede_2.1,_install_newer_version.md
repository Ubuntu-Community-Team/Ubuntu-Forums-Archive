---
title: "Devede 2.1, install newer version?"
date: 2007-02-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by JimmyME on 2007-02-24
I found Devede 2.11 at [www.getdeb.net](www.getdeb.net) and it installed fine in 6.10 64 bit and does exactly what I need.

In a previous Distro I was using KINO to capture digital video and exporting it as DVD ready mpeg and then used Devede with the option "Allows to specify that a file is already a DVD-compliant MPEG-PS file, so it won't be recompresed, but stored "as is" into the disc (usefull when you capture video from a TV capturer of other sources)." 

This prevented Devede from recompressing the file which allowed it to create the ISO much faster and with better quality than I can now do with Devede version 2.1.  The above feature started in Devede 2.4

Devede is now up 2.11.  Is there a way for me to download the latest Devede and install it in Ubuntu 6.10 64 AMD?

Thanks much,

Jim

---

### Post by dfreer on 2007-02-24
Don't know if this will work for you as I haven't tested this on a vanilla AMD64 install. But the program downloads and installs for me with this method (although I didn't see the option you were describing... it IS devede version 2.11 though):

```
wget -c http://www.rastersoft.com/descargas/devede-2.11.tar.bz2
tar xvzf devede-2.11.tar.bz2
cd devede-2.11
sudo ./install.sh
devede
```

Once again, I do have 32-bit libs installed, that may explain why this works for me. Good Luck!

---

### Post by JimmyME on 2007-02-25
Don't know if this will work for you as I haven't tested this on a vanilla AMD64 install. But the program downloads and installs for me with this method (although I didn't see the option you were describing... it IS devede version 2.11 though):


Code:
wget -c [http://www.rastersoft.com/descargas/devede-2.11.tar.bz2](http://www.rastersoft.com/descargas/devede-2.11.tar.bz2)
tar xvzf devede-2.11.tar.bz2
cd devede-2.11
sudo ./install.sh
devedeOnce again, I do have 32-bit libs installed, that may explain why this works for me. Good Luck!

Defreer,

Thanks for the reply.  The option I'm talking about is under the misc. tab and it allowed me to create the DVD ISO in about 6 minutes from my DVD ready mpeg out of KINO.  The quality was also great.  With Devede 2.1 it didn't have this option and it recompressed the video which made it look pretty bad.

I got 2.11 from [www.getdeb.net](www.getdeb.net) and it installed fine in 64 bit.

Best wishes,

JimmyME

---

### Post by Corbelius on 2007-02-28
Or install newer version :)

[http://janvitus.interfree.it/ubuntu/pool/edgy-janvitus/main-amd64/devede_2.12-1ubuntu1~janvitus_all.deb](http://janvitus.interfree.it/ubuntu/pool/edgy-janvitus/main-amd64/devede_2.12-1ubuntu1~janvitus_all.deb)

---

