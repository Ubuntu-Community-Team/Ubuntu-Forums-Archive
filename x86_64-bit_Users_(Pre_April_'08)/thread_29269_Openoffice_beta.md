---
title: "Openoffice beta"
date: 2005-04-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by estel on 2005-04-23
Hi, 
I'm a relative linux newbie, so I'll appreciate help.
Basically, I'm trying to get the latest OpenOffice 2.0 Beta to run on AMD64 . There's a really old beta (.79) in the repositories, which I don't want to use because its so buggy.
So is there any way of getting OOo 2 to work?

---

### Post by sethmahoney on 2005-04-23
ooo2 beta should be in the repositories.  Have you enabled universe and multiverse?

---

### Post by domesticatewhat on 2005-04-23
I tried to apt-get openoffice.org2 but openoffice.org2-core isn't available.

---

### Post by sethmahoney on 2005-04-23
[QUOTE=domesticatewhat]I tried to apt-get openoffice.org2 but openoffice.org2-core isn't available.[/QUOTE]
 I just peeked in Synaptic, and its there in mine.  I'd recommend firing up Synaptic and searching for openoffice.

---

### Post by domesticatewhat on 2005-04-23
Thats odd. I just updated and looked and still not there. Now its going to bother me until I find out why...

---

### Post by sethmahoney on 2005-04-23
[QUOTE=domesticatewhat]Thats odd. I just updated and looked and still not there. Now its going to bother me until I find out why...[/QUOTE]
 It looks like it is in universe - do you have that enabled?

---

### Post by domesticatewhat on 2005-04-23
Yea, I don't know what is up.

---

### Post by sethmahoney on 2005-04-23
[QUOTE=domesticatewhat]Yea, I don't know what is up.[/QUOTE]
 You're running Hoary, right?  Not Warty?  And you're using the i386 version?

I wonder if maybe something is going on with the package list.  I mean, I'm guessing that since I have it installed, openoffice.org2-base will show up in Synaptic even if its no longer in the repository.  So it could have gone missing and it would still show up on my computer.

---

### Post by tikal26 on 2005-04-23
funny because i don't have them either. I wonder what is wrong

---

### Post by Kareema on 2005-04-24
[QUOTE=estel]Hi, 
I'm a relative linux newbie, so I'll appreciate help.
Basically, I'm trying to get the latest OpenOffice 2.0 Beta to run on AMD64 . There's a really old beta (.79) in the repositories, which I don't want to use because its so buggy.
So is there any way of getting OOo 2 to work?[/QUOTE]

What version are you using - Ubuntu Hoary AMD64 or i386? Looking at your problems, it seems that you are running Ubuntu Hoary AMD64. Unfortunately, there's no recent beta of OO2 in the AMD64 repositories and the one in the reps doesn't work because of the missing dependency domesticatewhat mentioned. I'm waiting for a newer beta, too...

---

