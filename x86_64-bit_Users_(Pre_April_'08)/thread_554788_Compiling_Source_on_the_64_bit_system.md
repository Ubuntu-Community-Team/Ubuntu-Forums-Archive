---
title: "Compiling Source on the 64 bit system"
date: 2007-09-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by mikeym on 2007-09-19
Hi,

Could some boffin out there give me a quick rundown on what to expect when compiling source code on my 64 bit Fiesty system.

[COLOR="Red"][SIZE="3"]What I understand so far [/SIZE][/COLOR]

[LIST]
[*]For the most part you shouldn't need to compile most common applications. **[COLOR="Red"](edit)[/COLOR]**
[*]Compiling 32 bit code is OK, for example source code for games, but you must make sure that all the dependencies are 32 bit to.
[*]64 bit is OK as long as the coding doesn't make any assumptions about the bit'age. There are rarely any separate source codes for 32 bit and 64 bit. **[COLOR="Red"](edit)[/COLOR]**
[/LIST]

[COLOR="Red"][SIZE="3"]Questions I have [/SIZE][/COLOR]

[LIST]
[*]How do you tell the compiler to compile as 32 bit or 64 bit? **[COLOR="SeaGreen"][Adding -m32 flag to gcc][/COLOR]**.  **[COLOR="Red"](edit)[/COLOR]**
[*]How do you set it up to install and detect dependencies when you need a 32 bit and a 64 bit version?
[*]What flags is it OK to compile 32 bit code with? Can you make use of optimisations for your CPU?
[*]Can you test the code to see if it's 64 bit compatible? (perhaps not)
[/LIST]

---

### Post by Kilz on 2007-09-19
> **mikeym said:**
> Hi,

Could some boffin out there give me a quick rundown on what to expect when compiling source code on my 64 bit Fiesty system.

[COLOR="Red"][SIZE="3"]What I understand so far [/SIZE][/COLOR]

[LIST]
[*]Compiling 32 bit code is OK, for example source code for games, but you must make sure that all the dependencies are 32 bit to.
[*]64 bit is OK as long as the coding doesn't make any assumptions about the bit'age (most does).
[/LIST]

[COLOR="Red"][SIZE="3"]Questions I have [/SIZE][/COLOR]

[LIST]
[*]How do you tell the compiler to compile as 32 bit or 64 bit?
[*]How do you set it up to install and detect dependencies when you need a 32 bit and a 64 bit version?
[*]What flags is it OK to compile 32 bit code with? Can you make use of optimisations for your CPU?
[*]Can you test the code to see if it's 64 bit compatible? (perhaps not)
[/LIST]

Since no one has answered you perhaps my knowledge (which is limited in this area) will help. For the most part you shouldn't need to compile most common applications. There is now less than a 1% difference in available packages for the amd64 version vs the i386.
From what I have found is that almost all the applications I have tried to compile do so as 64bit executables. I have yet to compile a 32bit executable. But I think that the -m32 flag will accomplish that. If you want to make 32bit versions of something for distribution you may want to install a chroot for that to make it easier, or use a virtual machine.

---

### Post by Jouke74 on 2007-09-20
There are rarely any source codes separately for 32 bit and 64 bit. When you're compiling for 64 bit and  carefully read what it's doing then you will see that the 32 bits are converted to 64 bit in most cases by the compiler. I have had one program which failed to compile because of this, the rest worked fine compiling to 64 bit. (32 bit I have not tried compiling, because I specifically prefer 64 bit and usually 32 bit binary versions are available).

---

