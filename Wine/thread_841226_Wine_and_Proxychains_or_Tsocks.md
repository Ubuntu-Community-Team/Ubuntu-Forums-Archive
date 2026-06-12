---
title: "Wine and Proxychains or Tsocks"
date: 2008-06-26
forum: Wine
---

### Post by hyunkell on 2008-06-26
I cannot get wine to work with a socks wrapper.
I tried Proxychains and Tsocks, because that's the only ones I know for linux.

I get the following error:
> proxychains wine game.exe
ERROR: ld.so: object '/usr/lib/libproxychains.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libproxychains.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libproxychains.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libproxychains.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libproxychains.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libproxychains.so' from LD_PRELOAD cannot be preloaded: ignored.

same with tsocks, it errors on the tsocks library.

Any ideas?

Thanks,
Hyu

---

### Post by ph8 on 2009-02-23
Did you ever fix this? I'm having the same issue with tsocks...

---

### Post by md5encrypted on 2010-08-19
sudo ln -s /usr/lib/libproxychains.so.3 /usr/lib/libproxychains.so

Or if you are using amd64, download 32-bit libproxychains.so and copy it to /usr/lib32

---

### Post by dacha on 2010-08-23
Wine probably won't work with any socksifiers because they all assume socket identities are invariant, while on Wine they do change (each transit through wineserver changes the file descriptor's value).

Use a transparent proxy or NAT.

---

### Post by Gunman1982 on 2010-08-23
Another option is to use a windows proxyfying application.

---

