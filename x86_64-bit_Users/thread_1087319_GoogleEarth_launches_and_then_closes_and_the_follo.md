---
title: "GoogleEarth launches and then closes and the following is printed out..."
date: 2009-03-04
forum: x86 64-bit Users
---

### Post by qwertypianist on 2009-03-04
Hi all, 

Thanks in advance for the help. I'm new to Ubuntu and Linux in general really! :) 

I'm used to doing some things on Windows and I'd like to still be able to do them on Ubuntu if possible. This one problem is I'd like to use Google Earth. I've google'd how to do it and I got it so the GoogleEarth 5 program will open from the launcher icon in 'applications>internet>googleearth' but it sort of 'crashes' right away after it opens. 

I launched it from a command window which to get the error message which is below. The first part gets printed before the program starts to show up, the second part is after the program shows up and then disappears. 

converse@converse-desktop:~$ googleearth
Warning: Unable to create prefs directory '/home/converse/.googleearth'. File exists.

(the above is printed, then the program launches and then closes and the following is printed...)

/usr/lib/googleearth/googleearth-bin: relocation error: /usr/lib32/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference
converse@converse-desktop:~$ 



AMD Phenom 64bit quad core on a Foxcon mb. 
Ubuntu 64 8.10 Intrpid Ibex. 
nVidia 9800 GTX video card.

Thanks again in advance! :D

---

### Post by vandorjw on 2009-03-05
[http://ubuntuforums.org/showthread.php?t=195382&page=28](http://ubuntuforums.org/showthread.php?t=195382&page=28)

check that out.

I had the same problem as you did, and so had many other people.
There is a better thread somewhere that explains in more detail what exactly you have to do to fix it.

Basically, just remove one file. Do make sure it is the right one however. 

Reply if you get stuck.


Cheers - CC7

---

### Post by qwertypianist on 2009-03-05
> **cc7gir said:**
> [http://ubuntuforums.org/showthread.php?t=195382&page=28](http://ubuntuforums.org/showthread.php?t=195382&page=28)

check that out.

I had the same problem as you did, and so had many other people.
There is a better thread somewhere that explains in more detail what exactly you have to do to fix it.

Basically, just remove one file. Do make sure it is the right one however. 

Reply if you get stuck.


Cheers - CC7


Hi, right on!!! Thanks. It's working great now! TY. :D

I just removed that file that everyone was talking about and it seems to have worked. 

converse@converse-desktop:~$ locate libcrypto
/usr/lib/libcrypto.so.0.9.8
/usr/lib/googleearth/libcrypto.so.0.9.8
/usr/lib32/libcrypto.so.0.9.8
/usr/lib32/i486/libcrypto.so.0.9.8
/usr/lib32/i586/libcrypto.so.0.9.8
/usr/lib32/i686/cmov/libcrypto.so.0.9.8
converse@converse-desktop:~$ 
converse@converse-desktop:~$ rm /usr/lib/googleearth/libcrypto.so.0.9.8
rm: remove write-protected regular file `/usr/lib/googleearth/libcrypto.so.0.9.8'? y
rm: cannot remove `/usr/lib/googleearth/libcrypto.so.0.9.8': Permission denied
converse@converse-desktop:~$ sudo !!
sudo rm /usr/lib/googleearth/libcrypto.so.0.9.8
converse@converse-desktop:~$ 


Thanks again!

---

