---
title: "flash and 64bit"
date: 2005-02-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by AndersAA on 2005-02-10
I know flash doesn't work in 64bit, but it seems totem can play swf files... any way I can set the file asociation to have totem play it in firefox?

---

### Post by blinksilver on 2005-02-11
alot of the flash is embeded into the website, it is not something you download for you to setup file association with, sorry, but you gplflash, it crashs my Firefox, but hey, if you get it to work tell me how,

just grab it from synaptic, or if you perfer apt-get

---

### Post by Psy on 2005-02-11
gplflash works fine with my firefox using warty. I just did apt-get install swf-player (or something similar). So it is possible to get it to work.
It doesn't work that well tho. It will play most flash animations but it will not play them correctly. And forget interactive flash movies.  :?

---

### Post by blinksilver on 2005-02-11
well that is not gpl flash,  just search 'flash" in synaptic, it does not work, what you did installs is a different

but thanks at least some flash

---

### Post by kubla on 2005-03-01
[QUOTE=blinksilver]well that is not gpl flash,  just search 'flash" in synaptic, it does not work, what you did installs is a different

but thanks at least some flash[/QUOTE]

Gplflash, however, does compile and work quite well.

I've got it running now and at least it gives me the basics of Flash:

Shockwave Flash

    File name: libnpflash.so
    Flash Movie player Version 0.4.12 compatible with Shockwave Flash 4.0

    Shockwave is a trademark of Macromedia®

    GPLFLash homepage : gplflash.sf.net

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Flash Plugin 	swf 	Yes
application/x-futuresplash 	Future Splash 	spl 	Yes

It's also good to support another open source initiative rather than going on bended knee to Macromedia in the hope that they'll maybe someday release something for us.

[http://gplflash.sourceforge.net/](http://gplflash.sourceforge.net/)

---

### Post by blinksilver on 2005-03-01
will give it a shot

---

### Post by artimess on 2005-03-01
[QUOTE=kubla]
MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Flash Plugin 	swf 	Yes
application/x-futuresplash 	Future Splash 	spl 	Yes
[/QUOTE]
Could someone please tell me where and how to add these definitions.
Thanks.

Artimess

---

### Post by kubla on 2005-03-02
[QUOTE=artimess]Could someone please tell me where and how to add these definitions.
Thanks.
Artimess[/QUOTE]

The output I quoted was from putting about:plugins in the firefox address bar.

However, the key thing is to see what you have in your /usr/lib/mozilla-firefox/plugins/ directory.

Make sure that libnpflash.so goes in there if you're compiling the gplflash source.

Ian

---

