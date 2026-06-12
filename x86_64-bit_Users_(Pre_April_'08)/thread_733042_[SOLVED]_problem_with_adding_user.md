---
title: "[SOLVED] problem with adding user"
date: 2008-03-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by famous3warriors on 2008-03-23
I am using Ubuntu Studio x86 64 bit 7.10.  I added a user useing manage user groups and gave that person full admin rights.  This is what he gets on his desktop.  He cannot manage compiz fusion either.  Please help.  Thanks!

---

### Post by Oldsoldier2003 on 2008-03-24
> **famous3warriors said:**
> I am using Ubuntu Studio x86 64 bit 7.10.  I added a user useing manage user groups and gave that person full admin rights.  This is what he gets on his desktop.  He cannot manage compiz fusion either.  Please help.  Thanks!

check to make sure that user is part of the admin group. post the output of the following command replacing 'username' with the account that you created:
```

id username
```

this will show us what groups the user is in, and well help us get you sorted

---

### Post by famous3warriors on 2008-03-24
I found the problem I did not enable the appearance settings correctly.  My fault.  Thanks for your help.  I really do appreciate your time.

---

