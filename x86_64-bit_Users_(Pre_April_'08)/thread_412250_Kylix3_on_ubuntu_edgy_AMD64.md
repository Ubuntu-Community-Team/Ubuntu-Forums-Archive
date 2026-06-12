---
title: "Kylix3 on ubuntu edgy AMD64"
date: 2007-04-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Gasquet on 2007-04-17
hello,

i tried to install kylix3 ent on my ubuntu edgy
and my cpu is based on amd64
i followed known way to install kylix3 to ubuntu dapper
but there're huge problems
i think my pc can't access to binary libraries in kylix cd - is it because of amd64 ?
and there's an error when i execute install shell script named setup.sh
anyone who succeeded installing kylix3 on ubuntu edgy & amd64 ?
help me out plz~

from woonghee in s.korea

---

### Post by Kilz on 2007-04-17
> **Gasquet said:**
> hello,

i tried to install kylix3 ent on my ubuntu edgy
and my cpu is based on amd64
i followed known way to install kylix3 to ubuntu dapper
but there're huge problems
i think my pc can't access to binary libraries in kylix cd - is it because of amd64 ?
and there's an error when i execute install shell script named setup.sh
anyone who succeeded installing kylix3 on ubuntu edgy & amd64 ?
help me out plz~

from woonghee in s.korea

What is the error? What method did you use to install (link please).

---

### Post by Gasquet on 2007-04-17
i tried this way


   sudo apt-get install gcc libgtk1.2 libxaw6 
   sudo ln -s /usr/X11R6/lib/libx11.so.6 /usr/X11R6/lib/libx11.so : libx11.so.6 wasn't there, so i found libx11.so.6.2.0 instead, and i made symbolic link.

and then i did


   sh setup.sh 
       setup.sh: 93: Syntax error: "(" unexpected 


i saw the installation script file, but i don't think it does matter. in 93rd line, it is just declaration for function.

and i tried to check with "borpretest"
"borpretest" uses some *.o files but i see the files with using "ls" command, but my os acts like "*.o"s doesn't exist.

---

### Post by Kilz on 2007-04-18
> **Gasquet said:**
> i tried this way


   sudo apt-get install gcc libgtk1.2 libxaw6 
   sudo ln -s /usr/X11R6/lib/libx11.so.6 /usr/X11R6/lib/libx11.so : libx11.so.6 wasn't there, so i found libx11.so.6.2.0 instead, and i made symbolic link.

and then i did


   sh setup.sh 
       setup.sh: 93: Syntax error: "(" unexpected 


i saw the installation script file, but i don't think it does matter. in 93rd line, it is just declaration for function.

and i tried to check with "borpretest"
"borpretest" uses some *.o files but i see the files with using "ls" command, but my os acts like "*.o"s doesn't exist.

A quick search of the forums comes up [with this question]("http://ubuntuforums.org/showpost.php?p=2290273&postcount=20") wich is the exact same error message , [and this response]("http://ubuntuforums.org/showpost.php?p=2291413&postcount=21") which is a fix for it.

---

