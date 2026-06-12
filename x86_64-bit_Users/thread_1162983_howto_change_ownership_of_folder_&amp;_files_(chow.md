---
title: "howto change ownership of folder &amp; files? (chown not working)"
date: 2009-05-18
forum: x86 64-bit Users
---

### Post by dh003i on 2009-05-18
Hi all,

I want to change the ownership of a set of folders and the files within recursively. However, the chown command isn't working:

```
$ chown -R davidjheinrich ./Documents/
chown: changing ownership of `./Documents/Computer/xrandr script.txt~': Operation not permitted
chown: changing ownership of `./Documents/Computer/VP2290b-3 User Guide English.pdf': Operation not permitted
chown: changing ownership of `./Documents/Computer/IRC chat - resolution 2048x1536': Operation not permitted
chown: changing ownership of `./Documents/Computer/xrandr.txt': Operation not permitted
chown: changing ownership of `./Documents/Computer/xrandr-verbose.txt': Operation not permitted
chown: changing ownership of `./Documents/Computer/xrandr script.txt.bak': Operation not permitted
chown: changing ownership of `./Documents/Computer/xrandr script.txt': Operation not permitted
chown: changing ownership of `./Documents/Computer/Xorg.0.log': Operation not permitted
chown: changing ownership of `./Documents/Computer/Sony Gdm f520 Repair Manual.pdf': Operation not permitted
chown: changing ownership of `./Documents/Computer': Operation not permitted
chown: changing ownership of `./Documents/': Operation not permitted

```

Doesn't do anything to the file's ownership.

---

### Post by jbruced on 2009-05-18
Need to sudo?

---

### Post by bruno9779 on 2009-05-18
have you tried with sudo?

```
sudo chown -R davidjheinrich ./Documents/
```

---

### Post by dh003i on 2009-05-19
> **bruno9779 said:**
> have you tried with sudo?

```
sudo chown -R davidjheinrich ./Documents/
```

Sorry, I used sudo in it as well. It gives up output, and when I type "ls -l" again, the file is still not owned by me.

---

### Post by _Purple_ on 2009-05-19
Have you tried using the full path?

```
sudo chown -R davidjheinrich /home/*user*/Documents
```

---

### Post by dh003i on 2009-05-19
> **_Purple_ said:**
> Have you tried using the full path?

```
sudo chown -R davidjheinrich /home/*user*/Documents
```

Thanks a lot, that worked. Typing in the following produces the following:

> $ sudo chown -R davidjheinrich /home/davidjheinrich/Music/
[sudo] password for davidjheinrich:
$ ls -l
total 60
drwxr-xr-x 3 davidjheinrich dh003i 4096 2009-05-12 08:02 Avril Lavigne

My two users are obviously davidjheinrich and dh003i. What does this result mean? (i.e., davidjheinrich dh003i)

---

### Post by Slim Odds on 2009-05-19
> **dh003i said:**
> My two users are obviously davidjheinrich and dh003i. What does this result mean? (i.e., davidjheinrich dh003i)

The first is user ownership the other is group ownership

---

### Post by Yellow Pasque on 2009-05-20
```
sudo chown -R davidjheinrich:davidjheinrich /home/davidjheinrich/Music/
```

---

### Post by dh003i on 2009-05-20
Thanks all.

---

