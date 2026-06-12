---
title: "[solved] I can't install Java on Wine?"
date: 2015-06-21
forum: Wine
---

### Post by ohmysql on 2015-06-21
Is there something fundamentally screwed up about my wine?

I haven't done anything with the settings, I just recently installed it, but Java Runtime Environment isn't loading at all.

I browsed here:

[https://www.java.com/en/download/manual.jsp](https://www.java.com/en/download/manual.jsp)

I downloaded both:

jre-8u45-windows-i586-iftw.exe

and 

jre-8u45-windows-x64.exe

The first, I run and nothing happens. Here's winedbg:

```
winedbg jre-8u45-windows-i586-iftw.exe 
WineDbg starting on pid 0031
0x7b85f647: movl    %edi,0x4(%esp)
Wine-dbg>step
fixme:winedbg:be_i386_is_jump unknown 89
Single stepping until exit from function,
which has no line number information.
Invalid address (0x7b85f653) for breakpoint 0, disabling it
Process of pid=0031 has terminated
```

Here's the second problem:

```
winedbg jre-8u45-windows-x64.exe 
WineDbg starting on pid 0035
fixme:thread:GetThreadPreferredUILanguages 52, 0x23f728, (nil) 0x23f724
fixme:thread:GetThreadPreferredUILanguages 52, 0x23f728, (nil) 0x23f724
```

I am using a 64-bit machine on Windows 64.

---

### Post by flaymond on 2015-06-22
[QUOTE=ohmysql]I am using a 64-bit machine on Windows 64.[/QUOTE]

By that do you mean you wanna install Java with Wine on Windows?

Why do you need Wine to run Java:-s? Can't you just install Java and do your things with Java normally? I'm actually don't really understand about your question.

Here is my question to you -

# Do you installing Java on Linux or Windows? (with Wine ?)
# What is the purpose you need Java for? For Web browser or development?

Thanks! :-)

---

### Post by ohmysql on 2015-06-22
You're right, thanks for asking. The real application I want to install is [freephoneline]("https://appdb.winehq.org/objectManager.php?sClass=application&iId=10591"). When I run it, a window pops up that says 

JRE Not Found 

"The Java Runtime Environment (JRE) was not found. Please download and install a JRE (minimum version 1.6) from: [www.java.com](www.java.com) If you have JRE installed you can browse for it below: 

JRE Path:"

I obviously have JRE installed for linux, but I'm not sure how to talk Wine into thinking I have Java. So I tried to install it and ran into the error mentioned in this original post.

I hope that answers your question!

---

### Post by ohmysql on 2015-06-22
PS I tried this with no success (aka creating that folder):

[https://askubuntu.com/questions/117041/how-do-we-install-java-in-wine](https://askubuntu.com/questions/117041/how-do-we-install-java-in-wine)

---

### Post by ohmysql on 2015-07-08
Ah, I figured it out. For whatever reason, Wine doesn't work with Java 8, so the solution is to install Java 7. Thanks

---

