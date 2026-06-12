---
title: "novel client"
date: 2009-05-21
forum: Za Team - South Africa
---

### Post by cjfisrt on 2009-05-21
Good day

I am looking for advice on authentication from ubuntu 9.04 to novell edir server.....

I need my ubuntu users to do that so that they can change there groupwise passwords on the edir system and also get notifications on password's grace loggins....

Can some one local help?

Cheers
C:popcorn:

---

### Post by stefanor on 2009-05-22
Authentication is relatively easy, you can just use the edir server for authentication via libpam_ldap.

If you want to store your user accounts in edir too, you'll need to enable UIDs on the edir server so that each user has a suitable linux-friendly UID. Then you can use libnss_ldap

---

