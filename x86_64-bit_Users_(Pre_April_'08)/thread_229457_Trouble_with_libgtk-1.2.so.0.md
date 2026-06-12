---
title: "Trouble with libgtk-1.2.so.0"
date: 2006-08-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by tomek.vz on 2006-08-04
Hello :-)

I try to put to work ePSXe and Zsnes on Ubuntu 64bit but i always get this error:

./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory


libgtk1.2 and libgtk1.2-common are installed,so i think that epsxe is looking for 32bit version...?

Is there anyway around it?

P.S.-sorry my bad english.

---

### Post by Kilz on 2006-08-04
> **tomek.vz said:**
> Hello :-)

I try to put to work ePSXe and Zsnes on Ubuntu 64bit but i always get this error:

./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory


libgtk1.2 and libgtk1.2-common are installed,so i think that epsxe is looking for 32bit version...?

Is there anyway around it?

P.S.-sorry my bad english.

You could manualy copy in the 32bit libs into /usr/lib32. To save me typing this again and again [I created a page]("http://www.tghc.org/staticpages/index.php/32bitapplications") that explains how to do that.

---

### Post by fabertawe on 2006-08-05
> **tomek.vz said:**
> Hello :-)

I try to put to work ePSXe and Zsnes on Ubuntu 64bit but i always get this error:

./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory


libgtk1.2 and libgtk1.2-common are installed,so i think that epsxe is looking for 32bit version...?

Is there anyway around it?

P.S.-sorry my bad english.

Try [this post]("http://ubuntuforums.org/showpost.php?p=1339711&postcount=25"), it worked for me.

Paul

---

### Post by tomek.vz on 2006-08-05
Thanks guys :-) It works perfect :-)

---

