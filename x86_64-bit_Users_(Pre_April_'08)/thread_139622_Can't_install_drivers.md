---
title: "Can't install drivers"
date: 2006-03-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Chillaxed on 2006-03-04
when i try using the codes to install nvidia display drivers i just get a black screen and nothing happens after :cry: 

i am thinking this is because there are no chipset drivers installed :mad: 

then i have to use 
```
 sudo dpkg-reconfigure xserver-xorg 
```

but i can't select nvidia drivers. i need to select vesa or something and then it boots properly

but the drivers aren't installed because i can't up my refresh rate or screen resolution :-k 

system specs:
athlon 64 3000+
gigabyte s939 micro atx nForce 430
integrated geforce 6100
1 gb kingston ram

---

### Post by ricka on 2006-03-04
check [http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074) METHOD 2
if it does not work check lines starting with (EE) from file /var/log/Xorg.0.log for xorg errors, you can do this from console with the following command:
 ```
cat /var/log/Xorg.0.log | egrep "^\(EE\).*$"
```
it will list all errors during xorg startup

---

