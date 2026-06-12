---
title: "Moneydance Hangs"
date: 2007-05-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by smittym on 2007-05-21
When I try to install Moneydance, I get a window with Moneydance Setup as the title, but the window itself is blank.  I've tried both the "with java" and without java versions and can't get either to work.  Have also tried installing using sudo with same results.  Will it just not work in 64 bit Ubuntu?  I am running Feisty Fawn on an AMD 64 with Sun Java installed.

---

### Post by ronocdh on 2007-05-22
> **smittym said:**
> When I try to install Moneydance, I get a window with Moneydance Setup as the title, but the window itself is blank.  I've tried both the "with java" and without java versions and can't get either to work.  Have also tried installing using sudo with same results.  Will it just not work in 64 bit Ubuntu?  I am running Feisty Fawn on an AMD 64 with Sun Java installed.
Have you tried using the **dpkg --force-architecture** tag in your installation command in the terminal? This is useful when installing i386 debs on 64-bit.

---

### Post by smittym on 2007-05-22
It's a java installer that has a script to launch it.  Not sure how I would use the dpkg --force-architecture command with that.  Any ideas?

---

### Post by kuja on 2007-05-23
something along the lines of "sh filename" or "sudo sh filename"
If it doesn't like sh try bash.

---

### Post by smittym on 2007-05-24
Yes.  The script runs with the command sh.  That's not the issue.  I know how to run the script, but once I run it, it hangs up.  I was hoping that someone had figured out this issue and gotten Moneydance to run on Ubuntu 64, but I guess not.

---

### Post by shad0w_walker on 2007-05-24
Im able to run the java version of moneydance just fine here. How were you giving it access to JRE?

---

### Post by smittym on 2007-05-26
I'm not sure I understand your question,but I'll try to answer.  I first tried running the installer script as is without any modification, then I edited the script to have the location of java on my machine, /usr/bin/java.  Neither worked.  I'm glad to know that you have it working though because that means its possible and I'll eventually be able to figure it out.  Let me know if you have any other ideas.

Thanks.

---

### Post by porschify on 2007-07-24
I am not sure if this has been solved yet, but during a recent install of Moneydance, I had the same problem.  If you have Compiz/Beryl installed the setup screen will hang like smittym described.  The solution that worked for me was to stop Compiz Fusion by typing "metacity --replace &" into a terminal window.

After it installs you can restart compiz by typing "compiz --replace &" into the terminal.

---

