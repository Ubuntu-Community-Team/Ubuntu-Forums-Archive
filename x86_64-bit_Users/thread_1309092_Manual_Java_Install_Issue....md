---
title: "Manual Java Install Issue..."
date: 2009-11-01
forum: x86 64-bit Users
---

### Post by xdemo on 2009-11-01
demo@foxy:~$ cd /opt/java/64
demo@foxy:/opt/java/64$ sudo ./jre-6u16-linux-x64.bin
demo@foxy:/opt/java/64$ 


As you can see nothing happens... why isn't it running? i have tried to download the file several times, in case of damaged download etc etc.

i've followed everything upto step 8 on this tutorial (for 64bit install of course):
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Any suggestions?

EDIT: 9.10 karmic + just removed all previous java packages of older versions etc.

---

### Post by Yellow Pasque on 2009-11-01
Is there a reason you're not using the sun-java6 packages provided in the repository?

---

### Post by oldos2er on 2009-11-01
Did you make the *bin file executable? 
```
sudo chmod a+x jre-6u16-linux-x64.bin
```

---

### Post by Theriex on 2009-11-02
I've followed the guide for 64 bit and it worked flawlessly.  Just make sure you do everything in the guide 'according to your system' and it will work.

---

### Post by xdemo on 2009-11-02
> **Temüjin said:**
> Is there a reason you're not using the sun-java6 packages provided in the repository?

Yes, the x64 sun-java isn't the latest version in software manager

```
demo@foxy:~$ cd /opt
demo@foxy:/opt$ sudo mkdir java
[sudo] password for demo: 
mkdir: cannot create directory `java': File exists
demo@foxy:/opt$ cd java
demo@foxy:/opt/java$ ls
64
demo@foxy:/opt/java$ cd /64
bash: cd: /64: No such file or directory
demo@foxy:/opt/java$ cd 64
demo@foxy:/opt/java/64$ ls
jre-6u16-linux-x64.bin
demo@foxy:/opt/java/64$ sudo chmod 755 /opt/java/64/jre-6u16-linux-x64.bin
demo@foxy:/opt/java/64$ sudo ./jre-6u16-linux-x64.bin

```

After i type sudo ./jre-6u16-linux-x64.bin nothing happens o.O
Have also tried 
sudo chmod a+x jre-6u16-linux-x64.bin as you suggested, but no difference.

I have reinstalled 1.6.0_15 for time being, but i cannot enable certain graphics modes without the latest version for some online games. Rather annoying x_x

---

### Post by Yellow Pasque on 2009-11-02
You could grab the Java 6u16 packages from Jaunty. They probably weren't upgraded in Karmic because of developmnet deadlines and such.

---

### Post by stchman on 2009-11-02
To install Java in Ubuntu do the following:

```
sudo apt-get -y install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin
```

This will install the JRE, JDK, and browser plugin.  This will work for both 32 and 64 bit.

---

