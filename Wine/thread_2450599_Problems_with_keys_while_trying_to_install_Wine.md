---
title: "Problems with keys while trying to install Wine"
date: 2020-09-17
forum: Wine
---

### Post by nicckog2000 on 2020-09-17
Hi I'm very new with ubuntu and don't have much experience with computers in general. I'm trying to install the last version of Wine in Ubuntu 18.04, but I have this issue (sorry that it's in Spanish): 

```
nicolas@nicolas-RF510-RF410-RF710:~$ sudo apt-key add winehq.key
[sudo] contraseña para nicolas: 
gpg: invalid key resource URL '/etc/apt/trusted.gpg.d/home:stevenpusser.gpg'
gpg: recurso de bloque de claves '(null)': Error general
gpg: key 7721F63BD38B4796: 2 firmas no comprobadas por falta de claves
gpg: key 51F523511C7028C3: 1 firma no comprobada por falta de una clave
gpg: key 0FAD31CA8719FCE4: 1 firma no comprobada por falta de una clave
gpg: key 3B4FE6ACC0B21F32: 3 firmas no comprobadas por falta de claves
gpg: key D94AA3F0EFE21092: 3 firmas no comprobadas por falta de claves
gpg: key 871920D1991BC93C: 1 firma no comprobada por falta de una clave
gpg: key 76F1A20FF987672F: 1 firma no comprobada por falta de una clave
gpg: Cantidad total procesada: 12
gpg:       omitidas nuevas claves: 12

```
Could anyone help me to solve this please? Thanks

---

### Post by TheFu on 2020-09-17
First, let's ensure everything on the machine is 100% patched.
```
sudo apt update && sudo apt full-upgrade
sudo reboot  # only if necessary
```
Copy and paste each of those commands, in order. If there is any error, stop. Do not continue. You say you are new, so I don't want to assume anything.  Those commands should be run once a week. Also, please make weekly backups of anything you don't want to lose. That's a very different thread. Storage is going to fail. Hopefully, it will fail after we don't need it anymore, but we never know. A friend had a new, named-brand SSD that he got new in June fail last week. It failed hard. No access at all was possible.

I don't know anything about WINE, but found this: [https://www.winehq.org/pipermail/wine-devel/2017-March/117104.html](https://www.winehq.org/pipermail/wine-devel/2017-March/117104.html)
> We already added the new Ubuntu repository to the CDN, so that users can
start switching by now and don't have to wait till the next release. The
repository can be added using the following commands:

```
wget [https://dl.winehq.org/wine-builds/Release.key](https://dl.winehq.org/wine-builds/Release.key)
sudo apt-key add Release.key
sudo apt-add-repository 'https://dl.winehq.org/wine-builds/ubuntu/'
```
Copy and paste each of those commands, in order. If there is any error, stop. Do not continue.

Then you can run 
```
sudo apt install wine
```

That will install ... wine v5.0-3ubuntu1 on a 20.04 Ubuntu desktop. This will be a 64-bit version, which may or may not be what you need. Depends on what you hope to install under WINE.  You may want the _wine32_ package instead.

Some of these steps are preventative.  If anything creates warnings or errors, DO NOT CONTINUE. STOP. Post the exact command and output, wrapped in code tags, as I've done above.  We need code tags so it is readable. We are used to seeing it that way. Quote tags don't help.

---

### Post by mastablasta on 2020-09-18
there is also wine developer version in repositories.

i found that wine-staging is usually enough, unless you have some special cases or you would like to test it or develop it.

> [COLOR=#000000][FONT=&quot]Wine Staging is the testing area of winehq.org. It contains bug fixes and features, which have not been integrated into the development branch yet. The idea of Wine Staging is to provide experimental features faster to end users and to give developers the possibility to discuss and improve their patches before they are integrated into the main branch.
[/FONT][/COLOR][COLOR=#000000][FONT=&quot]Wine Staging is maintained as a set of patches[/FONT][/COLOR][COLOR=#000000][FONT=&quot] which has to be applied on top of the corresponding Wine development version. Package maintainers can decide if they want to include our full patchset, or only want to cherry-pick patches for specific bugs.[/FONT][/COLOR]

---

### Post by deadflowr on 2020-09-19
> gpg: invalid key resource URL '/etc/apt/trusted.gpg.d/home:stevenpusser.gpg'
This key seems to be breaking everything.
Removing that key should get things back, though you'll probably need to try to add it again for whatever repository needs it.

---

### Post by nicckog2000 on 2020-09-19
Ok I'll try your commands gentlemen, thank you for your answers!

---

