---
title: "Various Program Problems"
date: 2008-04-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by gtchamp7 on 2008-04-08
I have contiually tried to install ndiswrapper so I could install my wireless card driver (I have tried on both my 64-bit Ubuntu laptop and 32-bit Edubuntu desktop), but I have had absolutely no luck. I followed the readme instructions to a T, but when I use the ./install command it tells me that the command cannot be found. Ubuntu told me to use apt-get ndiswrapper, but when I tried to use ndiswrapper, it told me it could not find the command.

Also, I downloaded the ATi Radeon Xpress 200M driver and it was in a .run fie format and I know that I can execute it in the terminal, but whenever I do it tells me that I do not have sufficent rights. I knoew that I have to use the sudo command, but what command do i use specifically for .run files?

Thank You In Advance For Any Help,
Will Griffith

---

### Post by Glaxed on 2008-04-08
```

sudo apt-get ndiswrapper-common

```
the you've got to change into the directory where the install script is;
```

cd #the ndiswrapper directory
sudo ./install

```

---

### Post by Kilz on 2008-04-08
What version of Ubuntu did you install?

---

