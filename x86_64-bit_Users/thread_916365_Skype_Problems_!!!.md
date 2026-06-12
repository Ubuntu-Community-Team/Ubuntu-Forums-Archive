---
title: "Skype Problems !!!"
date: 2008-09-10
forum: x86 64-bit Users
---

### Post by jukarnarius on 2008-09-10
After several days of hard work I find the Skype version which supports Ubuntu 64-bit and show the pictures in contacts... (of course I install 32-bit libraries but...)

So this version is Static Package, I do not install it, I just unpack it.. so I have to create a luncher,link and the problems begin...

My Skype porks perfectly then I run it bu Nautilus, but whenever I try to use a simple luncher (link) it doesn't work... or rather It works but without sound... 
my launcher works correctly only than launcher and the Skype executable file are placed in the same folder !!!

Pleas help me 
Sincerely yours,
Juka

---

### Post by azzamite on 2008-09-10
Don't velieve me but... gnome executes the launchers from ~ so that may be the reason why the program doesn't find some libs...

You can try executing a bash script, and execute skype from there, kde allows you to define a "execution dir" or somethig
```

#!/bin/bash
cd skype/dir
./skype

```
save it as skype.sh, set it to executable, make the launcher and (hopfully) thats it

---

### Post by Crafty Kisses on 2008-09-11
Try this remove the Skype package and try installing it this way:

Do the following in the Terminal:```
 sudo apt-get install ia32-libs lib32asound2 libasound2-plugins; wget -O skype-install.deb http://www.skype.com/go/getskype-linux-ubuntu; sudo dpkg -i --force-all skype-install.deb; 

```
**Medibuntu's Repositories:**
Medibuntu offers Skype, which can be added to your repositories here: [Medibuntu]("https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f")
You can then install Skype by using your Synaptic Package Manager to search for "Skype" or by the command line:```
sudo apt-get install skype
```

That should work.

---

### Post by soxs on 2008-09-11
I installed skype 64bit from medibuntu repositories and it just works... maybe you should give it a shoot aswell?

---

### Post by jukarnarius on 2008-09-11
Tank you very mach!!!
I use the next actions:

sudo gedit 
   and create bash file with next text
I write this in it:
Code:

#!/bin/bash

cd /home/jukarnarius/skype
./skype

I create Launcher for bash file...

Then do this in terminal:
sudo chmod +x {my bush file}

without this last command my launcher do not work (permission deny)

thank you very much once again..

ps maybe I try install skype from Medibuntu or something else byt now I'm tired... My Skype works and that's enough for me... For my firs week in Ubuntu - I compile to much drivers and write to much scripts...

pps no I think I reinstall Skype in one week... I think reinstalling is my new habit...

---

### Post by jespdj on 2008-09-11
> **soxs said:**
> I installed skype 64bit from medibuntu repositories and it just works... maybe you should give it a shoot aswell?
Installing Skype from the [Medibuntu](http://www.medibuntu.org/) repository is easy. They have a package with 32-bit Skype for x86_64, which includes all the necessary libraries. It's just as easy as installing any other package and doesn't require you to fiddle with libraries and other difficult things.

---

