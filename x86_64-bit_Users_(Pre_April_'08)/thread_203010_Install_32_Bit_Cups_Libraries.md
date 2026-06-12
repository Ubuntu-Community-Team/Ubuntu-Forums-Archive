---
title: "Install 32 Bit Cups Libraries?"
date: 2006-06-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jonnycat26 on 2006-06-24
Hi,

The subject pretty much sums this all up...  I want to install 32 bit cups libraries on my 64bit kubuntu install.  The reason for this is because I have lexmark printer drivers, and they're 32 bit binaries.  They work amazingly well, but they have a dependency on the 32 bit cups libraries.

All of this worked in SuSE (64 bit) prior to my switch to kubuntu.  But SuSE 10.1 was so buggy it was unbearable.  So maybe someone out there in ubuntu land can help me solve the last piece of this puzzle.  :)

---

### Post by Kilz on 2006-06-24
[QUOTE=Jonnycat26]Hi,

The subject pretty much sums this all up...  I want to install 32 bit cups libraries on my 64bit kubuntu install.  The reason for this is because I have lexmark printer drivers, and they're 32 bit binaries.  They work amazingly well, but they have a dependency on the 32 bit cups libraries.

All of this worked in SuSE (64 bit) prior to my switch to kubuntu.  But SuSE 10.1 was so buggy it was unbearable.  So maybe someone out there in ubuntu land can help me solve the last piece of this puzzle.  :)[/QUOTE]
There may be a way of doing it. If you know the .deb files names you can [search for them]("http://packages.ubuntu.com/") . Then open them up and manualy add them to /usr/lib32  . You will need the dpkg-dev package installed for the archive program to open .deb files. Once you extract the file, they will be in a data.tar that you will have to extract again.
I hear you on how buggy SuSE 10.1 is. SuSE 10.0 was my first distro, I couldnt fix 10.1 so I looked and found Ubuntu.

---

### Post by Jonnycat26 on 2006-06-24
That worked, but it certainly felt a bit hacky doing it.  

I know there are versions of common 32 bit libraries available (such as gtk, qt, kde) for installation on 64 bit systems, and perhaps cups should be added.  A lot of printer manufactures distribute binary only drivers....

---

### Post by Kilz on 2006-06-24
[QUOTE=Jonnycat26]That worked, but it certainly felt a bit hacky doing it.  

I know there are versions of common 32 bit libraries available (such as gtk, qt, kde) for installation on 64 bit systems, and perhaps cups should be added.  A lot of printer manufactures distribute binary only drivers....[/QUOTE]
There may already be those packages, I'm not an expert. But I figured out how to get other 32 bit programs running that way. True it is hacking it in a sense, but sometimes that's the only way to figure out how to do something. If it works, thats all that matters, and isnt it wondeful to be able to do that with Linux :D

---

### Post by Jonnycat26 on 2006-06-24
[QUOTE=Kilz]There may already be those packages, I'm not an expert. But I figured out how to get other 32 bit programs running that way. True it is hacking it in a sense, but sometimes that's the only way to figure out how to do something. If it works, thats all that matters, and isnt it wondeful to be able to do that with Linux :D[/QUOTE]

True, but I've been using Linux for about 8 years now...  I don't expect a beginner to be able to figure out how to do what I did...  and IMO a 'desktop' distro such as ubuntu/kubuntu should be easy for people with very little linux experience.

---

