---
title: "Application has a lock on it"
date: 2015-02-18
forum: Wine
---

### Post by devdlp on 2015-02-18
Ive been trying to open a application and cant because theirs a lock on it how do i remove it.

---

### Post by deadflowr on 2015-02-18
What application?

---

### Post by Bashing-om on 2015-02-18
devdlp; Yeah !

+1 to deadflowr . There are thousands of files open at any given time. We do need to narrow this down a bit.

[INDENT][INDENT]a complex operating system
[/INDENT][/INDENT]

---

### Post by devdlp on 2015-02-18
Nexus 2 Setup.exe

---

### Post by deadflowr on 2015-02-18
That's a windows extension (.exe)
Did you install wine?

---

### Post by devdlp on 2015-02-18
yes i did. The logo shows up and everything

what i did was downloaded a iso file and extracted itt, then opened it with achrive manager and it should me the files i got all the files and two of them was exe. files autrun and the setup but they both have pictures of locks on the icons so i know that means i dont have premission to use the application but i have tried a few things and still havent been able to unlock them for this user how do i do that?

---

### Post by deadflowr on 2015-02-18
Locks typically mean read-only, not cannot use.
An X would mean you cannot use.

But, you can right click on the file and look at the permissions to see how they are set.
(And ultimately who own it -- hopefully you do)

---

### Post by devdlp on 2015-02-18
i right clicked and messed around with the premission and suddenly got the locks to go away i dont even know what i really chose to do but i got the locks to go away

I cant use the application anyway wine shows Runtime Error (at -1:0):
Cannot Import dll:C:\users\deven\Temp\ia-FDTQU.tmp\isskin.dll.

---

### Post by oldos2er on 2015-02-18
Moved to Wine.

---

### Post by SL0ltMJGyh on 2015-02-19
You said it was an iso- What is the iso of?

---

### Post by devdlp on 2015-02-19
air-nexus2.iso

---

### Post by SL0ltMJGyh on 2015-02-20
check out the chmod command in terminal- try chmod +x air-nexus2.iso and post the results :)

---

### Post by devdlp on 2015-02-23
i already changed the premissions to use it now theres a different problems sorry this one is solved.

---

