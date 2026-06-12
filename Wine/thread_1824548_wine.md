---
title: "wine"
date: 2011-08-13
forum: Wine
---

### Post by raja.genupula on 2011-08-13
i have got some wine1.3 tar.
got extracted and configure wents fine and gave me a message use make to compile 

i have done make 
then got a roll of code checking yes .......


checking whether we need to define __i386__... no


i have seen above message minimum three times and i understand that its not making and doing the same thing . no forward only its rotating there it self with that bunch of code .


       please help me to come out of this . thanks in advance . i wanna install wine .

---

### Post by Toz on 2011-08-13
Is there any particular reason that you want to compile wine 1.3? 

Why not just install it from the ubuntu wine ppa: [https://launchpad.net/~ubuntu-wine/+archive/ppa]("https://launchpad.net/~ubuntu-wine/+archive/ppa")

```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.3
```

---

### Post by uRock on 2011-08-13
Moved to *Wine* sub-forum.

---

### Post by raja.genupula on 2011-08-13
> **Toz said:**
> Is there any particular reason that you want to compile wine 1.3? 

Why not just install it from the ubuntu wine ppa: [https://launchpad.net/~ubuntu-wine/+archive/ppa]("https://launchpad.net/~ubuntu-wine/+archive/ppa")

```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.3
```

no man , its size upto 90mb . i am having slow and limited(3gb per month , ok size not a problem ) internet , my modem going to take roughly 1hr 30 min . thats why i had downloaded a tar .

---

### Post by raja.genupula on 2011-08-13
> **uRock said:**
> Moved to *Wine* sub-forum.

thanks man ,

---

### Post by Toz on 2011-08-14
> **raja.genupula said:**
> no man , its size upto 90mb . i am having slow and limited(3gb per month , ok size not a problem ) internet , my modem going to take roughly 1hr 30 min . thats why i had downloaded a tar .

Ok, but the i386 build is about 37MB: [https://launchpad.net/~ubuntu-wine/+archive/ppa/+build/2669294]("https://launchpad.net/~ubuntu-wine/+archive/ppa/+build/2669294")

---

### Post by raja.genupula on 2011-08-14
so what i can do finally to get wine in my system .

---

### Post by Toz on 2011-08-14
From post #1, you are trying to compile wine 1.3. 

I suggest installing it from PPA (see post #2). You have indicated you do not wish to download that much data.

I can offer no further assistance. Perhaps someone else can assist with troubleshooting your compilation errors.

---

### Post by raja.genupula on 2011-08-14
hmmm i will install from ppa , thanks man .

---

