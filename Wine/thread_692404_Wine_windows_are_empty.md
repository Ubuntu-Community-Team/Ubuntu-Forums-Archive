---
title: "Wine windows are empty"
date: 2008-02-09
forum: Wine
---

### Post by Fir3chi3f on 2008-02-09
Wine seems to be running ok but all the characters are gone in winecfg, regedit and all applications im not given anything in the command line

I've tried reinstalling wine and installing ms fonts but still nothing. 

Any help and or questions is appreciated.

---

### Post by XVII on 2008-02-10
Bump.  I am having the exact same problem.

---

### Post by sawjew on 2008-02-11
I had the same problem after installing ie6 using wine-doors.  I fixed it by deleting my ~/.wine directory and starting again and this time didn't install ie6.

I make a habit now before I install a new app in wine of running ```
cp ~/.wine ~/.wine_backup
```

then if something goes wrong I can just ```
rm -rf ~/.wine
cp ~/.wine_backup ~/.wine
```

and everything is back the way it was.

---

### Post by ReccaSquirrel on 2008-02-12
I found myself with the exact same issue.

Worked fine (relatively speaking for Wine) and after IE6 was installed through Wine-Doors it did that.

---

### Post by XVII on 2008-02-12
Thanks, could you post the offending modifications to the code though?  I don't have a backup.

---

