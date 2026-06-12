---
title: "msdl for 64 bit"
date: 2009-03-16
forum: x86 64-bit Users
---

### Post by niceguy123 on 2009-03-16
Can anyone help me install msdl on 8.10 64 bit.

Thanks,

---

### Post by cariboo on 2009-03-16
A little more information would help, What is msdl and can you include a link to the page.

Jim

---

### Post by sanderj on 2009-03-16
Do you mean the msdl "multi-protocol downloader for various streaming protocols" from [http://msdl.sourceforge.net/](http://msdl.sourceforge.net/)

If so, have followed the Install instruction on that web page? It does work for me on my 64-bit Ubuntu:

> 
  wget [http://downloads.sourceforge.net/msdl/msdl-1.2.3.tar.gz](http://downloads.sourceforge.net/msdl/msdl-1.2.3.tar.gz)
  tar xvzf msdl-1.2.3.tar.gz
  cd msdl-1.2.3/
  ./configure
  make
  sudo make install
  msdl


HTH

---

### Post by niceguy123 on 2009-03-24
> **sanderj said:**
> Do you mean the msdl "multi-protocol downloader for various streaming protocols" from [http://msdl.sourceforge.net/](http://msdl.sourceforge.net/)

If so, have followed the Install instruction on that web page? It does work for me on my 64-bit Ubuntu:



HTH

Worked like a charm.  Thanks a bunch. Do you have an idea how to download this type of stream [http://www.mako.co.il/news-channel2/Six-Newscast/Article-9c04b1606343021004.htm](http://www.mako.co.il/news-channel2/Six-Newscast/Article-9c04b1606343021004.htm)   ???  Its not happening in msdl

---

