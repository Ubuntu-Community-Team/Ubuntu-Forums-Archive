---
title: "Boot up and Shut down screen problems"
date: 2009-01-24
forum: x86 64-bit Users
---

### Post by ezekiel000 on 2009-01-24
Since I got a new pc and installed Ubuntu 8.10 (AMD64) the boot screen drops out to the text boot up, it seems to be when it is mounting partitions & checking their clean but I may be wrong I'm not sure how to figure out what's wrong looking through the logs (I'm also not actually sure what I'm looking for).

And on the shut down screen the graphics are garbled since I upgraded to version 180 of the nVidia drivers, I have a built in nVidia 8200 graphics card.

Can anyone help me?

---

### Post by dcstar on 2009-01-25
> **ezekiel000 said:**
> Since I got a new pc and installed Ubuntu 8.10 (AMD64) the boot screen drops out to the text boot up, it seems to be when it is mounting partitions & checking their clean but I may be wrong I'm not sure how to figure out what's wrong looking through the logs (I'm also not actually sure what I'm looking for).

And on the shut down screen the graphics are garbled since I upgraded to version 180 of the nVidia drivers, I have a built in nVidia 8200 graphics card.


```
sudo update-initramfs -k all -u
```

---

### Post by ezekiel000 on 2009-01-25
Thanks, that seems to have sorted the shut down screen, but the boot up screen still drops out.

---

