---
title: "Swap Space Nessesary?"
date: 2009-04-30
forum: x86 64-bit Users
---

### Post by ebanlague on 2009-04-30
Hello and thanks for reading.

Alright, I just got into the whole Linux world (Windows Convert :D) the other day and installed Jaunty. During installation, I didn't allocate any space for Swap Space, not fully understanding what it was at the time. 

My system has 8Gb (800Mhz) of memory but I am wondering if it would be beneficial to me in any way to allocate some Swap Space for my system.

Thanks in advance, Evan.

---

### Post by Yellow Pasque on 2009-04-30
With 8GB of memory, it might not be necessary depending on the tasks you do. What do you use your computer for?

---

### Post by ebanlague on 2009-04-30
Well, I frequently do video editing for me and my friends. On Windows I ran Sony Vegas, and I'm currently looking for a Linux Alternative to the program if you know of any. 

I also did work in Photoshop with high resolution photos, (3000 x 3000+). I'm starting to learn the ropes of the GIMP, but I'm very accustomed to Photoshop. If you know of anything that would the transition that would be great! :)

On rare occasion, I do web page design but that seems to be a lot lower pressure than the above two. I'm also going to leave gaming to my [very] small Windows 7 partition, as it's just a lot easier there.

Asides other regular computer tasks that sums it up. Your help is appreciated!
-Evan

---

### Post by Yellow Pasque on 2009-04-30
Use the following command to check your memory usage:
```
free -m
```
If you ever come near using all the buffers/cache, then you can create a swap file:
[http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/)

---

### Post by Sef on 2009-05-01
> My system has 8Gb (800Mhz) of memory but I am wondering if it would be beneficial to me in any way to allocate some Swap Space for my system.

Swap is needed for hibernation or suspend, if you choose to use them.

---

