---
title: "How to view encrypted DVD's in Ubuntu 9.10 Karmic on 64 bit."
date: 2009-11-11
forum: x86 64-bit Users
---

### Post by JayOne on 2009-11-11
How can I? I have to resort to continuously booting to Windows to do this but it's easier just to learn what I have to install. Just give me terminal options please because I've done this before but forgot.

---

### Post by HappyFeet on 2009-11-11
The following can go in all at once
```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update
```
then
```
sudo apt-get install libdvdcss2
```

---

### Post by JayOne on 2009-11-12
Thanks and can you also tell me how to change my experience from "First Cup of Ubuntu"?

---

### Post by KayakJim on 2009-11-13
> **JayOne said:**
> Thanks and can you also tell me how to change my experience from "First Cup of Ubuntu"?

I believe that is a forum setting based upon the number of posts you have.

---

### Post by HappyFeet on 2009-11-13
> **JayOne said:**
> Thanks and can you also tell me how to change my experience from "First Cup of Ubuntu"?

You can't change that. The more posts you have, it will change accordingly.

---

