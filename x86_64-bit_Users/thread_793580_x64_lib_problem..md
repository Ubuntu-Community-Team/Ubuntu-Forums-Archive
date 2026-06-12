---
title: "x64 lib problem."
date: 2008-05-13
forum: x86 64-bit Users
---

### Post by arckeda on 2008-05-13
Hey, I am trying to launch psclient.bin from Planeshift, on x64 Ubuntu, I downloaded the x64 client, although I am not sure if that matters, I keep getting this:
```
./psclient.bin: error while loading shared libraries: libCgGL.so: cannot open shared object file: No such file or directory

```
I tried getlibs, but it couldn't find it, and I can't find it on the Internet, at least from what I searched, I love Ubuntu and it's community, but so far I have had bad luck with the forums, I know this is a stupid question but, what do I do now?
Thank you.
     -ARCKEDA

---

### Post by Cappy on 2008-05-14
It's not in the ubuntu repos. It probably came with the game and it isn't in your library PATH.

Is there a launch script or does just "planeshift" launch the game. Also try "planeshift" and hitting tab twice and see if it autocompletes if that doesn't work.

If there isn't a launch script then try searching for the library with
```

sudo updatedb; slocate libCgGL.so

```

---

