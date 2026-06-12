---
title: "Help with Java (the flavor you like) needed"
date: 2008-05-07
forum: x86 64-bit Users
---

### Post by ioniviil on 2008-05-07
I am running a x64 machine. Everything works fine, firefox is stable, the desktop is stable, everything rocks.. but as a java developer, it was a need to install NetBeans and java to start making some good to the world.
I downloaded java from Sun Microsystems (yeah, I am fond to Sun), install it, then went to [www.java.com](www.java.com) to verify my installation (java -version doesn't pleases me because of the odd (to me) way that linux handles java, too many java.bin around, and java.bin is only one of the binaries, there is javaws and others, and they tend to point to different things...). Everything looked fine so I started azureus, ugly people that uses SWT I yelled (the word was not ugly as you might expect), that library is not compiled for x64... I went back to sun, downloaded the version for i386 (I was quite angry already), verified again the installation, fine again, run azureus... It launched!, wow, what a relief (though it was not x64), but wait! is isn't upgrading giving errors?, in fact, it isn't even "connecting" to internet, but if I am connected...mmm... lets try this openjdk after all.... Same procedure as before, and the exact same result...
No connection to internet with azureus!. I wanted to be very sure about this so I ran NetBeans, write up some lines to open a connection to Google, and no response!(of course that NetBeans couldn't either check his updates)... sigh... relax... breath deep... and AAAAAAAAAAAAAAAAAAAARRRRRRRRRRRGGGGGGGGG!!!!!!!! 
Much better now. So, does anyone got any idea?
(Sorry if someone found my little story boring, it was intend to give some humor to this frustrating thing)
Thanks

---

### Post by Sef on 2008-05-07
Have you tried [OpenJDK]("http://ubuntuforums.org/showthread.php?t=774956") to see if it works for you?  To download it, use Add/Remove, Synaptic, or the Terminal.  If you have a problem downloading it, check out the link.

---

### Post by Kilz on 2008-05-07
Try this

```
sudo apt-get inastall lib32nss-mdns
```

---

### Post by ioniviil on 2008-05-07
"Have you tried OpenJDK to see if it works for you?"
Yes Sef, I said that in the post above, i tried it.

Kilz, the package you said, is already installed on my computer.
Oh, I tried reinstalling the package as I wrote this, and it solve the problem!, thank you two very much!^^

---

### Post by jespdj on 2008-05-08
> **ioniviil said:**
> 
I downloaded java from Sun Microsystems (yeah, I am fond to Sun), install it, ...
Why did you not install it from the Ubuntu repository? The newest version of Sun Java (version 6 update 6) is in the Hardy repository.
```
sudo apt-get install sun-java6-jdk
```

---

### Post by phidia on 2008-05-08
> **Sef said:**
> Have you tried [OpenJDK]("http://ubuntuforums.org/showthread.php?t=774956") to see if it works for you?  To download it, use Add/Remove, Synaptic, or the Terminal.  If you have a problem downloading it, check out the link.

I'm still using gutsy (64bit) don't want to update right now since most everything i want is working.

I have tried using the add/remove method to get java but it is still not enabled. For some reason even with a very fast connection java wants to take hours to download.I actually allowed it to do that it completed without errors and i restarted ff but there is no jre working. Java is checked in preferences too.

---

### Post by jamesstansell on 2008-05-08
> **phidia said:**
> I'm still using gutsy (64bit) don't want to update right now since most everything i want is working.

I have tried using the add/remove method to get java but it is still not enabled. .. i restarted ff but there is no jre working. Java is checked in preferences too.

Sun does not provide a 64bit version of the Java plugin for Firefox.  There are some things I've heard you might try, but since I don't run 64-bit yet, I haven't tried them myself, so I hate to suggest them first.

My first suggestion is for you to check out the 64-bit users forum.

---

### Post by phidia on 2008-05-08
> **jamesstansell said:**
> Sun does not provide a 64bit version of the Java plugin for Firefox.  There are some things I've heard you might try, but since I don't run 64-bit yet, I haven't tried them myself, so I hate to suggest them first.

My first suggestion is for you to check out the 64-bit users forum.

That's where this thread is. I have looked at the java sticky here which is locked but essentially has the same method to install java as this thread.

---

### Post by caeroe on 2008-05-08
I can't get Frostwire or Azureus to run since the Hardy upgrade.  I've tried every version of java I can install.

I even attempted ia32-sun-java6-bin, but that just gives the wrong architecture errors.

Frustrating to see the simple things to be such a chore in Ubuntu, like installing software.

---

### Post by jamesstansell on 2008-05-08
> **phidia said:**
> That's where this thread is.
I see that now - that's what I get for hopping between forums too much!
> I have looked at the java sticky here which is locked but essentially has the same method to install java as this thread.

I'll have to look at the sticky again.  It needs to make it clear that Sun doesn't ship a 64-bit plugin.  And it should provide options, or at least links to them, for 64-bit users who are desperate for a Java plugin.

---

### Post by phidia on 2008-05-09
> **caeroe said:**
> I can't get Frostwire or Azureus to run since the Hardy upgrade.  I've tried every version of java I can install.

I even attempted ia32-sun-java6-bin, but that just gives the wrong architecture errors.

Frustrating to see the simple things to be such a chore in Ubuntu, like installing software.

If you don't mind using 32bit firefox there is a method [here]("http://ubuntuforums.org/showthread.php?t=202537&highlight=java") for installing that in 64bit ubuntu and variants.

---

