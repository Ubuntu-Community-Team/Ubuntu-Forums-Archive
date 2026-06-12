---
title: "I messed up my dpkg"
date: 2008-11-26
forum: x86 64-bit Users
---

### Post by figos on 2008-11-26
While installing mail-notification, my netbook froze and I head to shut it down manually. Now every time I try to use apt, I get this message:

> (A ler a base de dados ... dpkg: erro ao processar mail-notification (--purge):
 não foi possível abrir o ficheiro de lista de ficheiros para o pacote `mail-notification': Erro de Entrada/Saída de dados
Foram encontrados erros enquanto processava:
 mail-notification
O processamento parou porque ocorreram demasiados erros.
E: Sub-process /usr/bin/dpkg returned an error code (1)


How can I fix this?

Thanks

---

### Post by Stemp on 2008-11-26
Try : 
```
sudo dpkg --configure -a
```

Another tip, it's better to give the error messages in english, so use LANG=C before your command.

eg :
```
LANG=C sudo apt-get update
```

---

### Post by figos on 2008-11-27
The command you gave me didn't do anything :(

Anyway, this is what I get when I try to remove the broken package.

> xxx@xxxxpc:~$ LANG=C sudo apt-get purge mail-notification 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  mail-notification*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1491kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 106843 files and directories currently installed.)
Removing mail-notification ...
dpkg: error processing mail-notification (--purge):
 unable to stat installed pre-removal script `/var/lib/dpkg/info/mail-notification.prerm': Input/output error
dpkg: error while cleaning up:
 unable to stat installed post-installation script `/var/lib/dpkg/info/mail-notification.postinst': Input/output error
Errors were encountered while processing:
 mail-notification
E: Directory '/var/log/apt/' missing
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by Stemp on 2008-11-27
> E: Directory '/var/log/apt/' missing

Try to recreate it :

```
sudo mkdir -p /var/log/apt/
```

---

### Post by figos on 2008-11-27
I've managed to correct everything by removing var/lib/dpkg/info/mail-notification.*

Thanks for the help

---

