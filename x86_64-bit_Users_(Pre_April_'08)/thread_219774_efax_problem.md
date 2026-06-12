---
title: "efax problem"
date: 2006-07-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by mfleming on 2006-07-20
Folks, 

I would appreciate some help with the following. I have been using efax for many years. Now I am using it on an Opteron machine with the AMD64 version of Dapper Drake. On this platform, it crashes with the following message:

/usr/bin/fax: line 776:  2110 Segmentation fault      $EFIX -ve -otiffg3 -p$PAGEDIM -r$RES -n $1.%03d $TEXTFONT $1

fax is just a shell script, invoking here the program $EFIX which is just efix, a program which converts among fax file formats. 

I was wondering if anyone has seen this before and what I might do about it.

Thanks much,

Matthew Fleming

---

