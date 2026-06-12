---
title: "Question on impacto of installing ia32-libs"
date: 2007-06-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by willyram on 2007-06-23
Hi, I've installed Feisty on my new AMD64 machine, and I really love it, even more after installing compiz and beryl.  Simply rocks.
I have a question though. I've noticed that while installing some 32 bit application -if I recall right it was the flash9 to run under wrapper script- the ia32-libs packages have been installed. These made sense to me as these apps need a32-bit environment.
My question is about the impact of having this in the system (which seems unavoidable nevertheless). 
1) Are the IA32 libs used only by 32 bits applications or after installing them the previous libs replace their 64-bit equivalents?
2) It they do co-exist (which I think is the right answer), has anyone studied or evaluated the impact of having both environments running versus installing a 32-bit linux?
For my side, I really love and want to run on ia64, as some operations seems to run sensibly faster. But I want to separate emotions from reality.
And yes, this is just technical curiosity, as I am much too happy with my new system to change it.
Thanks, Willie.

---

### Post by Cappy on 2007-06-23
Yes, they are only used on 32-bit applications. 64-bit applications will still only use the 64-bit libraries.
32-bit libraries are in /usr/lib32 and sometimes in /lib32
64-bit libraries are in /usr/lib and sometimes /lib

They co-exist fine as long as you don't force install LIBRARIES from a deb file, in which case, it overwrites the 64-bit library. Force-installing is fine as long as it is a program and not a library.

---

### Post by willyram on 2007-06-23
Cappy, thank you very much for your response. 

I have a question then, does Automatix do any of those force libraries??

Txs, Willie.

---

### Post by Kilz on 2007-06-23
> **willyram said:**
> Cappy, thank you very much for your response. 

I have a question then, does Automatix do any of those force libraries??

Txs, Willie.

Its hard to tell exactly what automatix does anymore. Your question may best be suited to asking them. But I will suggest this. There is nothing that automatix installs that you yourself cant install. That when you do install some things you gain knowledge.
That cant be anything but a positive. If you need some help installing anything, do a search and if there isnt a post on it (with the amount of posts its hard to imagine there isnt a post on every subject) post one yourself.

---

