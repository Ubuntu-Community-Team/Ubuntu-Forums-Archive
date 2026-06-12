---
title: "I need step by step guide to uninstalling wine"
date: 2006-08-27
forum: Wine
---

### Post by EDog046 on 2006-08-27
after installing wine I can't run any 3d games properly, I want to get rid of wine so i can play my regular linux games.  Any other suggestions on how to fix my problem are welcome.

---

### Post by yfronto on 2006-08-27
I would recommend trying this:

```

sudo apt-get --purge remove wine

```

Then navigate to your ~/ and delete the .wine directory.

---

### Post by EDog046 on 2006-08-27
Terminal says "package wine is not installed" if this matters I installed it on 64 bit Ubuntu using a guide I found on these forums.

---

### Post by yfronto on 2006-08-27
How did you install it? If it's an RPM you could just rpm -e <package name>. But the package name is the actual name of the package, with numbers and whatnot. Or if you did it through Synaptic, you could just uncheck it. I'm assuming you used a command of some sort?

EDIT: 
If you used dpkg, you could type :
dpkg -r <package name>
Again, the package name has all the crazy numbers and stuff in it.

---

### Post by EDog046 on 2006-08-27
I used this command "sudo dpkg --force-architecture -i wine_0.9.19~winehq1~ubuntu~6.06-2_i386.deb" to install it

---

### Post by EDog046 on 2006-08-27
Can you tell me exactly what to type? I keep getting errors, the filename is wine_0.9.20~winehq0~ubuntu~6.06-1_i386.deb

---

### Post by yfronto on 2006-08-27
Try:

```

sudo dpkg -r wine_0.9.19~winehq1~ubuntu~6.06-2_i386.deb

```

EDIT:

One more thing, though, make sure when you type:

```

dpkg -l|grep wine

```

the packages listed match the syntax with what you're trying to remove.

---

### Post by EDog046 on 2006-08-27
sorry i forgot to fix the command, i had to change it to match the file's actual name, the guide i used to install was outdated

I tried that command and changed it to my file's name and it terminal tells me "dpkg: you must specify packages by their own names, not by quoting the names of the files they come in" and lists these options for me 
"Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*]."

---

### Post by yfronto on 2006-08-27
Yeah, I just typed dpkg -l|grep wine for myself, and I get :

```

ii  wine                                   0.9.20~winehq0~ubuntu~6.06-1    Microsoft Windows Compatibility Layer (Binar

```

So I would type:

```

sudo dpkg -r 0.9.20~winehq0~ubuntu~6.06-1

```

EDIT:


Actually....
I'm a retard, try:

```

sudo dpkg -r wine

```

KISS, right? ;)

---

### Post by EDog046 on 2006-08-27
You're the best, thanks for all of the help **gives lots of cookies** :D

---

### Post by EDog046 on 2006-08-27
OMFG you're last edit worked, it removed wine and my games work properly now thank you so much!!

---

### Post by yfronto on 2006-08-28
No problem, I've been uninstalling/reinstalling various packages all day, so at least I can offer my help on something. Glad to hear you got everything working well. Cheers.

---

### Post by mkquist on 2006-09-02
thanx from me too, was trying to do the same and that last command capped it.... thanx again =D>

---

### Post by Mimsy on 2006-09-06
Awesome! My stupid wine install that I managed to FUBAR pretty badly this morning, is now gone, and I can start fresh. Thank you!

/Mimsy

---

### Post by Mimsy on 2006-09-06
I realised I have one more question. Since I want to start over completely with Wine, do I need to manually remove all the folders and files that were left behind (I can see them in the file browser), and how do I do that? Just delete them, or is that a bad thing to do?

Thanks again,
Mimsy

---

### Post by HAARP on 2006-09-06
The .wine folder in your home folder? Yup, I'd recommened deleting this one to start over.

---

### Post by sk8dork on 2008-09-04
holy crap i had this same exact problem and your solution worked for me! thanks!!!! =D

---

### Post by funkyjan on 2011-04-09
1 go to the applications tab
2. click ubuntu software center 
3. go to installed software on the left
4. find wine(its on the bottom)
5.click wine then go to uninstall

---

