---
title: "NeroLINUX 64-bits"
date: 2006-10-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by luishenriques on 2006-10-27
When I try to run the Nero for Linux on Ubuntu Edgy (AMD64), I get the following message:

nero: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

I already tried installing the packages:
ia32-libs
ia32-libs-gtk
ia32-libs-kde
ia32-libs-openoffice.org

Any thoughts?

---

### Post by John.Michael.Kane on 2006-10-27
NeroLINUX is available for PCs based on a 32-bit x86 architecture.  so the only method you have is dpkg --force-architecture .deb ,and theres no guaranties this would work

---

### Post by Swab on 2006-10-27
Works for me in 32 bit land...

---

### Post by CyberAngel on 2006-10-28
Download the 32bit package [libgtk1.2_1.2.10-18_i386.deb]("http://mirrors.kernel.org/ubuntu/pool/main/g/gtk+1.2/libgtk1.2_1.2.10-18_i386.deb")

then run the following:

```
dpkg -X libgtk1.2_1.2.10-18_i386.deb .
sudo cp * usr/lib/* /usr/lib32/
```

Try to rerun Nero Linux.

---

### Post by fabertawe on 2006-10-28
> **SD-Plissken said:**
> NeroLINUX is available for PCs based on a 32-bit x86 architecture.  so the only method you have is dpkg --force-architecture .deb ,and theres no guaranties this would work

I forced it in on Dapper and it still appears to be working with Edgy. If you don't (won't) have a licence for NeroLinux and you're using Wine then [Deepburner Free]("http://www.deepburner.com/?r=download") works great for me (not sure if you need the [wnaspi32.dll]("http://ww2.nero.com/nero7/enu/ASPI_Driver.html") but it's a free download anyway).

Paul

---

