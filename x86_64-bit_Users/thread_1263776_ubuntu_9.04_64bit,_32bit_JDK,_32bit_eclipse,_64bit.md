---
title: "ubuntu 9.04 64bit, 32bit JDK, 32bit eclipse, 64bit xulrunner - no swt-mozilla-gtk"
date: 2009-09-11
forum: x86 64-bit Users
---

### Post by jinxxik on 2009-09-11
Hello, 

I have this problem, please some java developer with problem knowledge to respond my question.

I have Ubuntu 9.04 desktop 64bit, 32bit Sun JDK manualy installed. Eclipse 3.5 manualy installed, firefox and xulrunner from stable distribution - each I guess are amd64.

I want to make functional SWT Browswer Widget. Eclipse is falling with this exception:

```
 java.lang.UnsatisfiedLinkError: no swt-mozilla-gtk-3550 or swt-mozilla-gtk in swt.library.path, java.library.path or the jar file

eclipse.buildId=I20090611-1540
java.version=1.6.0_13
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=cs_CZ
Framework arguments:  -product org.eclipse.epp.package.jee.product
Command-line arguments:  -os linux -ws gtk -arch x86 -product org.eclipse.epp.package.jee.product 

```

I guess, problem is that 32bit eclipse with 32bit gtk/xulrunner api found 64bit firefox/xulrunner, is possible to coexists 32b and 64b xulrunner's ???

Thank you for your response.

[http://www.eclipse.org/swt/faq.php#browserlinux](http://www.eclipse.org/swt/faq.php#browserlinux)
[http://www.eclipse.org/swt/faq.php#howusemozilla](http://www.eclipse.org/swt/faq.php#howusemozilla)

---

### Post by jinxxik on 2009-11-02
This is solution [http://blog.javaee.cz/2009/11/ubuntu-910-64bit-and-custom-32bit-jdk.html]("http://blog.javaee.cz/2009/11/ubuntu-910-64bit-and-custom-32bit-jdk.html")

---

