---
title: "can't use sudo anymore, help!!!!!"
date: 2006-01-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by ewok on 2006-01-17
i dunno what happend (ok i do i just don't know how to fix it)

now when i log in the error comes up can't log into localhost "."
says i have to edit /etc/hosts

i can't use sudo anymore.... it tried su, apparently not the same password. i think i deleted my self from my network? in term it shows are ewok@~: vs. ewok@ewok: (this one is the good one!!!) help

how can i fix this, i am still a noob so make it easy for me, please.

---

### Post by darth_vector on 2006-01-17
you will have to log into single user mode. you can do this through the grub menu on startup (press escape on startup if you have a hidden menu).

you will now have a root shell. open /etc/hosts in a text editor - only editors like nano and vim will work - and make sure there is a line like:

127.0.0.1      localhost.localdomain    localhost     computername

where computername is the name of your computer (ubuntu by default, i think).

restart your machine with ```
shutdown -r now
``` and that should do it

---

