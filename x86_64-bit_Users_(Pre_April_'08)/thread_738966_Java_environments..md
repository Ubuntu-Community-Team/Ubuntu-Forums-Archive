---
title: "Java environments."
date: 2008-03-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by leg on 2008-03-29
Hi I am recently getting back into Java programming after a year or so where I have done very little and what I have been doing was on a Windows machine at work. I have had a quick look in synaptic and can only see 1.4.2. What I want to do is use either a 1.5 or 1.6 version and I would also like to have the wireless toolkit working and using Netbeans. I would also like to investigate J2EE but the rest of it is has more priority. I can see Netbeans 5.5 version in synaptic.

My question is how difficult will it be for me to set this up so that I can use Netbeans and with one of the java versions above and the mobility toolkit installed and working. I think the main problem is that I can't find a 64 bit version of the wireless toolkit from Sun so may be my biggest problem. Point me to the howtos please so I can see how much effort this is going to cost me.

---

### Post by Unterseeboot_234 on 2008-03-29
If I were you I would go ahead with the Sun download of Java6 with the NetBeans6. When coding, NetBeans "slams" the pathname for you every time you compile or run. We could always do the same thing in the Console but we usually had the PATH and CLASSPATH set up where we finally got the "javac" to work in Windows and then forgot about it.

I don't know about the Wireless. I do know you have problems cruising the web and viewing java applets. There is the IceTea plug-in for 64-bit. It works, it is buggy. There is also the ia32-lib method where links are made between the 32-bit plug-in and that library. This is a browser issue with 64-bit. Rumor is, Java7 will have a 64-bit plug-in. 

For code, the Sun install should go correctly. You can even put the JDK in the location where you want it. I mean, after all, when I'm developing, I want all my files to be readily available and not inside of usr/share.

To fix links for Console, I like this post from the Ubuntu Forums

[**Custom JDK Install**]("http://ubuntuforums.org/showthread.php?t=319138")

One other mention about Java6. They have vastly improved the Generics and a lot of development with custom Swing graphics. NetBeans will let you select your installed JDK versions.

---

### Post by leg on 2008-03-29
Excellent thanks for that. What about xcb and the swing libs with compiz is that a problem in Ubuntu.

[edit]
Well I think I have answered my own question there and xcb (I think it is) needs a newer version. Netbeans does not show anything when you start it just a grey screen. If I am right this is fixed with a newer version of this lib.

---

