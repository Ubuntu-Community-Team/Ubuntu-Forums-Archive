---
title: "Only shows 3.2gb of ram out of 4gb"
date: 2009-09-11
forum: x86 64-bit Users
---

### Post by dracule on 2009-09-11
Hey guys

I just installed it on my HP workstation wx9000
w/ 
2 separate dual core opterons
4gb RAM
ATI 4890


In windows, it displays my ram as "4.0 GB"

in Ubuntu it gives me "3.2 GB"


I checked to make sure it was 64 bit (using 'uname -m') and it was so where is my RAM?

---

### Post by pastalavista on 2009-09-11
In terminal, type "free". It's probably shared with graphics.

---

### Post by gagne on 2009-09-12
Open a terminal and type in free -m. You could also use top or htop to check the memory.

---

### Post by dracule on 2009-09-12
I enabled remapping of memory in my bios and reclaimed .6gb, so free-m shows my total at 3871

---

