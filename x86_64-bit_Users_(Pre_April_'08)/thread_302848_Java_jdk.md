---
title: "Java jdk"
date: 2006-11-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by fool on 2006-11-19
Hi

I am quite new to Ubuntu, and I think I finally have a stable x64 version.

I need to install the java jdk1.5 and would like to use it with netbeans. Any advice would be greatly appreciated, especially on which java version, either x86 or x64 version and where to get them from.

---

### Post by hod139 on 2006-11-21
I'm not sure about the 64bit version, but a 32bit version exists in the repositories.  See this [thread]("http://ubuntuforums.org/showthread.php?t=201378") (and ignore the eclipse part unless you want eclipse).

---

### Post by incubus on 2006-11-21
It should be easy to install the package from the NetBeans website.

First, have you installed Sun's Java JDK?  As a hint:
```

$ apt-cache search java |grep sun

```
...searches for the packages you can install.

Now, to install JDK:
```

$ sudo apt-get install sun-java5-jdk

```

Usually what people get wrong is that they forget to run:
```

$ sudo update-alternatives --config java
$ sudo update-alternatives --config javac

```
(this is to make your system use Sun's java instead of the GNU alternatives. so when asked, choose the sun's executable)

Get NetBeans from their website:
[http://www.netbeans.com/](http://www.netbeans.com/)

The package comes as a .bin file, so you have to make it executable before running it.
```

$ chmod +x netbeans-5_5-linux.bin
$ ./netbeans-5_5-linux.bin

```


Let us know if it doesn't work, I can try to install it here as well.

incubus

EDIT: Check this thread, by the way:
[http://ubuntuforums.org/showthread.php?t=119303&page=2&highlight=netbeans](http://ubuntuforums.org/showthread.php?t=119303&page=2&highlight=netbeans)

And the NetBeans instructions:
[http://www.netbeans.org/community/releases/55/install.html](http://www.netbeans.org/community/releases/55/install.html)

---

### Post by smolko on 2006-12-30
Everything went OK by me. I've tried the installation on a default amd64 6.10 system. There was no need to configure the alternatives for java and javac, although I've had to do this on my notebook (because of some alternative VM, I just can't recall its name... ;) ).

---

### Post by Unterseeboot_234 on 2006-12-30
Everything works fine except the java plug-in, that's where there is much confusion. NetBeans works because it slams the pathname after "javac" to your source code. Problems creep up when you want to javac and/or java from the terminal because you have two library jars that need to compile together. The other part of the story is the java plug-in is only 32-bit. No 64-bit plug-in avaialble. Sun makes a point of NOT including any java plug-in for the 64-bit SDK.

[http://www.ubuntuforums.org/showthread.php?t=319138]("http://www.ubuntuforums.org/showthread.php?t=319138")

The above link is an excellent resource if you need a newer jdk running. If you go for the upgrade sometime in the future, keep in mind about your browser. I use Swiftfox. There are some restrictions about including Swiftfox or altering the browser code, but it is the fastest browser on 64-bit. So, I've learned to keep the broswer links very well installed and documented in my mind so I can have the other add-ons like Flash, along with java-webstart/plug-in. Use the above link after you learn what NOT to change to make a custom JDK so you can do java and still have a browser to test it in. If you install Swiftfox, don't install anything else. Don't try the custom-built 32-bit Firefox. Java running in a browser is an important function that you don't want to lose. Thoroughly familiarize yourself about which browser is running what plug-ins to save yourself some time.

---

### Post by Unterseeboot_234 on 2006-12-30
Didn't mean to double post. Let me leave it with this thought by typing over the above paragraph. java is cool. It runs in its own environment and can't hurt ubuntu. It's when you try to build software packages using downloaded c++/python/ruby libraries that you break ubuntu.

---

