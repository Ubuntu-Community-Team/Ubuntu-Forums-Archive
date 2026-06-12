---
title: "JRE troubles"
date: 2009-07-17
forum: x86 64-bit Users
---

### Post by eram on 2009-07-17
OK, I'm posting a new thread for this because the other ones in this section concerning java seem to be caused by other problems.

So my problem simply state is that when I run ```
java FileName.class
``` in the terminal, I get this error: > Exception in thread "main" java.lang.NoClassDefFoundError: EmployeeTest/java
Caused by: java.lang.ClassNotFoundException: EmployeeTest.java
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: EmployeeTest.java.  Program will exit.
Note* in this case, the file name is EmployeeTest.class but I get the same thing with any other .class I compile.

Now to make this problem stranger, I can still compile .java files just fine using the command ```
javac FileName.java
``` and I can still view all java on firefox just fine! :confused: Weird isn't it.

Anyways, I thought I'd throw this out here and see if someone can lend me a hand in fixing this problem. I really don't have any idea what could even be the source of this.

Thanks.:D

EDIT:
I forgot to add this, but my OS is Ubuntu 9.04 64-bit, in case that helps.

---

### Post by prshah on 2009-07-17
> **eram said:**
> ```
java FileName.class
``` 

When trying to execute a class file with Java, don't give any extension. Just use ```
java EmployeeTest
```. It should automatically find the EmployeeTest class file. Note that classnames and filenames are case sensitive (in Windows, filename case does not matter, though classnames are case sensitive).

If it cannot find the class, ensure that the base path to your class is present in your CLASSPATH environment variable. If your class files are in the current working directory, you can add it to your classpath with ```
export CLASSPATH=$CLASSPATH:.
```

---

### Post by eram on 2009-07-17
> **prshah said:**
> When trying to execute a class file with Java, don't give any extension. Just use ```
java EmployeeTest
```. It should automatically find the EmployeeTest class file.

Wow, I feel so silly. That did the trick. Thanks man!!!

Is there a way to add reputation or something like that for people that helped you? I don't see anything here like I do on most forums.

---

### Post by Yellow Pasque on 2009-07-17
> Is there a way to add reputation or something like that for people that helped you? I don't see anything here like I do on most forums.
We used to have a thanking system. It caused issues with the database, so it was removed.

I can't speak for anyone else, but for me, when I see, "Problem Solved. Thank you.", it's sufficient.

---

### Post by eram on 2009-07-17
Oh well. In that case a big Thank You will have to be enough for him. :D

---

