---
title: "undefined symbol: gzopen64"
date: 2007-11-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by yngvi on 2007-11-12
Dear reader,

I am having some serious problems running a matlab mex file which always exits with the error:

```
??? Invalid MEX-file 'myfile.mexa64': /usr/lib/libxml2.so.2: undefined symbol: gzopen64
```

I have a clean fresh install of Ubuntu 7.10 (Gutsy) on a x86_64 architecture. I do have libz, libxml installed and I do NOT have any old versions of libxml around on this system (which seems to have caused similiar errors for users who have upgraded Ubuntu).

From extensive web-searches (o.k. googling if you like) I tried some of the hints given such as:

```
strings libz.so.1 | grep gzopen64
gzopen64
```

or

```
objdump -T /usr/lib/libz.so.1 | grep gzopen64
00000000000048a0 g    DF .text  000000000000000f  Base        gzopen64
```

and

```
strace -eopen myfile 2>&1 | grep libz
```

with no luck.

Checking the library dependencies of "myfile" results in:
```
ldd myfile
libz.so.1 => /usr/lib/libz.so.1 (0x00002aaf7c91d000)
```

Updating LD_LIBRARY_PATH to make it search for the Matlab version of libz gives:
```
libz.so.1 => /usr/local/tools/matlab_64/bin/glnxa64/libz.so.1 (0x00002ba56b015000)
```

NONE of the above solved this issue with gzopen64. I am running against a wall here.
The worst is, that this mexfile is working on other machines without problems. Before installing Ubuntu on this Laptop I had a testing version of Fedora and even there it worked out of the box. 
However, prefering Ubuntu (still) I would like to have this problem resolved somehow, but there is clearly a lack of ideas right now...

So, if anybody could point me to what I could try next, I would be extremely grateful!!

cheers,
i.

PS: I can not recompile the mexfile. It is part of a simulation tool I got and I do not have the source file.

---

### Post by yngvi on 2007-11-13
Ok, found the error.
For some reason (that I don't understand) my mexfile did not like the standard Ubuntu libxml. Linking to the one on another machine where the code works did the trick.

Thanks anyway,
i.

---

