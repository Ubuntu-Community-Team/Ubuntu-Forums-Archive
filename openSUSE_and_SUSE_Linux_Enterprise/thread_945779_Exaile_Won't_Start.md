---
title: "Exaile Won't Start"
date: 2008-10-12
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Vince4Amy on 2008-10-12
I have just installed the GTK media player Exaile on my OpenSUSE 11 KDE 3.5 system and when I try to launch it nothing appears, when I run it through the command line I get the following error:

```
python: symbol lookup error: /usr/lib64/python2.5/site-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_parse_flags_get_type
```

---

### Post by RedDwarf on 2008-10-12
Output from
```
$ rpm -qif /usr/lib64/python2.5/site-packages/gst-0.10/gst/_gst.so
$ rpm -qif /usr/lib64/libgstreamer-0.10.so.0
$ nm -D /usr/lib64/libgstreamer-0.10.so.0 | grep gst_parse_flags_get_type
```
?

---

