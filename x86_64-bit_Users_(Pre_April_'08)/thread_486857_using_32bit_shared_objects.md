---
title: "using 32bit shared objects ?"
date: 2007-06-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by kzm. on 2007-06-28
is there anyway to use 32bit shared objects in a 64bit install? 
i dont have access to the source code. i am not sure if this is a logical question, so excuse me, if its sounds stupid.

---

### Post by kzm. on 2007-06-28
i dont want to sound rude, but i am really looking for an answer, so excuse me the question, but does anybody may be suggest some other 'debian' forum, where i might find info about this issue?

---

### Post by RAOF on 2007-06-28
1) You should probably wait more than 3 hours before posting a second "please help" post.  The forums are not a good source of instant-gratification-help :).

2) Yes, you can.  32bit code will run just fine under a 64bit Ubuntu install.  However, you can't link 64bit code to 32bit code or visa versa, so your 32bit program will either need to be self-contained, or you'll need some of the **ia32libs** pacakges.

---

### Post by kzm. on 2007-06-29
@raof, i posted it under a different [topic]("http://ubuntuforums.org/showthread.php?t=485776")... thats may be why i sounded inpatient.. i know its not an instant response thing.

but from what you say, i understand its possible. i tested the *.so with the ldd command and every dependicy was good, but still it refuse to load because of some 32bit error:
```
wrong ELF class: ELFCLASS32
```

so i guess it cant load it because its 32bit, right?

---

### Post by Kilz on 2007-06-29
> **kzm. said:**
> @raof, i posted it under a different [topic]("http://ubuntuforums.org/showthread.php?t=485776")... thats may be why i sounded inpatient.. i know its not an instant response thing.

but from what you say, i understand its possible. i tested the *.so with the ldd command and every dependicy was good, but still it refuse to load because of some 32bit error:
```
wrong ELF class: ELFCLASS32
```

so i guess it cant load it because its 32bit, right?

Do you have the linux32 and ia32 packages installed?

---

### Post by kzm. on 2007-06-29
> Do you have the linux32 and ia32 packages installed?

yup. i do:

```
linux32
usage: linux32 [--3gb] [--4gb] program args ...
```

```
sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

i guess, thats why the ldd solves, right?

```
linux-gate.so.1 => (0xffffe000)
libc.so.6 => /lib32/libc.so.6 (0xf7e39000)
/lib/ld-linux.so.2 (0x56555000)
```

---

### Post by Kilz on 2007-06-29
> **kzm. said:**
> yup. i do:

```
linux32
usage: linux32 [--3gb] [--4gb] program args ...
```

```
sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

i guess, thats why the ldd solves, right?

```
linux-gate.so.1 => (0xffffe000)
libc.so.6 => /lib32/libc.so.6 (0xf7e39000)
/lib/ld-linux.so.2 (0x56555000)
```

Is ldd 64bit , and your using it to test a 32bit library? Wont work , you cant mix 64 and 32bit. Exactly what 32bit applications are you trying to use?

---

### Post by kzm. on 2007-06-30
its an apache module... but my server is 64bit (may be i should reinstall it.. hmm). thanx for the comments, though

---

### Post by Kilz on 2007-06-30
> **kzm. said:**
> its an apache module... but my server is 64bit (may be i should reinstall it.. hmm). thanx for the comments, though

Why not compile the module for the server you have now?

---

### Post by kzm. on 2007-06-30
dam.. i would love to, but i dont have the source code. the module is free but there is no source code.. at least not on the site where you get the module.. may be i should do some more indeep googeling. but its focusing more on windows servers or even osx! the module existed first those systems... beat me why.

---

### Post by RAOF on 2007-07-01
> **kzm. said:**
> its an apache module... but my server is 64bit (may be i should reinstall it.. hmm). thanx for the comments, though

Ah, so the question was actually "is it possible to use a 32bit library as a 64bit apache module" :).  The answer to **that** question is "no, you can't mix 32- & 64-bit code".

---

