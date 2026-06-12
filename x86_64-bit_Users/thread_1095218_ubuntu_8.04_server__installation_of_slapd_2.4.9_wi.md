---
title: "ubuntu 8.04 server : installation of slapd 2.4.9 with libdb4.6"
date: 2009-03-13
forum: x86 64-bit Users
---

### Post by Fida_jou on 2009-03-13
Hi 

Hope i'm in the right forum 

I want to install slapd 2.4.9 with libdb4.6. The problem is that the default package found on ubuntu 8.04 is depended on libdb4.2. 
I want to re-package this binary to have the right dependency. 

How can i do that ? 

Thank you

---

### Post by Thelasko on 2009-03-13
I don't recommend doing that.  The reason those packages are in the repositories is to ensure your system is stable.  When you start playing around with dependencies like this, bad things happen.

P.S. Why do you want to do this?

---

