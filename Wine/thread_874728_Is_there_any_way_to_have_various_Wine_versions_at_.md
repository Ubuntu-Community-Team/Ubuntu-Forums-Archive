---
title: "Is there any way to have various Wine versions at the same time?"
date: 2008-07-30
forum: Wine
---

### Post by Hellraizer51 on 2008-07-30
This would come in handy if it exists...

---

### Post by Hairy_Palms on 2008-07-30
yea there is, just install them to different prefixes, i have two versions, the latest and 0.9.61 for certain apps, (wc3 and FM08)

just install one version into /usr/local and then rename the executable, i have the latest wine as wine and the older wine command as wine96

---

### Post by kdorf on 2008-07-30
You could do that, but it's kind of a sloppy in that you have the executables in a system directory that aren't being managed by package.

Usually I compile from source and put them in ~/bin/wine.

You can get the needed build dependencies by running sudo apt-get build-dep wine

```
./configure prefix=${HOME}/bin/wine-x.x.x
make depend && make && make install
```

Should get you started. Obviously change the x to version number.

Benefit of this is you can also apply patches, etc. And no rogue system files. =)

---

### Post by Felson on 2008-07-31
One more side note... You should have a different .wine folder in your home directory for the different versions. Newer versions of wine will automatically update the contents of that directory, so if there is a change in there somewhere that an older version can't hack, it wont work.

---

