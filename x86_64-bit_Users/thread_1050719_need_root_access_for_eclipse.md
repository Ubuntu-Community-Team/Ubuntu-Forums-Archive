---
title: "need root access for eclipse?"
date: 2009-01-25
forum: x86 64-bit Users
---

### Post by qvyang on 2009-01-25
I installed eclipse, then I edited my program in it. When I tried to save, it reports error saying that the file I am trying to save is read-only. Later I tried to open up my eclipse in command line using:
sudo eclipse
Then I could save my project without any errors.
This means that every time I want to use eclipse I have to open it with root access, which is quit annoying. 
Can somebody tell me how to fix this? Thanks!

---

### Post by theApokalypsis on 2009-01-25
Hey,

I am running Eclipse/Aptana. where is your file being stored?

I was running a local Apache Server in /var/www/ which i had to change the permissions on.

could that be it?

---

### Post by stchman on 2009-01-26
> **qvyang said:**
> I installed eclipse, then I edited my program in it. When I tried to save, it reports error saying that the file I am trying to save is read-only. Later I tried to open up my eclipse in command line using:
sudo eclipse
Then I could save my project without any errors.
This means that every time I want to use eclipse I have to open it with root access, which is quit annoying. 
Can somebody tell me how to fix this? Thanks!

You are trying to save your project in a place that you do not have write access to.

---

### Post by qvyang on 2009-02-14
My eclipse is installed in /opt/eclipse
The problem is that it doesn't allow me save in any directory!

---

### Post by zacktu on 2009-02-14
When installed, Eclipse creates a directory named workspace in your home directory.  Unless you have defined another workspace, that should be where Eclipse saves your files.

---

### Post by qvyang on 2009-02-21
I set the location of the workspace in a subdirectory under my home directory. I don't think it's the problem with the location of my workspace. I think it's just something to do with to permission.

---

