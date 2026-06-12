---
title: "Netbeans 6"
date: 2007-05-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by kiwinewt on 2007-05-29
Hi,

I looked on here: [http://ubuntuforums.org/showthread.php?t=455114](http://ubuntuforums.org/showthread.php?t=455114) to try find the solution to my problem, so I have been researching...

I am trying to install Netbeans 6 using the .sh script downloaded from their website. First it complained that I had no Java installed. I had both J2SE 5 and 6 installed. I got past this by specifying it manually.

I now get to a point where it brings up an error about not having the right libraries installed (it wants 32-bit, im using ubuntu 64-bit)

Anyone got this working with this error? please help...

Nate

---

### Post by kiwinewt on 2007-05-29
Also, the specific error I am getting is:

java.lang.UnsatisfiedLinkError: /tmp/nbi-17032.tmp: /tmp/nbi-17032.tmp: wrong ELF class: ELFCLASS32

Nate

---

### Post by olafkock on 2007-06-01
I've managed to work around this problem by installing a 32 bit Java VM manually from java.sun.com and pointing the installer to this vm (e.g. set JAVA_HOME prior to running the installer script)

During the installation you can choose the JDK to run netbeans6m9 with. I've chosen the existing ubuntu vm then and netbeans is up and running.

Cheers,
Olaf

---

### Post by LinuxIsInnovation on 2007-12-16
Can you explain what you did..?? I'm a total newbie..

---

### Post by helix_r on 2007-12-16
> **olafkock said:**
> I've managed to work around this problem by installing a 32 bit Java VM manually from java.sun.com and pointing the installer to this vm (e.g. set JAVA_HOME prior to running the installer script)

During the installation you can choose the JDK to run netbeans6m9 with. I've chosen the existing ubuntu vm then and netbeans is up and running.

Cheers,
Olaf

Are you saying that you are using the 32 bit JRE ONLY for the installer. Then, when you configure netbeans, you pointed it to a 64bit JDK?

I really don't understand this. At work, I write java code on a 32 bit windows machine everyday. Then, I compile, package and deploy to 64 bit machines in a datacenter. I've NEVER had a 32 vs 64 bit issue.

How can it make a difference for the netbeans installer? **Bytecode is bytecode, it does not matter what jre runs it. Right?**

---

### Post by LinuxIsInnovation on 2007-12-16
Actually, I mean how do you run netbeans :)
The installer finishes but theres no launcher..

---

### Post by revchris on 2007-12-17
It should be under Programming...thats where mine's at anyway.  Mine just won't run, it looks like it's trying to but there nothing.  Anyone have that problem?  I read a few posts that its compiz-fusion, is that it.

---

### Post by Sportsdude11751 on 2008-01-21
I'm having the same problem, I get it to install fine. But when I go to run it, there's no icon for it. So I go to the /usr/local/netbeans-6.0 directory and run it from there, and it brings up a blank screen. One time though I was able to create a new project.

---

### Post by Sportsdude11751 on 2008-01-21
So I have fixed the problem it appears:


sudo sh netbeans-6.0-linux.sh --javahome /usr/lib/jdk1.6.0_04 

was the command I used, however because of Compiz conflicting errors, I couldn't get the netbeans icon installed, so t launch netbeans I have to go to the /usr/local/netbeans-6.0/bin and launch it from there

---

### Post by stuffelse on 2008-01-31
> **Sportsdude11751 said:**
> So I have fixed the problem it appears:

```

sudo sh netbeans-6.0-linux.sh --javahome /usr/lib/jdk1.6.0_04 
```


that saved my @$$! my code was more specifically

```
./netbeans-6.0-linux.sh --javahome /usr/local/jdk1.6.0_04/
```

but either way, having the proper syntax for the command helped out bigtime!

---

### Post by revchris on 2008-01-31
To get Netbeans to run with compiz I put "export AWT_TOOLKIT=MToolkit" (without the quotes) after the "if" statement in my /etc/profile.  Restart your session and you should be good to go

---

### Post by dcbc on 2008-05-15
kiwinewt

i am myself a ubuntu(linux) newbie.
i followed the procedure given here
[http://wiki.netbeans.org/InstallingNetbeans6.0OnUbuntu7.10](http://wiki.netbeans.org/InstallingNetbeans6.0OnUbuntu7.10)
i faced no problem.hope this helps

---

