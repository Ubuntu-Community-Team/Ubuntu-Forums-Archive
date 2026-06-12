---
title: "Sql"
date: 2009-01-27
forum: x86 64-bit Users
---

### Post by vandorjw on 2009-01-27
Hi,

I want to install mySLQ on my system, play around with it, learn how it works, but I don't really know which file to get.

I quickly check the synaptic package manager and there was nothing there.
"sudo apt-get install sql" didn't recommend anything either.

[http://dev.mysql.com/downloads/mysql/5.1.html#downloads](http://dev.mysql.com/downloads/mysql/5.1.html#downloads)  was the site I looked at.

Linux (AMD64 / Intel EM64T) seems right to me.
But I am became unsure when I saw "Linux (IA64)"

I believe I need the first...see my signature.

Edit: I figured it out, thanks for reading :)
[http://www.linuxforums.org/forum/peripherals-hardware/35963-cpu-naming-schemes-x86-386-486-586-amd-64-ia64-em64t.html](http://www.linuxforums.org/forum/peripherals-hardware/35963-cpu-naming-schemes-x86-386-486-586-amd-64-ia64-em64t.html)

Cheers - CC7

---

### Post by vandorjw on 2009-01-27
Problem Solved :)
```

sudo apt-get install mysql-server-5.0

```
Cheers - CC7

---

### Post by bukwirm on 2009-01-27
There should be mysql-server and mysql-client packages included in the repositories, which is probably easier than compiling them from source.

---

### Post by cariboo on 2009-01-27
The package you are looking for is mysql-server-5.0. IF you can find a package on the internet, 99% of the time if you search for the same package in Synaptic you will find it.

Mysql starts automatically so you should never have to issue a command  to start it. When you install mysql using synaptic, it will ask you to create a password for root. This password is only for mysql it has no effect on the rest of the installation.

I would suggest that while you are installing mysql, you should also download the mysql-doc-5.0, as it comes in handy when you are learning how it works. 

Jim

---

