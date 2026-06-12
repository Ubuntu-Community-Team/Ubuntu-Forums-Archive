---
title: "Java Sun 1.5.0_05 x86_64 VM Memory leak"
date: 2005-11-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by pablovp on 2005-11-10
I installed Sun Java VM 1.5.0_05(the last version) on my breezy AMD64.

I noted that Eclipse consumes a lot of memory.

I know that java applications tend to be memory hunger but this is not normal, i have 512MiB of ram and a swap space of  1 GiB(i extended my swap space due to this problem), and half was filled running eclipse.

Azureus and other java apps are behaving the same way.

I tested installing a 32 bits chroot, since that im using java vm 32bits with no problems with memory use.

I think there is a bug on Sun Java VM 1.5.0_05 for AMD64, if you have the same problem please reply to this topic.

Thanks

---

### Post by jvictor on 2005-11-10
Which version of eclipse are u running ? I run eclipse 3.1 x86_64 on Sun java 1.5.0_05  I really dont find such issues , quite intersting to see this happen

---

### Post by pablovp on 2005-11-10
I've tried 3.2M2(development version) and 3.1

But all had the same problem.

---

### Post by Yagisan on 2005-11-11
[QUOTE=pablovp]I think there is a bug on Sun Java VM 1.5.0_05 for AMD64, if you have the same problem please reply to this topic[/QUOTE]Yes there is a memory leak in the sun jvm. I discovered this after leaving azureus running for an extended period of time (read +week plus), and seeing that the jvm had used 1.5GB of ram. My suggestion is to try another jvm if possible, eg blackdown, ibm, gcj, sable etc

---

### Post by linuxted on 2005-11-11
[QUOTE=Yagisan]Yes there is a memory leak in the sun jvm. I discovered this after leaving azureus running for an extended period of time (read +week plus), and seeing that the jvm had used 1.5GB of ram. My suggestion is to try another jvm if possible, eg blackdown, ibm, gcj, sable etc[/QUOTE]

I added Universe & Multiverse and then added the Java jre.  Whenever I pull up a page with Java it crashes.

It is quite frustrating.

---

### Post by pablovp on 2005-11-11
I dont know if is a SWT or JVM issue...

I submited a bug at Sun describing this problem, waiting for their confirmation.

---

### Post by Yagisan on 2005-11-12
[QUOTE=linuxted]I added Universe & Multiverse and then added the Java jre.  Whenever I pull up a page with Java it crashes.

It is quite frustrating.[/QUOTE]IIRC There is no (Sun) Java plugin for 64bit browsers. I hope you added the java package by using the make-jpkg app, installed of letting suns installer crap all other your system, otherwise there is a good chance the sun jvm has loaded libaries in the wrong place (it assumes all linux systems are red hat systems)

---

### Post by Ryba on 2005-11-13
[quote=pablovp]I dont know if is a SWT or JVM issue...

I submited a bug at Sun describing this problem, waiting for their confirmation.[/quote] I'm still using _03 (as opposed to _05) version of the 1.5 jdk but I do know that SWT has some major memory leaks in it. It is not an eclipse or azureus problem other then that they are using the SWT api.

I develop a lot of stuff using SWT myself and their stuff is just leaky. I first noticed it when using their clipboard api with leaks everything that goes into the clipboard (so if you do ctrl-a in firefox and then look at it with the swt application you will have just leaked every byte of that info). They have several other little areas where this happens as well. I would submit the issue to the swt team if I were you. I can only hope that if enough people complain they will put in a real effort into fixing it other then the (i'll take a look at it .. 2 months later it is still on the todo list for them).

---

### Post by JuanC on 2005-11-13
Anyone knows when sun will include firefox plugin to run applets in firefox for amd64?

---

### Post by eDave on 2005-11-17
Just as a side note, Java being leaky?... Isn't the Java memory model specifically built around preventing this from happening by using garbage collection, etc, or is there something I'm missing?

---

### Post by Yagisan on 2005-11-17
[QUOTE=eDave]Just as a side note, Java being leaky?... Isn't the Java memory model specifically built around preventing this from happening by using garbage collection, etc, or is there something I'm missing?[/QUOTE]The memory model itself is supposed to prevent this for java apps in a jvm, it is just that suns current jvm for amd64 has a leak.

---

### Post by pablovp on 2005-11-25
Added a new bug on eclipse (SWT issue) about memory leak for amd64.

The bug can be found on this link:

[https://bugs.eclipse.org/bugs/show_bug.cgi?id=118124](https://bugs.eclipse.org/bugs/show_bug.cgi?id=118124)

---

### Post by vektor on 2005-11-26
Hi all, I'm an SWT developer.  Any reproducable steps for leaks would be awesome.  If you're really hardcore, you can run SWT applications under valgrind, but unfortunately you'll need to use gij/gcj to run.  Here is the suppression list I use for valgrind testing SWT apps under gij:

  [http://vektor.ca/eclipse/gcj.supp](http://vektor.ca/eclipse/gcj.supp)

The Eclipse bugzilla is best for discussion of potential leaks, or on IRC at #eclipse-dev, #debian-java, or #eclipse on irc.freenode.net.

---

### Post by vektor on 2005-11-26
[QUOTE=Yagisan]The memory model itself is supposed to prevent this for java apps in a jvm, it is just that suns current jvm for amd64 has a leak.[/QUOTE]

Java applications can easily leak, and often do.  Usually it happens when you have some large data structure, say a model of a Java class you're editing in Eclipse, and one plug-in somewhere keeps a reference to it in a linked list and never nulls it when it's done with it.  This memory is then kept around for the life of the application.

These leaks are the most common.  You can also leak through any API that uses JNI methods to access native stuff.  For example, SWT is a wrapper around GTK+.  Any time a programmer neglects to dispose an SWT widget, the memory used by GTK+ is also leaked, even if Java has garbage collected the Java memory for this widget.

---

### Post by sotua on 2005-11-29
[QUOTE=pablovp]
I think there is a bug on Sun Java VM 1.5.0_05 for AMD64, if you have the same problem please reply to this topic.
[/QUOTE]

I noticed that when I run eclipse-amd64 and jboss with the amd64 sun jvm, the virtual memory usage is alarmingly lower than with the i586 version.

Jboss: amd64 -> 1890MB, i586 -> 760MB
eclipse: amd64 -> 1750MB, i586 -> 527MB
tomcat 5.5: amd64-> 1395MB!!!, i586 -> 281MB

Now I'm going to try if the system slows to a crawl if I run the junit test within eclipse that hits both the jboss server and the tomcat server :)

---

