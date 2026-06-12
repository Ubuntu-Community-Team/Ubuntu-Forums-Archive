---
title: "Open/Save as dialog causes programs to crash"
date: 2008-07-17
forum: x86 64-bit Users
---

### Post by AisDeck on 2008-07-17
Whenever I try to open a file through File -> Open... in any program, the program crashes.

Example 1: Trying to open a file in Bluefish Editor. This is what the logs say.
```
Jul 17 09:20:39 late-laptop kernel: [  221.295319] bluefish[6660]: segfault at 3 rip 7f8bdd015940 rsp 7fffe72ffe98 error 4
```


Same thing happens if trying to save something.

Example 2: Trying to save an image through Save as in GIMP.
```
Jul 17 09:34:18 late-laptop kernel: [  568.799900] gimp-2.4[6916]: segfault at 3 rip 7f6b44ed2940 rsp 7fff508f2aa8 error 4
```

I think this has something to do with the kernel update, since the problems started right after that.

EDIT: Also tried using an older kernel, didn't help. Open/Save as feature is after all quite essential... Any way to fix this or is this going to be the first time I am going to have to reinstall linux due to something not working?

EDIT2: Reinstalled Ubuntu, updated kernel. Same problem continues.

EDIT3: Problem solved. Made a new user and it works like a charm. Thanks for nothing.

---

