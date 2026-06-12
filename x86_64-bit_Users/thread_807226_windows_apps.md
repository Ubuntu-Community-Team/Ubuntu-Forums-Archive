---
title: "windows apps"
date: 2008-05-25
forum: x86 64-bit Users
---

### Post by gordon3056 on 2008-05-25
how do I run other programs (Windows) in UBUNTU. I havent got milk in my cup yet :)

---

### Post by tim_wright on 2008-05-25
Load up terminal and copy and paste this:

***sudo apt-get install wine***

Make sure you have all the additional software sources (universe, restricted etc...) enables in "System --> Administration --> Software Sources"

---

### Post by Kilz on 2008-05-25
> **gordon3056 said:**
> how do I run other programs (Windows) in UBUNTU. I havent got milk in my cup yet :)

You might want to know a little bit more [about wine]("http://tghc.org/winefaq.html").

---

### Post by gordon3056 on 2008-05-25
Thanks did that but now cant get past password nothing types to terminal

---

### Post by tim_wright on 2008-05-25
Just type your normal login password. It's a security measure in linux console that it doesn't show you the little stars like windows does.

---

### Post by gordon3056 on 2008-05-25
Thanks that has done quite a lot so now I can run exe's using wine is that right

---

### Post by LeoSolaris on 2008-05-25
Yes, but it is NOT perfect. It will not work with everything. Best advice, try it to see if it will work. Do look to see if there are any comparable native Linux programs, like Aisle Riot Solitaire to replace MS Solitaire, or Evolution for MS Outlook.

If it does not work, there is no comparable program, and it is not a game, you can install windows in a virtualbox, and have it run the program. (usually good for tax software that doesn't like Linux.)

Leo

P.S. do look at that link posted by Kilz to learn more about Wine. It can be a little complex.

---

