---
title: "amd64 aspire laptop sound card detection"
date: 2008-01-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by pseudomonos on 2008-01-10
Dear Friends,

i have an amd64 X2 laptop and 64bit ubuntu installs brilliently on it, but it does bot detect that hard drives such as sound card. Can you give me a solution for the sound card.

thank you
chees:confused:

---

### Post by Yellow Pasque on 2008-01-10
Please run:
```
sudo update-pciids; sudo lspci
```
Post the output of lspci so we know what hardware we're working with here.

---

### Post by pseudomonos on 2008-01-11
thankyou, but i am new to linux. so can you give me the details of were and how to run
cheers

---

### Post by Yellow Pasque on 2008-01-11
Click Applications -> Accessories -> Terminal. Copy and paste that command in and then copy and paste the hardware info it gives here.

Also: what is the make/model of your laptop?

---

