---
title: "OpenLDAP (slapd) server crashes on IA64"
date: 2006-06-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Hko on 2006-06-28
Hi,

We run Ubuntu 6.06 on an IA64 (Itanium) server. But **slapd** is crashing reproducibly when doing a search in a contianer (or at least an OU).

ldapsearch -x -b dc=example,dc=nl  #OK
ldapsearch -x -s base -b ou=People,dc=example,dc=nl #OK
ldapsearch -x -b ou=People,dc=example,dc=nl #CRASHES slapd, remote and local.

_Versions:_

slapd_2.2.26-5ubuntu2_ia64.deb
libdb4.2_4.2.52-24build1_ia64.deb

_Tried:_

**(1) Dump and restore:**
/etc/init.d/slapd stop
slapcat -l dump.ldif
rm /var/lib/ldap/*
slapadd -l dump.ldif
/etc/init.d/slapd start

**(2) Dump and restore (through the server):**
Similar to (1), but using ldapsearch/ldapadd instead of   slapcat/slapadd.

**(3) Logging:**
Setting "loglevel" to "-1" in slapd.conf, but no information about the crash found in the logs. Except for much shorter log-results than a succesful (ie. non-crashing) ldapsearch.

**(4) Almost-empty database:**
dn: dc=example,dc=nl
objectClass: top
objectClass: dcObject
objectClass: organization
o: Example
dc: example

dn: cn=admin,dc=example,dc=nl
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP Admin
userPassword:

dn: ou=People,dc=example,dc=nl
objectClass: top
objectClass: organizationalUnit
ou: People


If anybody has a useful idea to try, information on how to try to solve this, or an instant solution (that would be nice ;) ) it would be very much appreciated.

Thanks in advance.

---

### Post by Hko on 2006-10-26
Until now I worked around this problem by installing an old version (slapd_2.1.30-3ubuntu3.2_ia64.deb) and apt-pinning slapd to this version.

Today I installed the "normal" version again, just to see if I could figure out more about what is happening.

I did not manage to solve the problem, but these were the last lines of output from "strace":
```
shell# strace -f -F /usr/sbin/slapd -f /etc/ldap/slapd.conf
[..snip..]
5446  mmap(NULL, 65536, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2000000001804000
5446  write(10, "/usr/sbin/slapd -f /etc/ldap/sla"..., 41) = 41
5446  close(10)                         = 0
5446  munmap(0x2000000001804000, 65536) = 0
5446  mmap(NULL, 622592, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2000000001804000
5446  mmap(NULL, 4194304, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x200000000189c000
5446  mprotect(0x2000000001a98000, 16384, PROT_NONE) = 0
5446  clone2(child_stack=0x200000000189c000, stack_size=0x3febe0, flags=CLONE_VM|CLONE_FS|CLONE_FILES|CLONE_SIGHAND|CLONE_THRE
5446  futex(0x2000000001c9b310, FUTEX_WAIT, 5447, NULL <unfinished ...>
5447  --- SIGSEGV (Segmentation fault) @ 0 (0) ---

```

Did somebody experience the same problems, and knows how to solve it?

Or are there too few people running Ubuntu on an itanium machine?

Does this post belong somewhere else? (please tell me if so..)

I have no idea where to look for a solution. Does anyone have an idea how this could be solved please?

Thanks in advance.

   Heiko

---

