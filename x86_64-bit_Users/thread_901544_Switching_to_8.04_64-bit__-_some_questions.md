---
title: "Switching to 8.04 64-bit  - some questions"
date: 2008-08-26
forum: x86 64-bit Users
---

### Post by niallporter on 2008-08-26
Hi all,

Until now I've always used the x86 releases on my AMD64 machine, mainly because of poor support for some things on x86_64.  I got bored at the weekend and decided to see how things were with the current release so downloaded the liveCD, booted and all looked OK.  Installed to a spare partition, added the ubuntu-restricted-extras package and some stuff from the Medibuntu repo and still all looks OK (got Flash plugin, Java, some other stuff that I used to have problems with installing manually).

So, the questions:

[LIST=1]
[*]Do the above actually now exist in 64-bit format?  Or have I installed 32-bit versions without realising?
[*]I also used Synaptic to export my package list from my x86 installation and it seems to be happy to install stuff from the list in Synaptic on the x86_64 install, do I take it these are from a 64-bit repository?
[*]Finally, is the whole of the userland stuff compiled for x86_64 as well as the kernel?
[/LIST]

Thanks in advance,
Niall

---

### Post by perlluver on 2008-08-26
> **niallporter said:**
> 


Do the above actually now exist in 64-bit format?  Or have I installed 32-bit versions without realising?


Answer to this question, is they are 32 bit still, with an IA32 wrapper, to make them compatible with 64 bit.

---

### Post by Joeb454 on 2008-08-26
I think only flash is 32 bit.

---

### Post by Thelasko on 2008-08-26
> **Joeb454 said:**
> I think only flash is 32 bit.
Yes and no.
Currently OpenJDK supports most web applets, but not all.  The most common complaint is the Facebook photo uploader doesn't work.  It's a native 64-bit program. 

It is possible to install the 32-bit version of Java in Ubuntu 64-bit, but it's more complicated.  In my opinion, if the OP couldn't get 32-bit Java to work before, he/she won't be able to get it to work now.

If the OP did install 64-bit Ubuntu, the version of Java used was likely OpenJDK.

I should add, that I've never used this medibuntu repository thing.  From what I gather it sounds alot like Automatix from back in the day (Feisty Fawn :)).  Automatix was how I got Flash and Java to work in Feisty.

---

### Post by Sef on 2008-08-26
> It is possible to install the 32-bit version of Java in Ubuntu 64-bit, but it's more complicated. In my opinion, if the OP couldn't get 32-bit Java to work before, he/she won't be able to get it to work now.


Follow [Kilz's tutorial]("http://ubuntuforums.org/showthread.php?t=202537").

---

### Post by jespdj on 2008-08-27
> **niallporter said:**
> So, the questions:
[LIST=1]
[*]Do the above actually now exist in 64-bit format?  Or have I installed 32-bit versions without realising?
[*]I also used Synaptic to export my package list from my x86 installation and it seems to be happy to install stuff from the list in Synaptic on the x86_64 install, do I take it these are from a 64-bit repository?
[*]Finally, is the whole of the userland stuff compiled for x86_64 as well as the kernel?
[/LIST]
1. Skype and Flash on Medibuntu are 32-bit, but they are packaged for 64-bit (with the necessary 32-bit libraries) and work without problems on 64-bit systems.

2. Yes, you get software from the 64-bit repository.

3. Yes, the whole userland stuff is also 64-bit. 64-bit Ubuntu is not a hybrid system like Mac OS X; it's completely 64-bit.

---

### Post by Thelasko on 2008-08-27
> **Sef said:**
> Follow [Kilz's tutorial]("http://ubuntuforums.org/showthread.php?t=772490").
I think you intended to link to [this one]("http://ubuntuforums.org/showthread.php?t=202537").  Some people won't settle for anything more complicated than a double click.:)

---

### Post by Kilz on 2008-08-27
> **Thelasko said:**
> **Some people won't settle for anything more complicated than a double click.**:)

Quoted for the pure truth. that howto really took off when I wrote it as a script.

---

### Post by Sef on 2008-08-28
> I think you intended to link to this one. Some people won't settle for anything more complicated than a double click.

You are right.

---

