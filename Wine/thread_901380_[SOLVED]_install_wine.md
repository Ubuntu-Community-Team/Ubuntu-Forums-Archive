---
title: "[SOLVED] install wine"
date: 2008-08-26
forum: Wine
---

### Post by cowboyup6983 on 2008-08-26
i have ubuntu 8.04 and i am a newbie. i want to install wine so that i can install some windows applications like convertxtoDVD. can anyone tell me how to get started

---

### Post by SpaceMaster on 2008-08-26
open the terminal and type:

```
sudo apt-get install wine
```.
you may have to enable "Multiverse" in Software Sources.

---

### Post by qstraza on 2008-08-26
Also you could to this:
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update
sudo apt-get install wine
```
So you will have the latest version.

---

### Post by cowboyup6983 on 2008-08-26
> **SpaceMaster said:**
> open the terminal and type:

```
sudo apt-get install wine
```.
you may have to enable "Multiverse" in Software Sources.

okay thanks now how do i enable multiverse in software sources.

---

### Post by cowboyup6983 on 2008-08-26
> **SpaceMaster said:**
> open the terminal and type:

```
sudo apt-get install wine
```.
you may have to enable "Multiverse" in Software Sources.

i used this site
[http://www.ubuntugeek.com/how-to-enable-the-universe-and-multiverse-repositories-in-ubuntu-804-hardy.html](http://www.ubuntugeek.com/how-to-enable-the-universe-and-multiverse-repositories-in-ubuntu-804-hardy.html)

and everything was already check off, so i guess it should be ready for me to install and application. how do i get started lets say if i have an EXE file.

---

### Post by qstraza on 2008-08-26
in terminal type:
```
wine xxx.exe
```

Or just click on exe and set so linux will autoaticly start wine for .exe

---

### Post by cowboyup6983 on 2008-08-26
> **qstraza said:**
> in terminal type:
```
wine xxx.exe
```

Or just click on exe and set so linux will autoaticly start wine for .exe

got it. now just have to make sure the application works, i need to test with an AVI file, thanks so much, i would love to be able to install COD4, but i doubt u can. 

look at some sites seems very complicated

---

### Post by cowboyup6983 on 2008-08-26
> **cowboyup6983 said:**
> got it. now just have to make sure the application works, i need to test with an AVI file, thanks so much, i would love to be able to install COD4, but i doubt u can. 

look at some sites seems very complicated


problem solved except, of course COD4

---

### Post by aoanla on 2008-08-26
Well, if you install Steam, I can't see it should be hard to get COD4 installed... and you can always ask for help here if you get stuck.

---

### Post by cowboyup6983 on 2008-08-26
> **aoanla said:**
> Well, if you install Steam, I can't see it should be hard to get COD4 installed... and you can always ask for help here if you get stuck.

whats steam!

---

