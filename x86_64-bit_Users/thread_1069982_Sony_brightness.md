---
title: "Sony brightness"
date: 2009-02-14
forum: x86 64-bit Users
---

### Post by sbardascione on 2009-02-14
Hi everybody,
i'm new(bie) and i'm italian so sorry for my english.
I recently installed 64Bit version of 8.10 in my sony vaio vgn-cs11 and i can't set the brightness of the lcd.
Thank you for advices.
Bye.

---

### Post by Nepherte on 2009-02-15
What is the graphics card of your laptop?

---

### Post by sbardascione on 2009-02-15
Hi,
it's an 
```
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9300M GS (rev a1)

```
.

---

### Post by Nepherte on 2009-02-15
Try out nvclock to set your brightness.
```
sudo apt-get install nvclock
```

Usage:
```
nvclock --smartdimmer <percentagevalue>
```

---

### Post by sbardascione on 2009-02-15
I tried it, but it doesn't work.

EDIT: it gives me this: 
```

xxxxxx@xxxxxx-laptop:/usr/bin$ ./nvclock -S 90
Error!
Smartdimmer is only supported on certain laptops using a Geforce 6200/7x00Go. If you want support on your laptop contact the author.
xxxxxx@xxxxxx-laptop:/usr/bin$ 


```

---

### Post by sbardascione on 2009-02-15
Ok, it works:
```

sudo apt-get install cvs sudo apt-get install libx11-dev automake nvclock
cd /root
sudo cvs -d:pserver:anonymous@nvclock.cvs.sourceforge.net:/cvsroot/nvclock login (nessuna password)
sudo cvs -z3 -d:pserver:anonymous@nvclock.cvs.sourceforge.net:/cvsroot/nvclock co -P nvclock
cd nvclock
sudo ./autogen.sh
sudo ./configure
sudo make
sudo make install

```
then:
```

nvclock -S (percent number)

```
:)

---

### Post by cuyo on 2009-04-13
Hi sbardascione
I'm trying to make my HP3510nr brightness works (same 9300m gs), I follow your directions but password don't works (nessuna)
Can you help me. Thanks
As you english is not my native language, but I try.

EDIT
I download nvclock 0.8b4 from project page and compile.
Works great. Next fn+f6 f7
Thanks again

---

