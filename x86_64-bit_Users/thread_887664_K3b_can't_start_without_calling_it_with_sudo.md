---
title: "K3b can't start without calling it with sudo"
date: 2008-08-12
forum: x86 64-bit Users
---

### Post by Dwezzel on 2008-08-12
Does someone have seen this issue ?

It seems impossible to start K3B without calling it with "sudo".

Tell me if I'm wrong...If I'm the only one ??

Dwe

---

### Post by felker2 on 2008-08-12
Open a terminal (xterm, konsole, kterm), type "k3b"<enter" and post what you see there.

---

### Post by stchman on 2008-08-13
> **Dwezzel said:**
> Does someone have seen this issue ?

It seems impossible to start K3B without calling it with "sudo".

Tell me if I'm wrong...If I'm the only one ??

Dwe

In some cases your ~/.kde folder gets owned by root.  TO fix it do the following:

```
sudo chown -R $USER:$USER ~/.kde
chmod -R 755 ~/.kde

```

---

### Post by Dwezzel on 2008-08-13
Thx stchman !!!

That's solved it !!!

Dwe

---

### Post by stchman on 2008-08-13
> **Dwezzel said:**
> Thx stchman !!!

That's solved it !!!

Dwe

You are welcone, this happened to me a while back and it took me a little while to figure out what happened.

---

