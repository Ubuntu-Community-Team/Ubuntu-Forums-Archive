---
title: "Upgrade from 32 bit to 64 bit OS"
date: 2007-04-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by maiios on 2007-04-02
I installed Ubuntu Server 6.10 on a server that I got from a friend. Just recently I realized that it is actually a 64 bit machine, but I installed the 32 bit version of US on the machine. Is it possible to simply update the repositories to move between versions? If not, can I install from disk over the pervious installation? I have some stuff already installed and I would prefer not to have to install the stuff again.

Sorry if these are dumb questions but I have never really delved into 64bit before.

Brian

---

### Post by kinson on 2007-04-02
Not too sure about what you just asked (I'm fairly new myself), but just FYI, there's nothing wrong with you using the 32bit version on your 64bit pc. I'm using a 32bit version on my AMD64bit as well :)

Cheers,
Kinson

---

### Post by maiios on 2007-04-02
I know there is nothing wrong with it, but I figure if I have the technology that I might as well harness it!

Anyway, to clarify my question...
I have a 64 bit machine that I am currently running a 32 bit version of Ubuntu on. What is the best way of upgrading the OS to the 64 bit version?

---

### Post by prince_niceguy on 2007-04-02
If you are going to use it as a server then it is better to move to 64 bit as it has better performance figures against 32 bit.

Except for you /home other portion would have to be reformatted. But it will be worth.

Check out some of the threads which gives performance numbers. I think one of them is in the sticky too.

---

### Post by maiios on 2007-04-03
So there is no way to upgrade without formatting?

---

### Post by in_flu_ence on 2007-04-03
I think there is no way not to reformat 'cause the lib for 64bit stores at different places and basically there are some changes to the file structure.

Maybe if you are good, you can take the time to install bits and pieces to make things work but to me, i think it will take too much time.

---

### Post by prince_niceguy on 2007-04-05
you will have to format the root partition, /usr, /lib partitions. Others which stores just your configurations like /opt or /home can remain untouched. Just make sure you mount the with /home or /opt and do not format them during installation.

---

