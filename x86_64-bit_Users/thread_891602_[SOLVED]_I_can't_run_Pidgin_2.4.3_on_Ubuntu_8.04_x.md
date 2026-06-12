---
title: "[SOLVED] I can't run Pidgin 2.4.3 on Ubuntu 8.04 x86_64"
date: 2008-08-16
forum: x86 64-bit Users
---

### Post by congminh1709 on 2008-08-16
Hello everybody, i am using Ubuntu 8.04 x86_64 version with Pidgin 2.4.3 included. It often runs well, but today i can't run pidgin, when i run it from Applications -> Internet -> Pidgin Internet Messenger, it appears "Starting Pidgin ..." and stops at here.

[IMG]http://img110.imageshack.us/img110/6636/pid2el3.png[/IMG]

I removed Pidgin and then reinstalled it, but can't fix this error? Why?

Thank for reading my post.

---

### Post by y-lee on 2008-08-16
If you start Pidgin in a terminal do you get any error messages?

---

### Post by congminh1709 on 2008-08-16
When run *pidgin* from the terminal, nothing appears although pidgin was installed.

---

### Post by y-lee on 2008-08-16
Ok, I see.

Pidgin keeps a hidden folder in your home directory called .purple.  Try deleting this folder or renaming it so that pidgin has to recreate it when it starts. Sometimes a corrupt file in this folder causes problems. BTW this is just a guess because I am not sure at all.

---

### Post by congminh1709 on 2008-08-16
I showed hidden files and folders to search but i can't see *.purple* folder? Only have

[I]/etc/purple
/usr/share/pixmaps/purple
/usr/share/sounds/purple
/usr/lib/perl5/auto/purple
/usr/lib/purple[/I]

Any comments for this problem? Thanks.

---

### Post by dje on 2008-08-16
run this in the terminal (applications >> accessories >> terminal):
```
mv $HOME/.purple $HOME/.purple.bak
```

dje

---

### Post by congminh1709 on 2008-08-16
Ok, thank you so much, i did it. Pidgin rus well now ^^

---

### Post by y-lee on 2008-08-16
dje's command above should work. It is in your home folder. good luck.

---

### Post by ptn107 on 2008-08-16
try this command in a terminal:
rm -rf /home/$USER/.purple/

---

### Post by y-lee on 2008-08-16
> **congminh1709 said:**
> Ok, thank you so much, i did it. Pidgin rus well now ^^

Ah cool. you can mark your thread as solved now. It helps make the forums easier to use, click on thread tools above.

---

### Post by dje on 2008-08-16
> **congminh1709 said:**
> Ok, thank you so much, i did it. Pidgin rus well now ^^

in that case run this (to remove the backup of the old pidgin settings folder):
```
rm -rf $HOME/.purple.bak
```

dje

---

### Post by congminh1709 on 2008-08-17
> **y-lee said:**
> Ah cool. you can mark your thread as solved now. It helps make the forums easier to use, click on thread tools above.
OK, i did it again.

---

### Post by yuhan on 2008-09-14
i have the same problem after installing from the pidgin2.5.1 source code now it can't run and stops at the same place, i tried all the solutions given above but it still doesn't work.
by the way i m on the i386 platform
can anyone help me?

---

