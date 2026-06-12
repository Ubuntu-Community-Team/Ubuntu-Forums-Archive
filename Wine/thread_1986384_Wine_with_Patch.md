---
title: "Wine with Patch"
date: 2012-05-24
forum: Wine
---

### Post by SJerry421 on 2012-05-24
Hello i was wondering if anyone could write me a step by step on how to install Wine with the wow patch from [http://bugs.winehq.org/show_bug.cgi?id=11674#c64](http://bugs.winehq.org/show_bug.cgi?id=11674#c64)  I have tried before and failed. I don't want to have to go back to Windows because the only game I play is giving me FPS issues. :(

---

### Post by SJerry421 on 2012-05-25
Ok So i Have installed wine doing these steps 
sudo apt-get build-dep wine1.5
apt-get source wine 1.5
cd wine1.5-1.5.4
patch -p1 < ../rgl.patch
./configure --enable-win64
make
The problem is when i run  ./wine64 /home/jerry/WoW/Launcher.exe I get an error at the bottom of terminal that says
wine: failed to initialize: /usr/local/lib64/wine/ntdll.dll.so: cannot open shared object file: No such file or directory

---

### Post by matt_symes on 2012-05-25
Hi

Open a terminal and type

```
sudo updatedb
```

Enter your password. It will not be echoed to the screen. This will update the database of where items are stored on your computer.

then type

```
locate ntdll.so
```

Post the results back here.

Kind regards

---

### Post by SJerry421 on 2012-05-25
jerry@jerry-HP-Pavilion-dv6-Notebook-PC:~$ sudo updatedb
[sudo] password for jerry: 
jerry@jerry-HP-Pavilion-dv6-Notebook-PC:~$ locate ntdll.so
jerry@jerry-HP-Pavilion-dv6-Notebook-PC:~$ locate ntdll.dll.so
/home/jerry/wine1.5-1.5.4/dlls/ntdll/ntdll.dll.so
/usr/lib/i386-linux-gnu/wine/ntdll.dll.so
/usr/lib/x86_64-linux-gnu/wine/ntdll.dll.so
jerry@jerry-HP-Pavilion-dv6-Notebook-PC:~$

---

### Post by uRock on 2012-05-25
Moved to *Wine* sub-forum.

---

### Post by matt_symes on 2012-05-25
Hi

> wine: failed to initialize: /usr/local/lib64/wine/ntdll.dll.so: cannot open shared object file: No such file or director

Wine is looking in /usr/local/lib64/... for ntdll.so.

> /usr/lib/i386-linux-gnu/wine/ntdll.dll.so
/usr/lib/x86_64-linux-gnu/wine/ntdll.dll.so

ntdll.so is actually stored in two locations /usr/lib/i386-linux-gnu/... and /usr/lib/x86_64-linux-gnu/...; one for 32 bit and one for 64 bit.

Maybe symbolic links would work.

```
sudo ln -s /usr/local/lib64/wine/ntdll.dll /usr/lib/x86_64-linux-gnu/wine/ntdll.dll.so
```

You may also want to create a symbolic link for the 32 bit ntdll.so library.

I don't actually use wine so i don't know if the above will work but try it.

Post back any errors. If there are erros then i will not be able to respond for a couple of hours.

Kind regards

---

### Post by SJerry421 on 2012-05-25
Well I do appreciate the help here is the error
```
jerry@jerry-HP-Pavilion-dv6-Notebook-PC:~$ sudo ln -s /usr/local/lib64/wine/ntdll.dll /usr/lib/x86_64-linux-gnu/wine/ntdll.dll.so
ln: failed to create symbolic link `/usr/lib/x86_64-linux-gnu/wine/ntdll.dll.so': File exists
```

---

### Post by matt_symes on 2012-05-25
Hi

Doh ! My bad.

It should have been

```
sudo ln -s /usr/lib/x86_64-linux-gnu/wine/ntdll.dll.so /usr/local/lib64/wine/ntdll.dll
```

I was getting ready to do some painting when i posted that :) Just having a quick break from it now.

Kind regards

---

