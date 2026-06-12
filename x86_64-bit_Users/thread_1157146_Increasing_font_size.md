---
title: "Increasing font size?"
date: 2009-05-12
forum: x86 64-bit Users
---

### Post by dh003i on 2009-05-12
Simple question: I have a 2048x1536 main-display CRT...most text is too small. 

Where do I increase the DPI settings to make the fonts appear bigger? Thanks.

---

### Post by obdu on 2009-05-12
sudo nano /etc/X11/xorg.conf

Under the monitor-section. Mine works with "DisplaySize	367	275", with 1280x1024 19" CRT

---

### Post by philinux on 2009-05-12
System>prefa>appearance fonts tab and details for dpi.

---

