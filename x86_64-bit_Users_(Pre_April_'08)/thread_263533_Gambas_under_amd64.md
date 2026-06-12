---
title: "Gambas under amd64"
date: 2006-09-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by dasyar613 on 2006-09-23
Gambas does not run when selected from the Applications menu. The program installed without any errors, the program shows up in the Applications menu, but when I click it to start it, nothing happens. I am expecting a Gambas window to open up, and to start doing my thing. Is their something else that has to be done, any ideas.

Thanks

---

### Post by Kilz on 2006-09-23
> **dasyar613 said:**
> Gambas does not run when selected from the Applications menu. The program installed without any errors, the program shows up in the Applications menu, but when I click it to start it, nothing happens. I am expecting a Gambas window to open up, and to start doing my thing. Is their something else that has to be done, any ideas.

Thanks

I installed it, not knowing what it is to see if I could get it to work. Im getting a error if started in terminal

sizeof(CLASS) = 256 !
ERROR: #51: Bad archive: Invalid argument

I really dont know what that means. You may want to post to the gambas site or file a bug report.

---

### Post by dasyar613 on 2006-09-23
Thanks Kilz,

Have you had success with any of the other programming suites. I was interested in something that was GUI based, with a straight foreward language like basic. I am not ready for C or C++, just yet. I thought their was a GUI based Perl, but I have not stumbled across it yet.

Thanks

---

### Post by Kilz on 2006-09-23
> **dasyar613 said:**
> Thanks Kilz,

Have you had success with any of the other programming suites. I was interested in something that was GUI based, with a straight foreward language like basic. I am not ready for C or C++, just yet. I thought their was a GUI based Perl, but I have not stumbled across it yet.

Thanks

From my experence 32bit development applications do not work well in 64bit. You may want to concider setting up a chroot. [There is a script that will make it easy. ]("http://www.ubuntuforums.org/showthread.php?t=157412") Then you would have a 32bit enviroment that is seperate, as I understand it, thats a good thing when developing applications.

---

### Post by Ramificatio on 2007-05-06
I have the same exact problem with Gambas, if anyone can post a solution it would be nice, how to run it in 32-bit mode?

---

### Post by damvcoool on 2008-03-01
Gambas is compiling on 64bit now, and it works.

---

