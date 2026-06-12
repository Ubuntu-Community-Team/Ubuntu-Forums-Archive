---
title: "java and libdc++ error"
date: 2006-04-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by egghead3 on 2006-04-13
I'm trying to install java on my dapper installation ony my 1.5ghz powerbook g4. I downloaded the ibm sdk for java 1.5 ppc as a tar file, untarred it in my /opt directory, and added its bin directory to my path in bashrc. When I try to run java or javac, I get the following error: 

Error loading: libstdc++.so.5: cannot open shared object file: No such file or directory

I'm not sure whats going on here. I checked in synaptic to make sure i have that library installed and indeed i do. Does anyone have any insight?

fwiw, I also tried to install java by using alien to convert the rpm. The generated deb claimed to install correctly, but did not work. It instead made a folder in /opt called 'ibm' which i was unable to open even using sudo. Uninstalling the the package had the unpleasant side effect of removing my entire /opt folder! (fortunately there was nothing else in there)

---

### Post by gerbman on 2006-04-14
What's the output of```
ls -la /usr/lib | grep libstdc++
```

---

### Post by egghead3 on 2006-04-14
```

greg@gregubuntuppc:~$ ls -la /usr/lib | grep libstdc++
lrwxrwxrwx   1 root root       18 2006-04-13 23:40 libstdc++.so.6 -> libstdc++.so.6.0.7
-rw-r--r--   1 root root   982236 2006-04-08 03:27 libstdc++.so.6.0.7

```

I notice it gives a libstdc++.so.6, whereas java is looking for libstdcc.so.5? Do I need to install a previous version of libstdc++?

---

### Post by gerbman on 2006-04-14
[QUOTE=egghead3]```

greg@gregubuntuppc:~$ ls -la /usr/lib | grep libstdc++
lrwxrwxrwx   1 root root       18 2006-04-13 23:40 libstdc++.so.6 -> libstdc++.so.6.0.7
-rw-r--r--   1 root root   982236 2006-04-08 03:27 libstdc++.so.6.0.7

```

I notice it gives a libstdc++.so.6, whereas java is looking for libstdcc.so.5? Do I need to install a previous version of libstdc++?[/QUOTE]Yes, I think so...```
sudo apt-get install libstdc++5
```Hope that works.

---

### Post by egghead3 on 2006-04-14
Yep, that worked great.

Thanks for the help.

---

### Post by pauljwells on 2006-04-19
[QUOTE=egghead3]
fwiw, I also tried to install java by using alien to convert the rpm. The generated deb claimed to install correctly, but did not work. It instead made a folder in /opt called 'ibm' which i was unable to open even using sudo. Uninstalling the the package had the unpleasant side effect of removing my entire /opt folder! (fortunately there was nothing else in there)[/QUOTE]

I also tried the 'alien' route and got the locked ibm folder in /opt. All I had to do to read it was

sudo chmod 755 -R /opt

Then I could see that java had installed properly and it all runs ok. I added the path to the bin folder to my .bashrc and a symbolic link to the firefox plugin as described on the wiki page, but using the /opt paths as appropriate.

---

