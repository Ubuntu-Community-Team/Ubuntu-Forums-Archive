---
title: "winetools error"
date: 2006-07-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Donnieboii on 2006-07-22
Hi
Yesterday i've installed wine and tried to install wine tools but when i try to run winetools it comes up with this error:

> donnieboii@morpheus:~$ wt
no suitable Wine directory found...
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Wine 0.9.17
wine is executed as wine
Parameters are --noexit
Wine is not configured yet!
Browser is /usr/bin/firefox.
WINEVER is "0.9.17".
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Calls to wine are executed as  "wine".
Config is /home/donnieboii/.wine/winetools.log.
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
donnieboii@morpheus:~$


i thought it had to do with that i had no 32 bit libraries but i've check i do have them... anyone solved this problem yet?

all help is great...

thankss...

Donnieboii

---

### Post by ajgreeny on 2006-07-22
Try running *winecfg* in a terminal and then try again.

---

### Post by Donnieboii on 2006-07-22
what do you mean at the same time?
at the same time doesnt work and seperated neither ... do i have to change something in winecfg?

---

### Post by ajgreeny on 2006-07-22
Sorry I think I'm out of my depth here.  I thought winecfg made a hidden *~/.wine* folder in the correct place automatically.  Anybody else able to help?

---

### Post by Donnieboii on 2006-07-22
ok.. well i think it has something to do with the libraries but i dont know what... i've been using ubuntu just for 2 weeks now... but if anyone here to help?? plzzz

Donnieboii

---

### Post by Kilz on 2006-07-22
> **Donnieboii said:**
> ok.. well i think it has something to do with the libraries but i dont know what... i've been using ubuntu just for 2 weeks now... but if anyone here to help?? plzzz

Donnieboii

Welcome to the wonderful world of making 32bit applications work on 64bit dapper. For the most part it works, but sometimes it can be a pain. You say you have looked for the libs and they are there, but make sure they are in the /usr/lib32 instead of /usr/lib. On a 64bit system /usr/lib is for 64bit lib's, /usr/lib32 is for 32bit libs. [I do have a page that deals with this subject that might help.]("http://www.tghc.org/staticpages/index.php/32bitapplications")

---

### Post by Donnieboii on 2006-07-22
thanks... but thats where i looked... ill have a look on the website aswell thank you... do you mayB kn ow something else that it could be?

Thanks...
Donnieboii

---

### Post by Kilz on 2006-07-22
> **Donnieboii said:**
> thanks... but thats where i looked... ill have a look on the website aswell thank you... do you mayB kn ow something else that it could be?

Thanks...
Donnieboii

it could be that the version of that lib is to old.

---

### Post by juicemansam on 2006-07-23
From my experience, a library not found generally means that it either doesn't exist or that the dynamic loader cannot find it (via built-in paths or LD_LIBRARY_PATH). I also notice that the file /etc/ld.so.conf vanished a while back. Another thing I noticed is that when running **ldconfig -v** there is no mention of /usr/lib32. So if libgtk-1.2.so.0 exists in /usr/lib32, you can try setting the LD_LIBRARY_PATH to include /usr/lib32, or create /etc/ld.so.conf and add /usr/lib32 to it. I don't know why /etc/ld.so.conf disappeard, or if it should stay that way, missing, but creating it and adding the /usr/lib32 line in it does fix library path/location issues.

---

### Post by Donnieboii on 2006-07-24
Thanks it sounds like that will help me... but like I said im just a beginner in ubuntu so could you please tell me how to do it? or add the line to LD_LIBRARY_PATH or create that file??

thanks..

Donnieboii

---

### Post by Kilz on 2006-07-24
> **Donnieboii said:**
> Thanks it sounds like that will help me... but like I said im just a beginner in ubuntu so could you please tell me how to do it? or add the line to LD_LIBRARY_PATH or create that file??

thanks..

Donnieboii
If you are using Ubuntu to edit or create the file the command is.
```
gksudo gedit /etc/ld.so.conf
```

---

### Post by Donnieboii on 2006-07-24
thanks.. what about the ld_library_path??  and what to add in the file??   
(i guess i have to create it cause its empty right??)


Thankss...

Donnieboii

---

### Post by Kilz on 2006-07-24
> **Donnieboii said:**
> thanks.. what about the ld_library_path??  and what to add in the file??   
(i guess i have to create it cause its empty right??)


Thankss...

Donnieboii

"So if libgtk-1.2.so.0 exists in /usr/lib32, you can try setting the LD_LIBRARY_PATH to include /usr/lib32, or **create /etc/ld.so.conf and add _/usr/lib32_ to it**."

From the instructions, you add /usr/lib32 to the file.

---

### Post by Donnieboii on 2006-07-24
thanks:D... im gonna try that... do i need to add lib64 aswell??? 
where do i find the ld_library_path

thanks..:)..

there's another post from me about mercury... do you mayB know a awnser to that aswell??

Donnieboii

---

### Post by Donnieboii on 2006-07-24
i tried to make that file with /usr/lib32 and /usr/lib64 in it then try to do wt in the terminal and it comes up with same error...

how do i edit the LD_LIBRARY_PATH??

thankss...

---

### Post by juicemansam on 2006-07-24
In the console you could type in **export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib32**. That will set the LD_LIBRARY_PATH to what it already has, plus /usr/lib32 (with the colon as a separator). That variable will only work for that console you have open, so in the same console test run the application in question. If that solves the problem, you can add that export line to your /etc/profile file, that way the variable is always set.

---

### Post by Donnieboii on 2006-07-25
no doesnt solve the prob... sorry... 
mayb to reinstall 32bit libraries??? 
I you think that could help it how do I remove them and reinstall them again??

thanks anyway...

Donnieboii

---

### Post by Donnieboii on 2006-07-27
does anyone know? 
if not how do i reinstall 32bit libs??

Donnieboii

---

### Post by juicemansam on 2006-07-27
I'm not sure, but you could try Synaptic. Search for ia32-libs, and Mark for Reinstallation.

---

