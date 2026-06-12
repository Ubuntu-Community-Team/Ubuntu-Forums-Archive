---
title: "Erron when running ./configure: &quot;X11 environment not found&quot;"
date: 2007-04-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by shane25119 on 2007-04-10
Hi everyone,
                  I just setup a AMD64 bit system which completely rocks.

I am trying to setup nspluginwrapper so I can bemuse myself with videos on YouTube.  When I try to run ./configure I get this error:

```
shane@geno:~/Desktop/nspluginwrapper-0.9.91.4$ ./configure 
X11 environment not found

```

I have tried googling- I have tried installing headers (I'm not really sure what I am doing there).  It's not working.  Initially I had gotten GLIB 2.0 environment not found" and I should have kept that page... but I found a howto online that told me how to fix that by adding a couple of packages from Synaptic.. then I ran into the X11 problem.

I'm sure it's just a package or two... but I am completely stuck.... :-(

Shane

---

### Post by Kilz on 2007-04-11
> **shane25119 said:**
> Hi everyone,
                  I just setup a AMD64 bit system which completely rocks.

I am trying to setup nspluginwrapper so I can bemuse myself with videos on YouTube.  When I try to run ./configure I get this error:

```
shane@geno:~/Desktop/nspluginwrapper-0.9.91.4$ ./configure 
X11 environment not found

```

I have tried googling- I have tried installing headers (I'm not really sure what I am doing there).  It's not working.  Initially I had gotten GLIB 2.0 environment not found" and I should have kept that page... but I found a howto online that told me how to fix that by adding a couple of packages from Synaptic.. then I ran into the X11 problem.

I'm sure it's just a package or two... but I am completely stuck.... :-(

Shane

Most people who go the nspluginwrapper rout use rpm's and use alien to convert them to .deb files. Be aware that the nspluginwrapper does not work with the java plugin.
You also have the alternative of running a 32fit Firefox with java flash and mplayer plugins. link in my signature.

---

### Post by shane25119 on 2007-04-11
I'll give that a go- I'm just a little worried that my ability to compile and install pretty much anything might be messed up....

---

### Post by Kilz on 2007-04-11
> **shane25119 said:**
> I'll give that a go- I'm just a little worried that my ability to compile and install pretty much anything might be messed up....

No, compiling is a real pain. It isnt always a smooth easy prossesss and errors pop up.

---

### Post by wolkengold on 2007-07-24
install xorg-dev and everything should be fine

---

