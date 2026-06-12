---
title: "building Wine 58 on Hardy Heron (amd64)"
date: 2008-03-22
forum: Wine
---

### Post by slavik on 2008-03-22
Info taken from here: [http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)
Thanks to Triskelios from #winehq for help!

Follow the guide for building wine on 64bit gutsy, but where it asks you to create links, run the following 2 commands in addition to the one the guide says.
```

ln -s /usr/lib32/libcapi20.so.3 `pwd`/lib32/libcapi20.so
ln -s /usr/lib32/libdbus-1.so.3 `pwd`/lib32/libdbus-1.so

```

then you can continue with the rest of the guide or do the following:
```

make depend && make
sudo checkinstall

```

I prefer *checkinstal*l to *make install* because *checkinstall* generates a deb based on *make install* actions, to make removing wine easier.

---

### Post by IanW on 2008-03-23
Official build showed up this morning.

---

