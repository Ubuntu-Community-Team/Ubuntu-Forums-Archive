---
title: "which java version do I have?"
date: 2005-10-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by funkenstein on 2005-10-27
I followed [_this_]("http://ubuntuforums.org/showthread.php?t=70428") guide with no errors, but when I try to find out what java version I have, I get:
```
me@mybox:~$ java -version
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) 64-Bit Server VM (build Blackdown-1.4.2-02, mixed mode)

``` when I look into /usr/lib I get:
```
me@mybox:~$ ls /usr/lib/j<tab>
j2re1.5-sun/ j2se/        jni/         jvm/

``` 
Can anyone help me please / what other info do you need to help me?

---

### Post by Sykil on 2005-10-27
Hrm, you should get 1.5.0_05.

Try this:
```
sudo update-alternatives --config java
```

And then choose the right one. java -version should then give you
```
java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_05-b05, mixed mode)
```

---

### Post by funkenstein on 2005-10-27
dude....
```
me@mybox:~$ java -version
java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_05-b05, mixed mode)

```

I could kiss you. :D

---

