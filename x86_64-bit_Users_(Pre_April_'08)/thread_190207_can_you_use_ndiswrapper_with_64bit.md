---
title: "can you use ndiswrapper with 64bit?"
date: 2006-06-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by rpesq on 2006-06-06
Hi,
I past experience, I have found the nic drivers for my wifi card to be lacking in reliability (freezes under heavy network load, such as bittorrent).  This is true even though the company has released all the drivers into the open-source community approx 1 year ago, so IMO the current reliability should be better than it is.  (Ralink RT2500 USB, aka RT2570).

Anyway, under 32 bit, I found ndiswrapper and the Windows drivers to work excellent.  But obviously those Windows drivers are 32 bit, so that is why I am asking whether ndiswrapper will be an option.

Thanks in advance.

---

### Post by Patsoe on 2006-06-06
Ndiswrapper is available in a 64bit version. However, you will need WindowsXP 64bit drivers with it.

---

### Post by praxxus on 2006-06-06
try here: [http://www.ralinktech.com/supp-1.htm]("http://www.ralinktech.com/supp-1.htm")

---

### Post by minneyar on 2006-06-06
I helped a friend set up ndiswrappers on an AMD64 laptop just last weekend, so I can verify that it does work.  Just make sure you have the 64-bit drivers for the card you're using.  If you have trouble finding a driver, I recommend looking around at [http://www.planetamd64.com/](http://www.planetamd64.com/) .

---

### Post by rpesq on 2006-06-07
Hi to all,

Many thanks to everyone for the fast and quality answers.  That is what I love about Ubuntu.  Knowledgeable and good people.  If the Ralink craps out, I'll be sure to go with Ndiswrapper.  I just hope their 64 bit drivers work as good as their 32 bit ones do!

---

