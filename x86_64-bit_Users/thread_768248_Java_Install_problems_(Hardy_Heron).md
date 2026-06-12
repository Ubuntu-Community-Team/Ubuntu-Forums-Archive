---
title: "Java Install problems (Hardy Heron)"
date: 2008-04-26
forum: x86 64-bit Users
---

### Post by Sef on 2008-04-26
I am following [John Michael Kane's guide]("http://ubuntuforums.org/showthread.php?t=765428") on how to install Java, but I run into a problem.

When I get to ```
cp -r -p ./jrel.6.0_05/* /usr/local/java32', I get this message:  cp: cannot stat `./jrel.6.0_05/*
``` : No such file or directory

The file exists 

```
root@jokat:~/Desktop# mkdir /usr/local/java32
mkdir: cannot create directory `/usr/local/java32': File exists
```

UPDATE:

I figured out my problems with the above, but now I have a problem with this line:

```
cd /usr/lib32/firefox32/plugins/
bash: cd: /usr/lib32/firefox32/plugins/: No such file or directory
```


What do I need to do to get java installed or is there an easier way to install java?

---

### Post by FredB on 2008-04-26
Just search for openjdk in synaptic...

---

### Post by Sef on 2008-04-26
That worked, but it is not as current as java, it seems.  I can't wait till Java is open source and a 64-bit version is out.

---

