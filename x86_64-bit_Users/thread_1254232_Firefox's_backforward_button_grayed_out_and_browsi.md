---
title: "Firefox's back/forward button grayed out and browsing history is gone"
date: 2009-08-31
forum: x86 64-bit Users
---

### Post by speedup on 2009-08-31
Hi guys,

Can you help me solve my problem, I have the latest firefox version 3.0.13 installed on ubuntu 8.04 64-bit. I do not know what I did but the following capabilities are gone:
  a. back and forward is grayed out
  b. browsing history is gone when you click the drop down box
  c. bookmarks are gone
  d. opening firefox won't bring up the default startup page. 

Adding this information:

Even doing a manual bookmark on a certain website does not add the site in the bookmarks.

Thank you in advance.

---

### Post by themtx on 2009-08-31
Check perms and/or owenership of your user's ~/.mozilla dir?  Sounds like you can't write to/read from there.

---

### Post by philinux on 2009-08-31
This is a typical mozilla firefox profile problem.

[http://www.google.co.uk/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:unofficial&hs=gIs&ei=LSScSpu-MN6fjAeP5YzbDQ&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=mozilla+corrupt+profile&spell=1](http://www.google.co.uk/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:unofficial&hs=gIs&ei=LSScSpu-MN6fjAeP5YzbDQ&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=mozilla+corrupt+profile&spell=1)

Links within the past 12 months.
[http://www.google.co.uk/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=JfX&as_q=mozilla+corrupt+profile&as_epq=&as_oq=&as_eq=&num=10&lr=&as_filetype=&ft=i&as_sitesearch=&as_qdr=y&as_rights=&as_occt=any&cr=&as_nlo=&as_nhi=&safe=images](http://www.google.co.uk/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=JfX&as_q=mozilla+corrupt+profile&as_epq=&as_oq=&as_eq=&num=10&lr=&as_filetype=&ft=i&as_sitesearch=&as_qdr=y&as_rights=&as_occt=any&cr=&as_nlo=&as_nhi=&safe=images)

Also search these forums for similar.

---

### Post by speedup on 2009-08-31
@themtx and philinux

Thank you for your help it was indeed a permission problem. After I have checked and edit the permission it worked. Thank you so much again for your help guys

---

