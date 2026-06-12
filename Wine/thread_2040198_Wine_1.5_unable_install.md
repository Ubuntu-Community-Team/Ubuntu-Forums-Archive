---
title: "Wine 1.5 unable install"
date: 2012-08-10
forum: Wine
---

### Post by Dr Dedoverde on 2012-08-10
hello!

is that to install wine must be added the repositories, update with apt-get and install.
the problem is in the installation

```
jorge@jorge-A790GXM-AD3:~$ sudo apt-get install wine1.5
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
 wine1.5 : Depende: wine1.5-amd64 (= 1.5.10-0ubuntu1~pulse19+build2) pero no va a instalarse
           Recomienda: ttf-droid pero no es instalable
           Recomienda: ttf-mscorefonts-installer pero no va a instalarse
           Recomienda: ttf-umefont pero no es instalable
           Recomienda: ttf-unfonts-core pero no es instalable
           Recomienda: winetricks pero no va a instalarse
E: No se pudieron corregir los problemas, usted ha retenido paquetes rotos.
```try installing the file list that gives me, but it is impossible.

---

### Post by rukiaEnix on 2012-08-10
¿Y qué pasa si sólo escribes así la instalación?:

```

sudo apt-get install wine

```

---

### Post by Dr Dedoverde on 2012-08-10
> **rukiaEnix said:**
> ¿Y qué pasa si sólo escribes así la instalación?:

```

sudo apt-get install wine

```


```
 wine : Depende: wine1.5 pero no va a instalarse
```entiendo que tengo que descargar los paquetes... me canse de buscarlos
I understand I have to download packages ... I get tired of searching

---

### Post by rukiaEnix on 2012-08-13
Have you already try installing it with this guide?:

[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

---

