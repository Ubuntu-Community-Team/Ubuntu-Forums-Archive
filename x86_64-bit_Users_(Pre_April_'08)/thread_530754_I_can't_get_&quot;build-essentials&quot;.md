---
title: "I can't get &quot;build-essentials&quot;"
date: 2007-08-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by jns-nun on 2007-08-20
i can't take build-essentials to my PC, i don't know what happen.
my kernel is 2.6.15-28-386, and this is the out:
x@x-desktop:~$ sudo apt-get install build-essentials
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
E: No se pudo encontrar el paquete build-essentials

Sombody can help me?

---

### Post by BobCFC on 2007-08-20
Try build-essential without the S

It got me recently I don't know why the difference.. maybe 32-64bit thing?

---

### Post by John.Michael.Kane on 2007-08-21
> **jns-nun said:**
> i can't take build-essentials to my PC, i don't know what happen.
my kernel is 2.6.15-28-386, and this is the out:
x@x-desktop:~$ sudo apt-get install build-essentials
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
E: No se pudo encontrar el paquete build-essentials

Sombody can help me?

To install build-essential

Type the below command inside your terminal

```
gksudo aptitude install build-essential
```

---

### Post by bharadwaj on 2008-03-31
> **John.Michael.Kane said:**
> To install build-essential

Type the below command inside your terminal

```
gksudo aptitude install build-essential
```

Hey! that worked perfectly...but I just can't figure out why this thing din't work when I tried installing it from apt-get..it was showing me error that the package was available in other sources..may be that could be the reason...
and as far as I know gksudo is only used for loading graphical based apps..

---

### Post by Sam324 on 2008-06-20
The command didn't work for me.  Halfway through it gave me
```
Couldn't find any package whose name or description matched "build-essential"
Couldn't find any package whose name or description matched "build-essential"
```

---

### Post by Ducksgoquak on 2008-07-11
Hmm same problem for me... anyone know the solution?

---

### Post by sam_delta on 2008-07-13
try installing from the cd

insert ubuntu CD then type
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```

sam

---

