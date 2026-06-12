---
title: "Instructions for installing .net framework 4.0 with wine 1.6"
date: 2013-08-04
forum: Wine
---

### Post by A.O._Stanley on 2013-08-04
I've read the instructions on how to do this at winehq, but it's pretty much all Greek to me. I attempted an install in a virtual machine, but it just didn't work.

If anyone comes across or has come across a site that gives step by step instructions on how to get .net framework 4.0 installed in wine, would you please provide a link?

Thanks

---

### Post by GwL3eNC on 2013-08-04
Hi A.O._Stanley,

i got a look at the site you talked about. Why don't you just try it. What is the problem for you.
If you dont try it you cant find out where you get stuck.

1. Download the file
2. get a mscoree.dll. On a windows system you can find it in the Windows\system32 folder. You need that file
   during installation because:

    Winetricks removes the default mscoree.dll file, but a Windows version of it is required 
    for a successful installation. 

3. Open a console and go to the folder where you saved the file out of step 1 and type

    winetricks dotnet40

   When the installer window pops up, do NOT immediately continue the setup. 
   Put now your own mscoree.dll into the windows/system32 folder (/yourhome/.wine...), and then continue 
   with the setup.

That seems to be the only thing you have to do. Please try it or concrete your problems on installation.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=17886](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17886)

---

### Post by A.O._Stanley on 2013-09-15
Still looking for a step-by-step how to along the lines of how "How To Geek" would explain this. Though I continue to do searches, I still haven't found one, yet. 

I have Win7 so I can get this dll, but since I really don't know much about computers in general I have no idea how to get this from Win7 to Ubuntu. So what I'm looking for is a link to a site where I can follow a simple tutorial.

Thanks

---

