---
title: "Noob question - can't find linux-headers to match kernel"
date: 2009-04-17
forum: x86 64-bit Users
---

### Post by krakan on 2009-04-17
Hi all,

I've tried so many searches over three days I'm going to go utterly mad if I don't ask someone instead. This is also a cross-platform problem (mine, not the distro!) in that I ran into the exact same problem in Debian and Centos, so I know this has to be something I'm doing wrong..

I'm installing VMWare server 2.0 onto a 64-bit AMD server which I'm renting from a hosting company. This is a proof of concept project.

Obviously I need the header files for my kernel in order to install VMWare. The version of my currently-running kernel, according to uname -r is: 2.6.21.27-20090324a

Problem is, there isn't even a remotely similar version of linux-headers or linux-source available, at least as far as aptitude is able to determine. All the versions referred to when simply issuing apt-get install linux-headers are 2.6.24 or up

Having tried apt-get dist-upgrade I'm a little unsure of where to go now! I've tried every avenue I can think of, but cannot understand why no available versions of these packages match my running Kernel?

Has anyone encountered this before, and is it something obvious I'm missing?

It's driving me mad, all comments appreciated!

---

### Post by Bachstelze on 2009-04-17
> **krakan said:**
> The version of my currently-running kernel, according to uname -r is: 2.6.21.27-20090324a

How did you install that kernel? It is definitely not a standard Ubuntu one.

---

### Post by krakan on 2009-04-17
The server is preinstalled with it, unfortunately. As it's a hosted server, I'm a little restricted by what is available (insofar as I have no physical access to the machine, only SSH)

---

### Post by Bachstelze on 2009-04-17
Then you must try and see whether the kernel headers are available for your version *or* install a stock Ubuntu kernel. What is the output if this command?

```
dpkg -l | grep linux-image
```

---

### Post by krakan on 2009-04-17
Hi HymnToLife,

Output is as follows:

```
root@s15340842:/# dpkg -l | grep linux-image
ii  linux-image-2.6.26.8-20081113a        rootserver.1                          Linux kernel binary image for version 2.6.26
ii  linux-image-2.6.27.21-20090324a       rootserver.1                          Linux kernel binary image for version 2.6.27
```

I'm up for installing a stock kernel - as long as it's not too tricky, and the odds of success are good (bearing in mind again that I've only got access via SSH!)

---

### Post by krakan on 2009-04-29
Hi all,

Could anyone point me in the right direction of some information on installing a new kernel? I'm a little out of my depth but this isn't a production server so I don't mind learning the hard way!

---

