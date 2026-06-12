---
title: "No web access with Celtx 1.0"
date: 2008-08-18
forum: x86 64-bit Users
---

### Post by Ozdemon on 2008-08-18
I have just installed Celtx 1.0 under Ubuntu 8.04 (64-bit).  The program works, but it cannot access the internet for any purpose - login, banner, etc.

As the program is based on Firefox, there has been a suggestion on another site that it is related to 64 bit issues and Firefox.  I don't know, but is sounds plausible.

Has anyone been able to get Celtx to work properly with internet access running 64-bit?

---

### Post by Thelasko on 2008-08-19
I had to do some reading about this program, and I checked [URL="http://wiki.celtx.com/index.php?title=Installation#For_Linux"]the wiki.
[/URL]  Unfortunately, the program appears to be proprietary. (this is incorrect)
> As the program is based on Firefox, there has been a suggestion on another site that it is related to 64 bit issues and Firefox.
Firefox doesn't have issues with 64-bit.  But you gave me an idea. See what happens when you [install the 32-bit version of Firefox]("http://ubuntuforums.org/showthread.php?p=1174435") in your system.  The part of the instructions that say,
> You might have to install the normal "ia32-libs" and also "ia32-libs-gtk", perhaps more. 
makes me think that by installing 32-bit Firefox, you may install some dependency for this program.  It would also be nice if the creator provided some better information than "perhaps more."

Kilz, any thoughts?

---

### Post by Ozdemon on 2008-08-19
Tks for the reply.  As you have seen, I am not the only person with this issue.

> **Thelasko said:**
> 
makes me think that by installing 32-bit Firefox, you may install some dependency for this program. 

Is it okay to install another version of Firefox on my 8.04 system?  I already have the right one for 64 bit.  BTW, I installed all the ia32's that could possibly apply, but it made no difference.

---

### Post by Thelasko on 2008-08-19
> Is it okay to install another version of Firefox on my 8.04 system?
Yes, you just can't use them both at the same time.

EDIT: If you try to, you will just get an error message that Firefox is already open.  You won't break your computer or anything.

---

### Post by Thelasko on 2008-08-19
I read that wiki some more and it appears the the program is open source.  It would be possible to compile the program for 64-bit with some work.

---

