---
title: "Wine 0.9.53 released"
date: 2008-01-11
forum: Wine
---

### Post by Melhisedek on 2008-01-11
Get it while it is still hot :)

[http://www.winehq.org/?announce=0.9.53](http://www.winehq.org/?announce=0.9.53)

---

### Post by hikaricore on 2008-01-11
5 bucks says the next post after mine whines that there is no debian/ubuntu package yet.

---

### Post by happyhamster on 2008-01-11
So, who gets the 5 bucks? :P

---

### Post by hikaricore on 2008-01-11
me ^_^

---

### Post by sYnOnYx on 2008-01-12
> **hikaricore said:**
> 5 bucks says the next post after mine whines that there is no debian/ubuntu package yet.

this doesnt work with ubuntu ?

---

### Post by Fred_E _krugar on 2008-01-12
> **sYnOnYx said:**
> this doesnt work with ubuntu ?
:lolflag:

---

### Post by hikaricore on 2008-01-12
[IMG]http://img242.imageshack.us/img242/4424/ohoq9.jpg[/IMG]

---

### Post by sYnOnYx on 2008-01-12
> **Fred_E _krugar said:**
> :lolflag:

well doesnt work for me .........

---

### Post by Faud on 2008-01-12
haha

cd /www.ubuntu.com/forums/wine
cd/www.ubuntu.com/forums/wine$: ./configure
cd/www.ubuntu.com/forums/wine$: sudo apt-get install <missing file>
cd/www.ubuntu.com/forums/wine$:./configure
cd/www.ubuntu.com/forums/wine$: make
.
.
.
Im so waiing for it in the repos...this is just not working out.

:lolflag:

---

### Post by karth on 2008-01-12
well... it is in the repos already...

---

### Post by Sockerdrickan on 2008-01-12
> **Fred_E _krugar said:**
> :lolflag:

:lolflag:

---

### Post by mikerduffy on 2008-01-12
Enable the multiverse, and you'll have it.

---

### Post by hikaricore on 2008-01-12
> **mikerduffy said:**
> Enable the multiverse, and you'll have it.

false.

you'll have a very outdated version from the multiverse.

---

### Post by Cochise on 2008-01-12
add the winehq repo's and you get it fairly quickly

Heres a guide to add them:

[http://ubuntuforums.org/showthread.php?t=624644](http://ubuntuforums.org/showthread.php?t=624644)

---

### Post by b0rka7a on 2008-01-12
Or download the .deb and install it.
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by YokoZar on 2008-01-12
> **Faud said:**
> haha

cd /www.ubuntu.com/forums/wine
cd/www.ubuntu.com/forums/wine$: ./configure
cd/www.ubuntu.com/forums/wine$: sudo apt-get install <missing file>
cd/www.ubuntu.com/forums/wine$:./configure
cd/www.ubuntu.com/forums/wine$: make
.
.
.
Im so waiing for it in the repos...this is just not working out.

:lolflag:
apt-get build-dep wine will give you most of what you need.

---

### Post by Sockerdrickan on 2008-01-13
What else do I need to build 0.9.53 do you think

---

### Post by Faud on 2008-01-13
> **YokoZar said:**
> apt-get build-dep wine will give you most of what you need.
Sorry that was my poor attempt at a joke

---

### Post by Faud on 2008-01-13
> **Tux0r said:**
> What else do I need to build 0.9.53 do you think

Its in the repos allready

```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -

```
and for Gusty
```

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list

```
then
```

sudo apt-get update

```
```

sudo apt-get install wine

```

---

### Post by Sockerdrickan on 2008-01-13
No it's still [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) 0.9.52

---

### Post by b0rka7a on 2008-01-13
Tux0r, look again ;)

---

### Post by Sockerdrickan on 2008-01-13
I beat them by a few hours! muhaha :D

---

