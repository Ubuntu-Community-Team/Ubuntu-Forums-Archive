---
title: "MS Project 03 (and IE rendering)"
date: 2008-05-15
forum: Wine
---

### Post by quanumphaze on 2008-05-15
Finally MS Project works in Wine 1.0rc1 ... sorta

Everything seems fine except that it uses IE for rendering stuff. I installed the Gecko engine but it seems that I have to identify "gbui://mainpage.htm" as a trusted site in Internet explorer.

I just don't know how to get the IE settings dialog box up to see if Gecko even works with it.

Screenie of the error box included

---

### Post by quanumphaze on 2008-05-24
Bump :(

---

### Post by cogadh on 2008-05-24
Gecko is just a raw HTML rendering engine, it is not actually a browser, nor is it really configurable like Internet Explorer. You might want to try [IEs4Linux](http://www.tatanka.com.br/ies4linux/page/Main_Page) to see if that will do what you need.

---

### Post by quanumphaze on 2008-05-24
After installing IEs4Linux and putting gbui://mainpage.htm into trusted zone MS Project still gives me that error to put gbui://mainpage.htm into the trusted zone.

One step closer :).

---

### Post by quanumphaze on 2008-05-24
It seems that the IEs4Linux installer doesn't install IE6 into the ~/.wine/ directory and instead installs to ~/.ies4linux/ie6/

How would I go about installing it into ~/.wine so the settings can be used by MS Project?

---

