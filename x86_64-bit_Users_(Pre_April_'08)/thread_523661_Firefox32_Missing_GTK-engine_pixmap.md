---
title: "Firefox32 Missing GTK-engine pixmap"
date: 2007-08-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by shanepardue on 2007-08-12
The default firefox on an amd64 ubuntu setup has the pixmap engine working beautifully, but when I installed firefox32, I can't get it to look right and this is the error message I get...
```

(firefox-bin:989): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
```

I'm assuming that firefox32 isn't seeing the 32-bit library, but I did install ia32-libs, ia32-libs-gtk, and linux32. Any help would be greatly appreciated!

---

### Post by Kilz on 2007-08-12
Hi, did you install firefox32 by my script or howto? The link is in my signature.

---

### Post by shanepardue on 2007-08-12
Yes I did...Thanks to you I was able to stick with the 64-bit firefox and got rid of my 
problem altogether. I used your nspluginwrapper method instead and am very happy 
with the performance. I appreciate your work for the 64-bit ubuntu community!

Keep up the good work!

---

### Post by Kilz on 2007-08-12
Since firefox is 32bit code, only compiled for 64bit. You are not getting any extra performance. Couple that with a 32bit wrapper flash plugin you dont get any difference.
Secondly there are plugins that dont work with the wrapper. There is also no safe java plugin for the 64bit browser.
If you would like , let me suggest you reread the 32bit firefox howto and look for a section on appearance.

---

### Post by shanepardue on 2007-08-12
Interesting! I don't know how I missed that when I went through your guide many times. 

Thanks again for your help!

---

### Post by shanepardue on 2007-08-12
That did get rid of the pixmap error message however I'm still receiving this message along with a bad-looking firefox.

```

 Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
```

---

