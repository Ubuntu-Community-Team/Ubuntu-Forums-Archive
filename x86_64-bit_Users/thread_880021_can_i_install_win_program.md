---
title: "can i install win program ?"
date: 2008-08-04
forum: x86 64-bit Users
---

### Post by kyo007 on 2008-08-04
hi, can i install windows programs to ubuntu ? 

Thanks.

---

### Post by Kilz on 2008-08-04
> **kyo007 said:**
> hi, can i install windows programs to ubuntu ? 

Thanks.

You can run some windows programs with Wine. But Wine is not perfect. It may require a lot of setup and configuration. There is no guarantee that the windows application will run, and if it does it may have a lot of problems. It is always best to find Linux applications (there are 20k free packages available in Ubuntu) that have the same functionality instead of running windows applications.

---

### Post by kyo007 on 2008-08-04
how can i install it ? i use x64 ubuntu.

---

### Post by perlluver on 2008-08-04
> **kyo007 said:**
> how can i install it ? i use x64 ubuntu.

Normally sudo apt-get install wine.  Or open up Synaptic Package Manager and search for Wine.

---

### Post by kyo007 on 2008-08-04
thanks ! it's great, where is it installing program ?

---

### Post by crwmike on 2008-08-04
> **kyo007 said:**
> thanks ! it's great, where is it installing program ?

/home/your_user_name/.wine/drive_c/Program Files

---

