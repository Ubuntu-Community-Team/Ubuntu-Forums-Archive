---
title: "Installing a single package file [.tar.gz]"
date: 2008-10-18
forum: x86 64-bit Users
---

### Post by saidulhdz on 2008-10-18
hi, i'm an infant user of linux (ubuntu 8.04) and trying to install some of my favourite programs. Specially **[COLOR="Blue"]"truecrypt-6.0a-ubuntu-x86.tar.gz"[/COLOR]** and read the Ubuntu Documentation on *"Installing a single package file"*. where says:  _The first step will be to uncompress and extract the tarball. If it is a .tgz or a .tar.gz, in a Terminal enter:_

tar xfvz tarball_name

I know nothing about terminal man! Tried the GNOME Terminal Manual where only the terminal interface is described. Where can i get a complete list of terminal command? Commands like cd, cd.., dir, run, open, xcopy, etc in windows command prompt?

And right this moment can any angel help me out how can i install this software [COLOR="RoyalBlue"]**"truecrypt-6.0a-ubuntu-x86.tar.gz"**[/COLOR] using this terminal? Please.     :confused:

---

### Post by Rog-Mahal on 2008-10-19
you don't need to use terminal to unpack the file, if that will make your life any easier. Double click on it and it will open File Roller. From there you can extract it. Once that is finished, you will want to open the folder where the files have been extracted. Inside there should be a text file called 'INSTALL' or something like that. Read it for instructions on how to continue. 

As a general rule, to build a program from source you need to open a terminal and get into directory where your extracted files are by typing:

```
cd /yourdirectoryhere
```

Once inside, (you will know you are by watching the prompt, it will tell you what directory you're inside), you need to type the following commands

First:

```
sudo make
```

You will get a lot of computer language looking output, that's normal.

If that succeeds, then you want to type:

```
sudo make install
```

That should install the program. I hope that helps.

As for a complete list of terminal commands, open a terminal window and type "help"

---

