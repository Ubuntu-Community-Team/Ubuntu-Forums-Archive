---
title: "install netscape 9"
date: 2007-07-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by artv on 2007-07-01
Is it possible to install Netscape 9?  The download they provide for Linux doesn't work for me and  I don't even see a was to download the source on [http://browser.netscape.com/downloads/](http://browser.netscape.com/downloads/)

---

### Post by dabang on 2007-07-01
No problem at all:

```
sudo apt-get install ia32-libs ia32-libs-gtk
```

Then download the .tar.gz from here: [http://browser.netscape.com/]("http://browser.netscape.com/")

and unpack it to your home directory (or wherever you want) and run Netscape via:

```
/path/to/navigator/navigator
```

Have fun!

---

### Post by artv on 2007-07-01
Thanks.  It was the library info that I needed.

---

### Post by Adam_GUI on 2007-07-01
Does linux Netscape still have Netscape radio?
The radio function in Netscape was always a favorite of mine.  And I'd love to get it under linux.

Looked for Radio Plug-Ins.  One for Swedish WebRadio (I'm keeping it.  But I don't really understand what I'm doing.)
The best seems to be for Sirius Satellite Radio.  But you have to have an existing account.  :(

I miss a certain radio station that you used to be able to get though Netscape/AOL or Winamp/AOL radio.
But it seems that station was phased out.

---

### Post by artv on 2007-07-02
I don't know, but I don't see anything about it in the help or the menus.

---

### Post by tuesday20102001 on 2008-03-12
Browser locked upon me when running from command line. Worth noting you should check browser requirements here: [http://browser.netscape.com/sysreqs/](http://browser.netscape.com/sysreqs/)

It seems after installing: libxxf86misc-dev package, the browser worked.
I am not entirely sure if this is the same package requirement referred to in the link above.

---

