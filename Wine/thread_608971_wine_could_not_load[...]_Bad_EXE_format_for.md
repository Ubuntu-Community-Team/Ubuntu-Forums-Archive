---
title: "wine: could not load[...]: Bad EXE format for"
date: 2007-11-10
forum: Wine
---

### Post by P4VV37 on 2007-11-10
I'm getting this message
wine: could not load L"I:\\virtual-drives\\setup.exe": Bad EXE format for
when I'm trying to install the game.
I have used wine setup.exe and ~\virtual-drives\\setup.exe both are not working.
What's the problem?

p.s.
sorry for my english:)

---

### Post by Vadi on 2007-11-10
Name of the game?

---

### Post by P4VV37 on 2007-11-10
The witcher, but  I read on AppDB that instalation works

---

### Post by Vadi on 2007-11-10
Virtual drives... are you using AcetoneISO to mount an image? If so, shouldn't there be folders labelled 1-9 inside the virtual-drivers folder?

---

### Post by P4VV37 on 2007-11-10
Yes, cd is mounted in "1"
I had this error so i coppied "setup.exe" and changed premissions, i was thinking so that's because of premissions.

---

### Post by geirha on 2007-11-10
What does ```
file setup.exe
``` say?

I encountered a similar problem once. I don't remember if it was the same error message, but in my case it turned out to be a self-extracting zip-file, of which you can unzip like a regular zip-file.

---

### Post by Vadi on 2007-11-10
Yeah, I never got anything working because AcetoneISO messes file permissions up somehow and their ownership.

So just burn the file on a CD, or aquire the original CD.

---

### Post by P4VV37 on 2007-11-10
$ file setup.exe
setup.exe: data

---

### Post by bulletxt on 2007-11-11
AcetoneISO doesn't mess up anything.
When you mount an image, it's using as backend fuseiso wich itself works on fuse library.
Your problem depends on fuse. to be more clear, if you mount, the folder becomes of root user. this is normal and depends on fuse. it's of root user but is readable by any user if properly configured.
it's not good to say bad about software without knowing how things work.

@P4VV37 

why ~/virtual-drives//setup.exe?
it should be mounted in ~/virtual-drives/1 .
I think you didn't properly set fuseiso permissions as clearly stated on acetoneiso's source.

 open a terminal and as root user type:

   chmod 4755 /usr/bin/fusermount  (may be /bin/fusermount depending on distro)
   chmod o+rw /dev/fuse
   addgroup <your-user> fuse  (ex. addgroup johndoe fuse)

now you can mount your image and correctly read files.
also be sure you have latest AcetoneISO2 1.96 version.

---

### Post by Vadi on 2007-11-12
I did those chmod instructions when I was installing. And I did it now just to test, same result :(.

---

### Post by bulletxt on 2007-11-12
I'm starting to think AcetoneISO2 has nothing to do with your problem. as a last solution, I can advise you to use Extract feature of acetoneiso2. it will extract your image inside a folder so you will have permissions. you will find the feature in the main gui.

---

### Post by Vadi on 2007-11-12
I'll try that.

But since the program depends on the fuse so much, as I understand, acetone devs would want to do something about it.

Instead, when I emailed them, I got the same answer - "not acetones problem". Well, okay, but I can't use your program either because of that problem.

---

