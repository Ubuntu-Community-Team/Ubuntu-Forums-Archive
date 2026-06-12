---
title: "gcc 4.3.1"
date: 2009-03-18
forum: x86 64-bit Users
---

### Post by JanRa on 2009-03-18
Hello,

I need to have gcc 4.3.1 to be able to compile OpenFoam on my laptop. However I can not find it in my repositories. Is there a simple way to install it (i am not an advanced user)?

greetings,

Jan

---

### Post by stchman on 2009-03-18
> **JanRa said:**
> Hello,

I need to have gcc 4.3.1 to be able to compile OpenFoam on my laptop. However I can not find it in my repositories. Is there a simple way to install it (i am not an advanced user)?

greetings,

Jan

gcc 4.3.1 is in the Intrepid repositories.

What is so special about gcc 4.3.1 over older versions?

---

### Post by JanRa on 2009-03-18
How do i get it from the intrepid repository? 

I am trying to compile Openfoam and get lots of errors. The manual says you need gcc 4.3.1. So that is why I would like to get it running.

Thanks for the help

Jan

---

### Post by 3Miro on 2009-03-18
> **JanRa said:**
> How do i get it from the intrepid repository? 

I am trying to compile Openfoam and get lots of errors. The manual says you need gcc 4.3.1. So that is why I would like to get it running.

Thanks for the help

Jan

System -> Administration -> Synaptic, hen search for gcc.

Everything in Ubuntu is installed via either Add/Remove Programs or the package manager.

---

### Post by JanRa on 2009-03-19
> **3Miro said:**
> System -> Administration -> Synaptic, hen search for gcc.

Everything in Ubuntu is installed via either Add/Remove Programs or the package manager.

That is what I did and it installs the 4.2 version. I need the 4.3 version.

---

### Post by stchman on 2009-03-19
> **JanRa said:**
> How do i get it from the intrepid repository? 

I am trying to compile Openfoam and get lots of errors. The manual says you need gcc 4.3.1. So that is why I would like to get it running.

Thanks for the help

Jan

First off you need to have Intrepid.  Are you running Hardy?  If yes to Hardy then that is gcc 4.2.4.

The package gcc is installed by default in Ubuntu.  You do however need the build essential package for all the header files.

```
sudo apt-get install build-essential
```

Without it you won't be able to compile.

---

