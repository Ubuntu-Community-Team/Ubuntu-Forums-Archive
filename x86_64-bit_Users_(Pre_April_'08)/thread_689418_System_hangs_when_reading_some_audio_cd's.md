---
title: "System hangs when reading some audio cd's"
date: 2008-02-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Gumper on 2008-02-06
I'm in the process of ripping my music cd's to ogg format and I'm having some issues with some of the cd's. After inserting the cd into my drive my system becomes very sluggish and can't access the cd. This is only happening with a couple of the cd's. Most of them are able to be seen by the system. When I eject the cd, my system returns to normal.

If I try the same cd in my windows partition, there's no problem. 

Any idea what's going on here?

---

### Post by prince_niceguy on 2008-02-06
run the following command in the terminal.

```
$ top
```

after running the command put the cd in the drive and see which process is taking highest cpu or if %wa is reaching close to 100%.

that will give some starting point to find the problem.

---

### Post by Gumper on 2008-02-06
> **prince_niceguy said:**
> run the following command in the terminal.

```
$ top
```

after running the command put the cd in the drive and see which process is taking highest cpu or if %wa is reaching close to 100%.

that will give some starting point to find the problem.

From looking at the output for "top", I see that there are two processes that alternate with 99% cpu load. They are 'kio_audiocd' and 'hald-addon-stor'.

---

