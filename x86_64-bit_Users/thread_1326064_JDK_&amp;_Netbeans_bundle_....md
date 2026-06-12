---
title: "JDK &amp; Netbeans bundle ..."
date: 2009-11-14
forum: x86 64-bit Users
---

### Post by xtbt on 2009-11-14
Well, I've been looking all over the x64 forum for the answer with no luck so here's my situation.

I'm using an ACER ASPIRE 5536 which had Windows Vista pre-installed. Obviously I took off that piece of shhhhh...tupend OS out my laptop and made a fresh install of Windows 7 Ultimate x64 (I needed to see it working by myself, and curiously, as far as I've been using it, it seems very stable and not that slow as I thought.) and then a fresh install of Ubuntu 9.10 x64 making the partitions by myself and stuff.

Well, everything went just fine, Ubuntu boots alright, my wireless card was detected without the need of additional drivers or something, I then installed my ATI card drivers (ATI's website), then compiz-fusion (Repo) with the cube and all those cool effects, 64-bit flash (Ubuntu forums), 64-bit java JRE (Repo), 64-bit java plugin (Repo) but there's something I need to have it all, to be happy, to be complete, etc.

I need the JDK & Netbeans bundle in 64 bits. I've been looking all over sun's website but it seems that they only have the 32 bits linux version and when I try to install it, this error message appears: eval: 1: /tmp/.nbi-6113534.tmp/jre-6u14-linux-i586.bin: not found. I had that bundle working on Intrepid some months ago but I don't remember exactly if it was the 32 bits bundle working over 64 bits Intrepid or if it was a 64 bits one.

Alternatively, if anyone had any luck installing both packages separately from the repos, please let me know too. I think it's not a big deal configuring the jdk values into netbeans, is it?

Any help will be appreciated.
Thanks in advance.

---

### Post by hoboy on 2009-11-14
I ma using Linux ubuntu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux.
I have install Netbeans from Ubuntu Software Center 
and it is working fine for me.
Go to Ubuntu Software Center /Porgamming you will find NetBeans 6.7.1

---

### Post by Unterseeboot_234 on 2009-11-14
If you use JDK1.6.0_16 for Linux you get the 64-bit JRE plug-in. NetBeans will link to the JDK of your choice. Be advised that JavaFX will be problematic with some things and also be advised some of the Java1.6 API has not been implemented. Specifically, JDK1.6.0_12 (32-bit) runs the java.awt.Desktop, (open the OS's default Textpad, browser, etc.), but the same code run with the JDK1.6.0_16 prints an error message to terminal: "Not yet implemented". Same goes for java.awt.Desktop.Icon err: not yet implemented. The 64-bit JRE plug-in does seem to run faster.

Nothing, none, no JRE, seems to work for me in Opera.

I downloaded the NetBeans bundle from Sun.

---

### Post by xtbt on 2009-11-15
> **hoboy said:**
> I ma using Linux ubuntu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux.
I have install Netbeans from Ubuntu Software Center
and it is working fine for me.
Go to Ubuntu Software Center /Porgamming you will find NetBeans 6.7.1

Just to be sure ... is the Netbeans from the repos the 64 bits one ?

> **Unterseeboot_234 said:**
> If you use JDK1.6.0_16 for Linux you get the 64-bit JRE plug-in. NetBeans will link to the JDK of your choice. Be advised that JavaFX will be problematic with some things and also be advised some of the Java1.6 API has not been implemented. Specifically, JDK1.6.0_12 (32-bit) runs the java.awt.Desktop, (open the OS's default Textpad, browser, etc.), but the same code run with the JDK1.6.0_16 prints an error message to terminal: "Not yet implemented". Same goes for java.awt.Desktop.Icon err: not yet implemented. The 64-bit JRE plug-in does seem to run faster.

Nothing, none, no JRE, seems to work for me in Opera.

I downloaded the NetBeans bundle from Sun.

I've downloaded the NetBeans bundle from Sun's webpage too, the problem I had was that I couldn't installed it because of the error that I mentioned at the beginning, but now I found out that the bundle from sun's webpage has 32bits netbeans with 32 bits jdk.

I think the only choice is to download 64 bits jdk from sun, and then 64 bits netbeans from repos (if and only if it's 64 bits, if not I'll get it from netbeans.org).

My configuration right now is like this:

JRE - sun-java6-jre & sun-java6-bin (from repos, supposedly 64 bits)
Plug-In - sun-java6-plugin (from repos, supposedly 64 bits)

I haven't had any trouble with any of these two packages so far. I'm using firefox by the way.

Only thing is that when I check in sun's webpage for java, it says that my version is not the recommended because it's out-of-date. Is there some way that I can update the the java plugin that comes in the repos?

---

