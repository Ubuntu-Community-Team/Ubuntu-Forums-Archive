---
title: "build-essential madness"
date: 2007-12-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Ouoertheo on 2007-12-07
I've been switching back and forth between windows and ubuntu studio 64 for about 3 hours straight trying to get the dependencies to install so I can build my wifi drivers. 
So it comes down to me trying to install g++-4.2 and not being able to because libstdc++6-4.2-dev needs to be installed... well I can't install libstdc++6-4.2-dev without freaking g++-4.2 installed. 
So as I'm smashing my face onto my keyboard from the sheer insanity of linux madness, I'm slowly losing hope of ever having a linux system run smoothly.

Someone please help and explain an easy way to get a build environment for my wireless drivers that doesnt involve infinite dependency loops. Preferably while I still have a keyboard and a face that are not fused together.

---

### Post by Yellow Pasque on 2007-12-07
Have you tried going to System -> Administration -> Software Sources
and disabling all sources except the install CD?

That way, you can use your install CD to install packages.

Out of curiosity, what wifi do you have?

---

### Post by jpkotta on 2007-12-08
Works fine for me.

```
sudo aptitude install g++-4.2
```

You could try downloading the packages from packages.ubuntu.com and installing them manually.

```
sudo dpkg -i /path/to/package.deb
```

---

### Post by Ouoertheo on 2007-12-09
I thank your for your replies, it turned out that I had a corrupted libstd install somehow. So after trying all that you posted here (without any luck) I decided to stop being lazy and drag my computer to my router and connect it via cable. So I did manage to get my build environment installed.

But unfortunately that didn't fix my problem.

This is what it is doing when i run make.

ouoertheo@frostbite:~/Desktop/compat-wireless-2.6$ sudo make
[sudo] password for ouoertheo:
make -C /lib/modules/2.6.22-14-rt/build M=/home/ouoertheo/Desktop/compat-wireless-2.6 modules
make: *** /lib/modules/2.6.22-14-rt/build: No such file or directory.  Stop.
make: *** [modules] Error 2
ouoertheo@frostbite:~/Desktop/compat-wireless-2.6$ 

Does anyone have any suggestions as to how to compile the wireless drivers?

---

### Post by Ouoertheo on 2007-12-09
BTW, the network driver is for the ABS NW-200-USB

---

### Post by jpkotta on 2007-12-09
Don't run make as root.  Just run the "make install" part as root.  You probably don't have the kernel headers installed.  
```
sudo aptitude install linux-headers-$(uname -r)
```

---

