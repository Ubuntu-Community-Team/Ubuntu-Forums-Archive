---
title: "Can't install wine 0.58 :("
date: 2008-05-08
forum: Wine
---

### Post by creeco on 2008-05-08
I can't seem to get wine version 0.58 to install on gutsy. I downloaded the .deb manually from "Wine HQ" but whenever i try to install it with gdebi it gives me this: error: Dependency is not satisfiable: libldap2

Please help me out...

---

### Post by pedro_orange on 2008-05-08
> **creeco said:**
> I can't seem to get wine version 0.58 to install on gutsy. I downloaded the .deb manually from "Wine HQ" but whenever i try to install it with gdebi it gives me this: error: Dependency is not satisfiable: libldap2

Please help me out...

Seems like you're missing the LDAP dev libs.
```

pedro@pedro-laptop:~$ apt-cache search libldap2
libldap2-dev - OpenLDAP development libraries
pedro@pedro-laptop:~$ 

```

Could go with an old fashioned:

```
sudo apt-get install libldap2
```

---

### Post by ajackson on 2008-05-08
> **creeco said:**
> whenever i try to install it with gdebi it gives me this: error: Dependency is not satisfiable: libldap2
Have you tried installing libldap2? Or is it asking for a version higher than the one available?

---

### Post by creeco on 2008-05-08
> **ajackson said:**
> Have you tried installing libldap2? Or is it asking for a version higher than the one available?
I installed "slapd libldap-2.4-2" instead of libldap2 because it said that libldap2 couldn't be installed... I also installed binfmt-support, but i am still getting the same error

---

### Post by pedro_orange on 2008-05-08
So you've installed the LDAP server? 

If its moaning about the LDAP-dev files; surely you should install them.
Can you still not install these? 

Is there anything in particular you want this version for? Is the version in the repos unacceptable?

---

### Post by creeco on 2008-05-08
> **pedro_orange said:**
> So you've installed the LDAP server? 

If its moaning about the LDAP-dev files; surely you should install them.
Can you still not install these? 

Is there anything in particular you want this version for? Is the version in the repos unacceptable?
You mean the OpenLDAP development libraries? Because i have them installed..

For some reason wine versions after 0.58 wont run msoffice07.. So i really need 0.58.

---

