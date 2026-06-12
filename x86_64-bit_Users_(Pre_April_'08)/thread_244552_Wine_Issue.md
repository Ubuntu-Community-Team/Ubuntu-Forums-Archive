---
title: "Wine Issue"
date: 2006-08-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by kob0724 on 2006-08-26
So I went to compile wine because I'm running on an amd-64 architecture. Everythign was going fine (I was following this [http://winehq.org/site/download-deb)](http://winehq.org/site/download-deb)), until I typed 
```

sudo apt-get --build source wine

```

Then I got this

```
configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [config.status] Error 77
Build command 'cd wine-0.9.20~winehq0~ubuntu~6.06 && dpkg-buildpackage -b -uc' failed.
E: Child process failed

```

Whats going on?

---

### Post by Kilz on 2006-08-26
> **kob0724 said:**
> So I went to compile wine because I'm running on an amd-64 architecture. Everythign was going fine (I was following this [http://winehq.org/site/download-deb)](http://winehq.org/site/download-deb)), until I typed 
```

sudo apt-get --build source wine

```

Then I got this

```
configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [config.status] Error 77
Build command 'cd wine-0.9.20~winehq0~ubuntu~6.06 && dpkg-buildpackage -b -uc' failed.
E: Child process failed

```

Whats going on?

Its very hard to compile wine, almost impossible with the 64bit version. In my signature you will find a link to the wine howto that will help you install it.

---

