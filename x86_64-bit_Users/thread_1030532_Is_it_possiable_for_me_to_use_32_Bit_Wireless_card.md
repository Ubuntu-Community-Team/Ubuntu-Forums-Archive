---
title: "Is it possiable for me to use 32 Bit Wireless card?"
date: 2009-01-04
forum: x86 64-bit Users
---

### Post by Zaytoven on 2009-01-04
Hello I have a 32 Bit  EDIMAX EW-7728In PCI wireless adapter. I was wondering if it was possiable for me to use with Ubuntu 8.10 the 64 bit edition. If so how exactly do I do this because i'm very very lost :-(.

---

### Post by dicecca112 on 2009-01-04
32 Bit refers to the PCI slot not the version of Ubuntu it can work with,  As long as Ubuntu supports the chipset of the wireless card, yes you can use it.

---

### Post by Zaytoven on 2009-01-04
i'm so lost i don't even know where to start. This is the only thing that has completely stumped me so far in my PC building process. I need help. I can't go back to a windows world.:-(

---

### Post by jespdj on 2009-01-04
First, find out if Ubuntu sees the card, and find out what WiFi chipset it uses, and search for a Linux driver. Maybe the website of the manufacturer has a Linux driver, if it doesn't work out-of-the-box.

If the card has a Broadcomm chip, then it might be hard to get it to work. Broadcomm is notorious for its bad Linux support with regard to their WiFi chipsets.

Try
```
lspci
```
to get a list of devices, see if you see anything that looks like your wireless card in the list.

---

### Post by Zaytoven on 2009-01-06
It detects it as RaLink RT2800 but it says that it is unclaimed. it doesn't describe it as a being a wireless device. I got the latest driver downloaded but i have no idea how to install it. The Readme directions don't make sense to me. They are not in lamens terms to me.

---

### Post by jespdj on 2009-01-06
It would be helpful if you posted a link to the instructions, so that someone who knows more might help you with them.

Also, try searching the forums or with Google for "RaLink RT2800" or "Ubuntu RaLink RT2800" or something similar, and you might find more useful information.

---

