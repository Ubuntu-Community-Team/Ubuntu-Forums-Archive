---
title: "Can't get plugins to work in 32 bit Chrome"
date: 2009-10-12
forum: x86 64-bit Users
---

### Post by RobertHamilton on 2009-10-12
Hai, 
I've been using Google-Chrome-unstable for amd64 which for the most part works flawlessly but i couldn't play Runescape (java-based game) in High Detail with 64 bit and people were saying it doesn't work in 64 bit but 32 bit works.. So I /force/ installed Google-chrome-unstable for 32 bit on my amd64 ubuntu which is working fine except i can't get any plugins to work. I've made a new directory in /opt/google/chrome called 'Plugins' and put the lib files there but i get nothing when i go to Runescape or Youtube.. just black. 

What am I doing wrong? won't 32 bit plugins work on 64 bit architecture or something? :confused:

---

### Post by Yellow Pasque on 2009-10-12
If you're running a 32-bit browser, then you would need 32-bit plugins, e.g.:
```
sudo apt-get install ia32-sun-java6-bin
```

---

