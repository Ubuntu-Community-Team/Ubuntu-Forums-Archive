---
title: "Wine in 64 bit?"
date: 2005-07-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by filemanager on 2005-07-03
Does anyone know if Wine works on amd64 systems?

---

### Post by WMCoolmon on 2005-07-03
You can get Cedega working on AMD64; see the guide [here](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#How_to_install_Cedega_on_AMD64).

---

### Post by ::DoGG:: on 2005-07-04
I was able to run CrossoverOffice and Cedega on AMD64, but i never was succesfull to compile Wine from Source. Compiler complains about some Assembler errors, i did some research and came to conclusion that it`s a kernel fault basically, don`t know exactly wchich function caused it... I f anybody was able to compile it on AMD64, please report it :D

---

### Post by filemanager on 2005-07-04
> **WMCoolmon]You can get Cedega working on AMD64 said:**
> here[/url].
 I've installed Cedega as that page said, but I can't see it anywhere, and the documentation on transGaming is pretty vague. How do I use it?

---

### Post by WMCoolmon on 2005-07-04
"cedega name_of_application.exe"

For more info just type "cedega", or "man cedega" for even more.

---

### Post by filemanager on 2005-07-04
[QUOTE=WMCoolmon]"cedega name_of_application.exe"

For more info just type "cedega", or "man cedega" for even more.[/QUOTE]
 This is the error I got:

root@calvin3:/home/jen # cedega setup.exe
/usr/lib/transgaming_cedega//winex/bin/wine: error while loading shared libraries: libwine.so: cannot open shared object file: No such file or directory

the setup.exe file is on a CD in my CD-ROM. Not sure how to point it there though. I tried installing point2play but I'm getting an error during the install =\

---

### Post by Jet2k5 on 2005-07-05
OMG there is a guide for this!  NICE!!!! I thought I was all alone when it came time to get cedaga running on AMD 64

Thanks for the post/answer this relieves me of 1 nightmare!! w00t w00t

---

