---
title: "Error: Wrong architecture 'i386'"
date: 2009-05-01
forum: x86 64-bit Users
---

### Post by mcluhan on 2009-05-01
Hello,
 

 I'm trying to install a 32-bit photography program called “Bibble” on my 64 bit installation of Ubuntu and am getting nothing but errors. I've already installed the 32-bit “getlib” dependency files mentioned on another thread:   [http://www.boundlesssupremacy.com/Ca...etlibs-all.deb](http://www.boundlesssupremacy.com/Ca...etlibs-all.deb)
 

 I really can't think of anything else to do besides going back to the 32-bit version of Ubuntu.  
 

 Any ideas?
 

 Thanks,
 

 David

---

### Post by dcstar on 2009-05-01
> **mcluhan said:**
> Hello,
 

 I'm trying to install a 32-bit photography program called “Bibble” on my 64 bit installation of Ubuntu and am getting nothing but errors. I've already installed the 32-bit “getlib” dependency files mentioned on another thread:   [http://www.boundlesssupremacy.com/Ca...etlibs-all.deb](http://www.boundlesssupremacy.com/Ca...etlibs-all.deb)
 

 I really can't think of anything else to do besides going back to the 32-bit version of Ubuntu.  
 

 Any ideas?
 

 Thanks,
 

 David

You can try the "force-architecture" option to install, but no guarantees it will run.

---

### Post by jespdj on 2009-05-01
To forcibly install a 32-bit .deb on your 64-bit system, do this:
```
sudo dpkg -i --force-architecture filename.deb
```
You will ofcourse have to have the necessary 32-bit libraries installed that the application needs.

---

### Post by manolitos on 2009-05-01
hello guyz! i m new to linux and i got prob with the force architecture! it told me that i need more access ! what does it mean?

---

### Post by 3Miro on 2009-05-01
Why don't you just go to Applications -> Add/Remove, select all available programs and install Ubuntu-restricted-extras. That will install flash for you and it is much easier. That is how I am watching youtube videos.

Otherwise, well I cannot help you since the output of the command is in Greek (or something similar). Can you translate it in English.

---

### Post by bford16 on 2009-05-01
> **manolitos said:**
> hello guyz! i m new to linux and i got prob with the force architecture! it told me that i need more access ! what does it mean?
You have to run the command with 'sudo.' Like this:```
sudo dpkg -i --force-architecture yourpackage.deb
```You will have to enter your password.

---

### Post by manolitos on 2009-05-01
the output of the command means that i need more access

---

### Post by MontelEdwards on 2009-05-01
Needing more access means that your not root, do what he says

---

### Post by manolitos on 2009-05-01
which is my sudo password?

---

### Post by WakkiTabakki on 2009-05-01
> **manolitos said:**
> which is my sudo password?

Your own (same as you logged in with).

/N

---

### Post by mcluhan on 2009-05-01
This is the error I just got when I tried to force the install:

bergendc@bergendc-desktop:~$ sudo dpkg -i --force-architecture bibblelite_4.10.1-1_i386.deb
dpkg: error processing bibblelite_4.10.1-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 bibblelite_4.10.1-1_i386.deb

I downloaded this file to my desktop. Should I have placed it somewhere else? I'm probably just making some simple beginners mistake...

Thanks,

David

---

### Post by Fir3chi3f on 2009-05-03
I got it to work after installing libstdc++5

Copy and paste this into terminal and try the force install again
```
sudo apt-get install libstdc++5
```

---

### Post by Fir3chi3f on 2009-05-03
OH! I see whats going on!
Try this in your terminal my friend!
```
sudo dpkg -i --force-architecture /home/bergendc/Desktop/bibblelite_4.10.1-1_i386.deb
```

---

