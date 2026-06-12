---
title: "Google Earth 5 in 8.10 64"
date: 2009-02-13
forum: x86 64-bit Users
---

### Post by Milleman on 2009-02-13
Hi,

I've downloaded the latest installation file for Google Earth 5. The installation works fine. But when I start Google Earth, it shows for a few seconds and then just disappear. If I start it again, it will be the same.

Starting the Google Earth from a text terminal, gives this output after it disappear:

> 
$ ./googleearth
./googleearth-bin: relocation error: /usr/lib32/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference


Anyone that have experienced this?

(I'm using Ubuntu 8.19 64-bit.)

---

### Post by x33a on 2009-02-13
a lot of people have been facing the same problem.

this should work:

[http://blog.mymediasystem.net/avchd/google-earth-5-crashes-on-linux/](http://blog.mymediasystem.net/avchd/google-earth-5-crashes-on-linux/)

---

### Post by Milleman on 2009-02-13
Thanks x33a! :)
The information on your link, was the remedy for my problem.

Cheers,
/Mill

---

### Post by darco on 2009-03-01
> **x33a said:**
> a lot of people have been facing the same problem.

this should work:

[http://blog.mymediasystem.net/avchd/google-earth-5-crashes-on-linux/](http://blog.mymediasystem.net/avchd/google-earth-5-crashes-on-linux/)

thanksks, worked for me...I do still get this message tho when I enter sudo googleearth:

Warning: Unable to create prefs directory '/root/.googleearth'. File exists.
Xlib:  extension "XFree86-DRI" missing on display ":0.0".


darco

---

