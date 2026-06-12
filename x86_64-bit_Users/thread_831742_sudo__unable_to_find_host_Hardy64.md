---
title: "sudo : unable to find host Hardy64"
date: 2008-06-17
forum: x86 64-bit Users
---

### Post by L1mit30 on 2008-06-17
Hello everyone,

I successfully installed the 64 bit Ubuntu 8.04 and i am very happy with it. But i think i did something but i cant remember. And now every tiime i want to use the sudo command i get the following error "sudo : unable to find host Hardy64" but after that it asks for the password and everything works. THe only thing is that every time i type sudo i get the error.
Does anyone knows why?

Thank you.

Sam

---

### Post by argail1980 on 2008-06-17
what is your computer name?

the config-file is /etc/sudoers. maybe that ominous host is mentioned there.

---

### Post by Nepherte on 2008-06-17
If it's "sudo: unable to resolve host" look in this thread for the solution: [http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

---

### Post by ddales on 2008-06-20
I had the same problem and had to adjust my /etc/hosts file to get it to work again.

###
127.0.0.1  localhost loopback
192.168.1.1  computername

---

