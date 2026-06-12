---
title: "a driver from ati site bunch of problems"
date: 2006-11-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by baytuni on 2006-11-29
Hi. I have an ati radeon x550 and I had a lack of performance in 3d applications so i decided to install a new driver from ati site which is not so wise I guess. I did exactly what they say at [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.31.5-inst.html]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.31.5-inst.html")
but then after uninstalled fglrx Iget this message namely .xsession-errors

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "kobra"
/etc/gdm/Xsession: Beginning session setup...
.: 106: Can't open /etc/profile

```

Then I reinstalled fglrx from synaptic but I still have this.Also the fonts and the themes are changed.

Thanks in advance!

---

### Post by pay on 2006-11-29
You would be better off looking at a Ubuntu specific guide [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) or
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---

### Post by baytuni on 2006-11-29
when applying the steps on wiki when I write

```
bash ati-driver-installer-8.29.6.run --buildpkg
```

it says
```
./ati-installer.sh: 176: Syntax error: Bad substitution

```

---

### Post by baytuni on 2006-11-29
also when I execute fglrxinfo
I get this. Who is Mesa? I guess i would be ATI.

```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
```

---

### Post by baytuni on 2006-11-29
in the [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](wiki)
I applied method 2. But fglrxinfo show mesa driver as I showed previous entry. I guess problem is that. But I Can't get rid of it. I did what the wiki says in the troubleshooting section.But no good. I need some help...

---

