---
title: "MP160 on 64-bit"
date: 2008-10-13
forum: x86 64-bit Users
---

### Post by Pro-reason on 2008-10-13
I've recently upgraded to Kubuntu Intrepid 64-bit (from Ubuntu Hardy 32-bit), and it's all going fine, except that I've just realised that my printer-scanner doesn't work.  It's a Canon Pixma MP160, and Linux drivers are available for it on the Canon website.  They are in RPM format, and I previously had no trouble converting them to DEB so that I could install them.

I've tried installing them with “sudo dpkg -i --force-architecture”, but they don't work.

What do I have to do to make them work?

---

### Post by howefield on 2008-10-13
Use Alien to convert rpm to .deb ?

---

### Post by Pro-reason on 2008-10-14
> **howefield said:**
> Use Alien to convert rpm to .deb ?

Perhaps I didn't express myself clearly.  Converting from .rpm to .deb is trivial.  The problem is that they are 32-bit packages.  They no longer work, because I am currently using a 64-bit system.

How can I get this printer-scanner to work on a 64-bit system?

---

### Post by Thelasko on 2008-10-14
You can try to compile it from source.  Download the src.rpm file and convert it to a src.deb using alien.  I've never tried it, but it might be your best bet if force-arch didn't work.

---

### Post by Pro-reason on 2008-10-14
> **Thelasko said:**
> You can try to compile it from source.  Download the src.rpm file and convert it to a src.deb using alien.  I've never tried it, but it might be your best bet if force-arch didn't work.

It doesn't have a configure script.  I don't know what to do with it.

---

### Post by Thelasko on 2008-10-15
> **Pro-reason said:**
> It doesn't have a configure script.  I don't know what to do with it.
From what I understand source RPM files don't have configure scripts.  They have a [.spec]("http://www.madboa.com/geek/specs/") file instead.

I don't know how you tried to install it, but my guess is you need to convert the source rpm into a source deb.  There is very little documentation about this process.  I don't think you can build it the same way you would a tar.gz.

Why do printer manufacturers think Red Hat is the only Linux distribution out there?

---

### Post by Thelasko on 2008-10-15
I found a program called[ mock.]("http://manpages.ubuntu.com/manpages/hardy/man1/mock.html")

---

### Post by Pro-reason on 2008-10-15
> **Thelasko said:**
> From what I understand source RPM files don't have configure scripts.  They have a [.spec]("http://www.madboa.com/geek/specs/") file instead.

I don't know how you tried to install it, but my guess is you need to convert the source rpm into a source deb.  There is very little documentation about this process.  I don't think you can build it the same way you would a tar.gz.

I converted to .deb first of all, and extracted the source code.  I'm familiar with compiling, but this didn't have all the necessary files in it for a non-guru.

I've ended up installing 32-bit Intrepid instead.

---

### Post by Thelasko on 2008-10-16
> **Pro-reason said:**
> I've ended up installing 32-bit Intrepid instead.

Booo! :(

I was hoping you would try that mock program.

---

