---
title: "SQLDeveloper problem"
date: 2008-11-16
forum: x86 64-bit Users
---

### Post by MickSulley on 2008-11-16
Hi,

I am running 64 bit Intrepid and I have just installed Oracle-xe and SQLDeveloper.  When I try to start SQLDeveloper I get an error message 
Error: Java home /usr/bin/java is not a J2SE SDK.

When I first started it I was asked for the location of Java -

Type the full pathname of a J2SE installation (or Ctrl-C to quit), the path will be stored in ~/.sqldeveloper/jdk

But I cannot find ~/.sqldeveloper/jdk

From other posts it seemed that it may be set in .sqldeveloper.conf but there was nothing in there, and adding a line

SetJavaHome = /usr/lib/jvm/java-6-sun/jre/bin

does nothing to change it.

Does anyone know where it actually holds the path to java and how I can change it?

I am still learning Linux so it is quite possible that I have missed something obvious.

Thanks

Mick

---

### Post by Sef on 2008-11-17
Did you install the 64-bit version of Java?

---

### Post by MickSulley on 2008-11-17
I think I have 64 bit java, how can I tell?  java -version gives -

mick@mick-laptop:~$ java -version
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) 64-Bit Server VM (build 11.0-b15, mixed mode)


If I run update-alternatives --config java I get - 

mick@mick-laptop:~$ update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/jvm/java-6-sun/jre/bin/java
 +        2    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          3    /usr/bin/cacao

Press enter to keep the default[*], or type selection number: 

But changing the default makes no difference when I start SQLDeveloper

---

### Post by Sef on 2008-11-17
How did you install Java?

---

### Post by MickSulley on 2008-11-17
I installed through Synaptic

I think (though by no means certain) that the problem is that I don't know how to tell SQLDeveloper which one to use.

Thanks
Mick

---

### Post by alekons on 2008-12-05
Put the following lines in .profile or .bascrc 

export JAVA_HOME=/apps/jdk1.5.0_14   <--which is you java installation
export PATH=$JAVA_HOME/bin:$PATH


log out and login again and it will run

---

### Post by MickSulley on 2008-12-05
I am still getting the same error message.  Have I done it correctly?  This is what I have done - 

to find Java, 

update-alternatives --config java

There are 5 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/jvm/java-6-sun/jre/bin/java
 +        2    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          3    /usr/bin/cacao
          4    /usr/bin/gij-4.3
          5    /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number: 

so I added 

export JAVA_HOME=/usr/lib/jvm/java-6-openjdk/jre/bin/java
export PATH=$JAVA_HOME/bin:$PATH

to etc/profile

but when I run sqlplus.sh I still get -

Oracle SQL Developer
 Copyright (c) 2008, Oracle. All rights reserved.  

Reading configuration from: /home/mick/SQLDeveloper/sqldeveloper/sqldeveloper/bin/sqldeveloper.conf
Error: Java home /usr/bin/java is not a J2SE SDK.
Running SQL Developer under a JRE is not supported.

If the Java VM specified by the SetJavaHome is actually a full J2SDK installation
then add 'SetSkipJ2SDKCheck true' to /home/mick/SQLDeveloper/sqldeveloper/sqldeveloper/bin/sqldeveloper.conf


Any ideas????

---

### Post by berteipc on 2009-01-15
follow this my guide:

[http://fucinatecnica.blogspot.com/2009/01/install-oracle-sql-developer-on-ubuntu.html]("http://fucinatecnica.blogspot.com/2009/01/install-oracle-sql-developer-on-ubuntu.html")

and resolve all your problem

mb

---

### Post by jespdj on 2009-01-15
> **MickSulley said:**
> export JAVA_HOME=/usr/lib/jvm/java-6-openjdk/jre/bin/java
This is incorrect; JAVA_HOME should point to the JRE directory, not to the java executable. Try this:
```
export JAVA_HOME=/usr/lib/jvm/java-6-openjdk
```
Log out and back in again to make sure that it's activated.

---

