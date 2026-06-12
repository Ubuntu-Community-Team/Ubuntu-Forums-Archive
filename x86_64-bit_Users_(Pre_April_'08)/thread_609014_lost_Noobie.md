---
title: "lost Noobie"
date: 2007-11-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by jakefrog on 2007-11-10
I am trying to get a java program running under Ubuntu 7.10.  The Java version says it is 1.5.0, which is OK. (The program cannot run under 1.4).  The program detects java but then throws the following error message:  error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory.

Research on the net indicates that I am getting this error because the java program was complied for 32 bit systems and not for my amd64 bit system.

How do I get this to work? I tried the suggestion under installing 32 Firefox: sudo aptitude install ia32-libs ia32-libs-gtk linux32 lib32asound2. I got an error message telling me that these packages don't exist.

I am lost. Thankful for any help.

---

### Post by jakefrog on 2007-11-10
I also tried the suggestion in the sticky by SD.  That failed also.  Here is what I got.

Unpacking...
Checksumming...
Extracting...
./jre-6u3-linux-i586.bin: line 333: ./install.sfx.15656: No such file or directory
Failed to extract the files.

---

### Post by John.Michael.Kane on 2007-11-10
Did you use the manual method listed in that guide or the script?

---

### Post by jakefrog on 2007-11-10
No. It was with the manual install. I obviously missed the script so....

I went and tried the script.  It seemed to work fine except the fact that I noticed that it modified no packages (23) because it said I had the most recent version of all. Then it exited.  I looked and there was an option for 32 bit FF on the menu. I went to java and asked it to verify installation and it failed.  I then went to terminal and checked the version of java and it still said 1.5. (not 1.6). Then I ran my java program and got the same error as in the first message.

So I guess the script failed too.

---

### Post by jakefrog on 2007-11-10
Actually, it is I who was riding on the FAIL boat. I ran the script again and realized that I was pressing "y" where I was supposed to press "1". Now java 6.3 is installed when I use the 32 bit browser. However, when I run my java program I still get the error in the OP.

---

### Post by jakefrog on 2007-11-10
> **jakefrog said:**
> Actually, it is I who was riding on the FAIL boat. I ran the script again and realized that I was pressing "y" where I was supposed to press "1". Now java 6.3 is installed when I use the 32 bit browser. However, when I run my java program I still get the error in the OP.

Hmm. It seemed I needed to reboot my machine and now my java program see the new java install. The java program is still failing but it's not because of the absence of java. I think a path might be missing somewhere. 

Anyway, thanks for pointing me to the script SD. That did work.

---

### Post by John.Michael.Kane on 2007-11-10
> **jakefrog said:**
> Hmm. It seemed I needed to reboot my machine and now my java program see the new java install. The java program is still failing but it's not because of the absence of java. I think a path might be missing somewhere. 

Anyway, thanks for pointing me to the script SD. That did work.

No problem. I'm glad it worked out.

---

