---
title: "Wine and Scrivener Help :)"
date: 2019-10-27
forum: Wine
---

### Post by punk1977 on 2019-10-27
Hi All,

First of all thank you fro reading my post. Im very new to ubuntu so please be gentle with me. 
I am running a writing app named scrivener in wine and for the most part everything is fine. I have PDFs and word docs on my ubuntu C: drive (or what ever its called on ubuntu) and I can't import them into scrivener. Any ideas what I might be doing wrong?

Thanks for you time in advance

Matt

---

### Post by zimbuf on 2019-10-27
The default wine prefix for Ubuntu exports your root filesystem to Z:\ for applications running in wine. Accordingly, your files should be in Z:\home\<your login name>. Do you see anything after searching through there?

---

### Post by mastablasta on 2019-10-30
what do you mean you can't import them? you can't locate the file?

wine prefixes are hidden by default. you can "unhide" hidden files in nautilus. anyway files likely need to be there. you should find the familiar (well for windows people) "my documents" in there and other things.

---

