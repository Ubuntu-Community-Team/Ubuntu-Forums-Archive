---
title: "Shortcut (Launcher/Starter) &quot;start in&quot; field"
date: 2008-08-23
forum: Wine
---

### Post by AnvarOne on 2008-08-23
Hello,

I want to test a (medical) program in Ubuntu 8.04.
Now I've allready installed wine so that the windows program could run. But now I have to make a special shortcut (launcher/starter). I know how to make one but I'm missing a certain field.
In a windows enviroment, if you make a shortcut and go the properties afterwards you have "start in" field.
Now for this program to run correctly my "start in" field must be different then my program location.
But in ubuntu there is no "start in" field or something like it. 

My shortcut should be:
prog: /home/name/progname/bin/prog.exe
start in: /home/name/progname/database/

Can someone give me a hand on this one?

Thanks

---

### Post by amitkher on 2008-08-23
write the following into the "Command" field of the launcher:
```

bash -c "cd /home/name/progname/database/ ; /home/name/progname/bin/prog.exe"

```

---

### Post by AnvarOne on 2008-08-23
Amitkher: thanks for the reply.
But the command doesn't start the program. If I start the program without the direction to the database map he gives me an error messages. 
Now I don't see anything. Even if try it in the console with sudo in front of it (then I get the error, "wine isn't owned by you"
Any id what that means?

I've checked my spelling (copy / paste) to be a 100% sure.

thanks for all the reply's...

---

### Post by amitkher on 2008-08-23
Does the following work from the terminal (run it as 2 different commands) ?
```

cd /home/name/progname/database/
/home/name/progname/bin/prog.exe

```

---

### Post by Oldsoldier2003 on 2008-08-23
Moved from GH to Wine for better visibility.

---

### Post by AnvarOne on 2008-08-23
> **amitkher said:**
> Does the following work from the terminal (run it as 2 different commands) ?
```

cd /home/name/progname/database/
/home/name/progname/bin/prog.exe

```
Yup that works perfectly :) 
Can someone explains me the difference between the shortcut and the just launching the app in the database folder (thanks amitkher for the help)

---

### Post by Bios Element on 2008-08-23
Assuming it's a wine program, Prefix the file with wine as in
"wine /file/filehere/anotherfile/launcher.exe".

---

### Post by tomideta on 2011-12-23
hii all..there`s any video that can help..

---

### Post by tomideta on 2011-12-25
how if..the folder been placed from network and use pasword ...

thanks all...

---

### Post by tomideta on 2011-12-27
any one can help me...

i try to make desktop shortcut with a active directory folder to field in the "start in"
i`m using wine for a program ex. mgic program and the folder inside server..

program: "home/buntu/.wine/drive_c/program files/mgic/development/start.exe
start in :   smb://e/server/slnsys/user/folder


can u give me a clue....because i`m new of this...thanks be4 all..

---

