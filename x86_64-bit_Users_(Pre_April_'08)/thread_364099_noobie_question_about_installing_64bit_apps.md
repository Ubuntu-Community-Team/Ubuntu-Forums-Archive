---
title: "noobie question about installing 64bit apps"
date: 2007-02-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by ffxr on 2007-02-17
hi, i have a new 64bit PC in the post.. and want to install a 64bit OS on it..

i have a question about adding new software to it.. 

can i keep my current sources.list (i.e copy my current one to my new box) or does AMD64 have its own repos'? (i realise this is probably unlikely)

& when i do an apt-get install "whatever"; does the app get built automatically for my 64bit os?
also, if i download a .deb from somewhere, generally will this be built for my 64 bit os? i.e is there a seperate .deb for 32bit & 64bit OSs'

i have this notion that i will have to build all my apps from source to make them 64 bit.

any answers &/or elaboration on the technicalities of installing new software to an AMD64 system gratefully received.

---

### Post by John.Michael.Kane on 2007-02-17
The souce.list is the same. the programs for 64bit ubuntu are already built,and in the repo. when you apt-get said program it downloads the file + dependances,and installs them. 

The only time you the enduser would have to do a build is if a program is not backported yet. In this case you would download the source,and other needed tools,and build it yourself.

---

### Post by kodalisrikanth on 2007-02-19
First of all why u r willing to put 32-bit sourcelist..?
     Most of the ubuntu packages are same for 32 & 64 bit procesors.The main aim of 64-bit OS is to get maximum processor speed.If u put the 32-bit source list u may loose that performance.(Ex:64 bit firefox).
      comming to *.deb packages they are precompiled binary archives like *.exe files.(Easy to install).There are 64-bit *.deb packages.If u find any 64-bit packages better to install that only...

---

