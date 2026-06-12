---
title: "Can't Install IE"
date: 2009-08-03
forum: x86 64-bit Users
---

### Post by roystreet on 2009-08-03
Howdy - Yep I want to install internet explorer.  For one there are some sites that require it to view them correctly.  I've followed directions online & it appeared to download & begin it's installation process, when it was done installing I selected that that an icon be on the desktop & there wasn't one anywhere.  Is it possible that it doesn't work since I use a 64 bit OS?

I got the info from ie4linux 

Thanks...
  ~roystreet

---

### Post by theremper on 2009-08-03
1.You need to install Wine and Cabextract.If your source doesn't contain Wine and Cabextract,you can add this source:
Run sudo gedit /etc/apt/sources.list
and then add below two lines to your sources.list:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty universe
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main

Run :

sudo apt-get update
sudo apt-get install wine
sudo apt-get install cabextract

2.installing the ie4linux:

(1)Download the source files by run: wget [http://www.tatanka.com.br/ies4linux/downloads/ies4linux-2.0.tar.gz](http://www.tatanka.com.br/ies4linux/downloads/ies4linux-2.0.tar.gz) -O - | tar xvzf -

If above address is unsuccessful,you also can try this :

wget [http://modzer0.cs.uaf.edu/~hardwarehank/files/ies4linux-2.0.tar.gz](http://modzer0.cs.uaf.edu/~hardwarehank/files/ies4linux-2.0.tar.gz) -O - | tar xvzf -

(2)and then run:

cd ies4linux-2.0
./ies4linux

(3)the installation is begining once you run ./ies4linux.You need to answer severl question during installation:

the fist question is that:

Welcome, ray! I'm IEs4Linux.
I can install IE 6, 5.5 and 5.0 for you easily and quickly.
You are just four 'enter's away from your IEs.
I'll ask you some questions now. Just answer y or n (default answer is the bold one)

so don't estate,just select IE6 and then press "ENTER" :)

the sencond question is :

Do you want to install IE 5.5 SP2 too? [ y / n ]
And do you want to install IE 5.01 SP2? [ y / n ]

as seldom people use IE 5.5,i believe,I choosed NO

the third question is :

IEs can be installed using one of the following locales:
EN-US PT-BR DE FR ES IT NL SV JA KO NO
DA CN TW FI PL HU AR HE CS PT RU EL TR
Default is . Hit enter to keep it or choose a different one:

Choose the locale you want.

(4)once you have selected the lacate,installing procees is done,and then you can run the ie4linux by this command on terminal:

/home/ray/bin/ie6

Enjoy!

---

### Post by roystreet on 2009-08-03
Hi,
   I tried it & got it running.  It was unsuccessful in installing flash, it encountered an error.  I tested a page with flash & it didn't work, so I know it didn't install.  I ran it from the command line & it's IE6 for sure.

Now that I closed it, it doesn't want to open again.  The desktop link doesn't work, so I tried the terminal again & it just hangs there now...So I'm not quite sure what happened?  I was running it at one point & then it seemed to freeze up that application.  I had to force it to quit.

Any thoughts?
~roystreet

---

### Post by ninjapirate89 on 2009-08-03
> **roystreet said:**
> For one there are some sites that require it to view them correctly.
  ~roystreet

Before you go through the trouble of installing IE, try the User Switch Agent addon for firefox.

---

### Post by ell02 on 2009-08-03
Got my IE from [http://www.playonlinux.com/en/](http://www.playonlinux.com/en/) 
though i have not tried installing flash or anything on it.

---

### Post by theremper on 2009-08-03
here is the easy way to install ie and flash for ie on ubuntu. go to [http://www.playonlinux.com/en/](http://www.playonlinux.com/en/) install playonlinux and run it it. With it you can install ie and flash for ie with a single click

---

### Post by roystreet on 2009-08-04
Hello - Playonlinux sounds very interesting.  I installed it & thus far ie installed.  I haven't tried installing flash yet.  I did notice that it requested where I wanted to put a link for ie (On the desktop or menu) but one never showed up on my desktop as I requested.  Any thoughts as to why a shortcut wouldn't show up when  I told it to?

Thanks!
 ~roystreet

---

### Post by arashiko28 on 2009-08-04
Just out of mere curiosity, what web pages are those, if can be told, the ones that require only IE? And that you haven't managed to get them to work properly on firefox, opera, or epiphany? (just to name my main 3 web browsers)... :D

---

### Post by roystreet on 2009-08-04
Hello:
    Some governmental websites will only allow internet explorer.  It specifically requires it by name.  Also, I've run into a banking website that required it.  Some pages you can easily change the rendering engine & it's fine, but some absolutely require it or you can go no further than the first page.

I'm sure there are others & I don't remember all of the ones I've needed it before.

Thanks,
~roystreet

---

