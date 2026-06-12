---
title: "gnome fails to start"
date: 2007-01-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by DRagonRage on 2007-01-06
did something (maybe replaced libutils.so.1 file)
now xsession fails to start 
it writes:
error while loading shared libarrys : libutil.so.1 
tryed
apt-get remove libc6 <-- fails
apt-get install libc6

how can i restore my desktop?

sorry about my bad langage :-# 

here is ls -l /ib |grep libutils:
```

-rwxrwxrwx  1 1000 1000    7684 2007-01-06 17:02 libutil-2.3.6.so
lrwxrwxrwx  1 root root      16 2006-07-14 15:12 libutil.so.1 -> libutil-2.3.6.so

```

if you need more info what?
](*,) 

if my topic is illegal im trully sorry....

---

### Post by moma on 2007-01-06
I run 32 bits Ubuntu, but the mechanism should be the same in X86_64.

What package contains libutil.so.1 ?
$ [COLOR="SeaGreen"]dpkg -S libutil.so.1[/COLOR]
libc6: /lib/libutil.so.1
libc6-i686: /lib/tls/i686/cmov/libutil.so.1

Reinstall that package. Notice the --reinstall argument.
$ [COLOR="SeaGreen"]sudo apt-get install --reinstall libc6[/COLOR]

Your libutil-2.3.6.so has strange file owner and file group (1000?). What's that? 
Check it and fix it.
$ [COLOR="SeaGreen"]sudo chown root:root  /lib/libutil* [/COLOR]

Finally, update library cache 
$ [COLOR="SeaGreen"]sudo ldconfig [/COLOR]
or  ldconfig -vv

---

