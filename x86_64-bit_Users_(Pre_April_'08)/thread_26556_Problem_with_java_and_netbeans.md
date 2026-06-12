---
title: "Problem with java and netbeans"
date: 2005-04-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by capriciousmind on 2005-04-13
I have successfully installed the 32 bit chroot in my ubuntu 64 system thanks to the guide in this very forum.  My next task was to get my jdk working and then netbeans so that I could start doing my homework :-)  I then realized I had a few newb questions.  If I install the jdk in my 64 bit environment and there happens to be a netbeans 64 bit version (which i dont think there is), would the compiled programs run on a 32 bit machine the same?

Well I wanted to get started so I assumed there might be some difficulty, so I installed the I586 jdk from sun on my 32 chroot successfully.  java -version returns the correct info, but when i tried to install netbeans in the chroot it said that it could not execute binary file.  I am quite perplexed by this, can anyone give me some guidance.

---

### Post by alexp on 2005-04-13
capriciousmind,

[QUOTE=capriciousmind]java -version returns the correct info, but when i tried to install netbeans in the chroot it said that it could not execute binary file. I am quite perplexed by this, can anyone give me some guidance.[/QUOTE]

How did you start the installer? If you tried double-clicking: it doesn't work. However, starting the installer from the console should do the job.

Regards,
Alexander

---

### Post by capriciousmind on 2005-04-13
[QUOTE=alexp]capriciousmind,



How did you start the installer? If you tried double-clicking: it doesn't work. However, starting the installer from the console should do the job.

Regards,
Alexander[/QUOTE]

I typed sh "netbeans..." in console.  I was thinking it might have something to do with the chroot, but I am no guru.

---

### Post by alexp on 2005-04-13
capricousmind,
 
[QUOTE=capriciousmind]I typed sh "netbeans..." in console. I was thinking it might have something to do with the chroot, but I am no guru.[/QUOTE]

can you post the complete command output you get when starting the installer from a shell?

Regards,
Alexander

---

### Post by capriciousmind on 2005-04-13
[QUOTE=alexp]capricousmind,
 


can you post the complete command output you get when starting the installer from a shell?

Regards,
Alexander[/QUOTE]

I am at work right now so I don't have access to my box, but I can when i get home later.  It is along the lines of "netbeans(version..): Error executing bin file" and that is pretty much it and does nothing else returns to command line.

---

### Post by FluffyElmo on 2005-04-13
You should be able to run NetBeans without a chroot. Just install a 64-bit JVM and install Netbeans as normal (outside the chroot). You don't need a 64bit version of Netbeans but you'll likely see a performance boost running it under the 64 bit JVM. I don't run Netbeans myself but can try it when I get home if you have problems.

Also, any Java code you compile using the 64bit JVM will run on 32bit systems (or any other platform with a JVM). Briefly: Java code is compiled to a standardized object code. The JVM then converts this object code to native code on the fly at runtime.
 
The exception to this rule are Java programs that use/access non-Java code/libraries. For instance Eclipse and Azureus use a native GUI toolkit (SWT) so you need a 64bit build for them to run.

Hope something in this post helps...good luck and welcome to Java programming:)

---

### Post by capriciousmind on 2005-04-13
[QUOTE=FluffyElmo]You should be able to run NetBeans without a chroot. Just install a 64-bit JVM and install Netbeans as normal (outside the chroot). You don't need a 64bit version of Netbeans but you'll likely see a performance boost running it under the 64 bit JVM. I don't run Netbeans myself but can try it when I get home if you have problems.

Also, any Java code you compile using the 64bit JVM will run on 32bit systems (or any other platform with a JVM). Briefly: Java code is compiled to a standardized object code. The JVM then converts this object code to native code on the fly at runtime.
 
The exception to this rule are Java programs that use/access non-Java code/libraries. For instance Eclipse and Azureus use a native GUI toolkit (SWT) so you need a 64bit build for them to run.

Hope something in this post helps...good luck and welcome to Java programming:)[/QUOTE]

Thank you very much, your post was very helpful.  And I must say out of the many distros that I have tried to learn linux with and ran back to windows, Ubuntu is by far the best.  I love the ubuntu community.  I have gotten nothing but swift and precise responses.  Ubuntu is gonna be the one that gets me over the hump.

---

### Post by capriciousmind on 2005-04-13
Update: 
I deleted the java install in the chroot and installed the 64 bit version but when i try to install the netbeans.bin file I still get the same error message.

@xalien:~/Desktop$ sh net*
netbeans-4_0-bin-linux.bin: netbeans-4_0-bin-linux.bin: cannot execute binary file

any more ideas?

---

### Post by FluffyElmo on 2005-04-13
Hmm, I just tried it and it worked for me. Maybe check to see if the download was corrupted? Try the MD5 sum, if they don't match you'll have to download the install package again. Run:
```
md5sum netbeans-4_0-bin-linux.bin
```

The MD5 sums are listed on the netbeans download page, when I run it I get:
```
4889369dbaf31b77759d574ce2c42c4e  netbeans-4_0-bin-linux.bin
```
 
If they match let me know and we'll have to think of something else:)

---

