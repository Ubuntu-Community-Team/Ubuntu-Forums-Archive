---
title: "openoffice hangs with JRE enabled"
date: 2006-12-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by rajeev1204 on 2006-12-01
hi

I cannot run openoffice with JRE enabled.I tried to install J2RE 1.5 but open office wont show that in tools/options/java.It shows 1.4 version only.


iam running office without JRE so i cant use wizards in it now. but runs fine.

any solutions?


regards

rajeev

---

### Post by rajeev1204 on 2006-12-05
hi

is anyone here facing problems with openoffice and java . it seems this problem is there in other 64 bit distros as well.


it seems office is 32 bit application and recognises only 32 bit jre

but it probably tries to look for other versions also in tools/options/java.

after a lot of time it lists the versions , gcj free and sun java 32

if i select either one it still hangs.

i have also filed  a bug report. i found on google lot of people have this problem


regards

rajeev

---

### Post by rajeev1204 on 2006-12-09
hi

i managed to solve this problem by selecting the 32 bit sun java version from the repos.

also most importantly , i type in terminal :

" sudo update-alternatives --config java".

This lists all the available java versions .select 32 bit SUN VERSION .

then in office in tools/options/java select this version.

Problem solved


regards

rajeev

---

