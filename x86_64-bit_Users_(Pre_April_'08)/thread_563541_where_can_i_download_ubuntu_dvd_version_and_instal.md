---
title: "where can i download ubuntu dvd version? and installing problems"
date: 2007-09-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by asdf2 on 2007-09-30
where can i download ubuntu dvd version? and installing problems
i had many problems to install ubuntu (5. something) because there was many kinds of problems with the "partitioning" of the hard drive.
when i tried to use that kink of automatic partitioning it freezes

thanks.

---

### Post by John.Michael.Kane on 2007-09-30
> **asdf2 said:**
> where can i download ubuntu dvd version? and installing problems
i had many problems to install ubuntu (5. something) because there was many kinds of problems with the "partitioning" of the hard drive.
when i tried to use that kink of automatic partitioning it freezes

thanks.

7.04 64bit dvd link below.
[64-bit PC (AMD64) install/live DVD]("http://cdimage.ubuntu.com/releases/7.04/release/ubuntu-7.04-dvd-amd64.iso")

---

### Post by asdf2 on 2007-09-30
thanks,
there is wireless internet package in this big file?

---

### Post by John.Michael.Kane on 2007-09-30
> **asdf2 said:**
> thanks,
there is wireless internet package in this big file?

Wireless support will really depend on the card being used.

I would suggest having a look over this [WifiDocs/WiFiHowTo]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo"), After you have your system running.

---

### Post by asdf2 on 2007-10-03
ok, so by your replies i understand that i don't just need to install wireless internet package, but also to install a driver if available. and i don't know how to do that.

---

### Post by John.Michael.Kane on 2007-10-03
> **asdf2 said:**
> ok, so by your replies i understand that i don't just need to install wireless internet package, but also to install a driver if available. and i don't know how to do that.

You will need to know what chip your wifi card uses. To find out that info use the command below.
```
lspci
```

Example lspci output, This is what you would look for.

```
06:09.0 Ethernet controller: Makers Name Co., Ltd. RTL-XXXX IEEE 802.11a/b/g Wireless LAN Controller (rev XX)

```

---

