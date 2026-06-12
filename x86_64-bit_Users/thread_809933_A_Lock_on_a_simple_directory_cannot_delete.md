---
title: "A Lock on a simple directory? cannot delete"
date: 2008-05-27
forum: x86 64-bit Users
---

### Post by mike_302 on 2008-05-27
Hi, I am having ZERO luck so far with this Hardy Heron. I had more luck in gutsy... But I am not here to start an argument on that. I am here to find out why I cannot delete a file that I "accidentally" and unknowingly created on my desktop by using "alien" to convert the Adobe Flash RPM file into a tar file. I did the sudo alien -k file-name.rpm command in terminal like I was told to by a website, and that file was created on the dekstop with a lock over it. I still don't know how to get the flash player to install so I just decided to give up and delte the folder, but it has a lock on it and even "sudo rm filename" won't let me get rid of it (and yes, I'm on the desktop directory) because it says it cannot remove a directory? 

I have no idea what is going on. I have yet to have luck installing a single program that I downloaded the tar for. Not one of them seems to work for me. I need some help here guys. 

Sorry for hte dumb questions and thanks for any help you can give!

---

### Post by Bataille23 on 2008-05-27
No such thing as a dumb question.  What you need to do in order to remove a directory is this:

```
sudo rm **-r** *directoryname*/
```

The "**-r**" option allows you to remove *recursively*, which, for lack of a better definition, allows you to remove a folder and its contents.

---

### Post by mike_302 on 2008-05-27
Worked! Thanks so much. I might try to use the tutorial in this forum on installing flash for 64-bit ubuntu... Maybe that will show more luck... But I still don't understand how to install .tar files! I mean, I love linux for its freedom, and many other things, but I still honestly believe that its this type of thing that is slowing it down.

Should I start a new thread on this question or can you answer it here? I HAVE googled "how to install .tar files" and found one sort of helpful site but even following the instructions there, I had little luck installing programs.

---

### Post by Bataille23 on 2008-05-27
> **mike_302 said:**
> Worked! Thanks so much. I might try to use the tutorial in this forum on installing flash for 64-bit ubuntu... Maybe that will show more luck... But I still don't understand how to install .tar files! I mean, I love linux for its freedom, and many other things, but I still honestly believe that its this type of thing that is slowing it down.

Should I start a new thread on this question or can you answer it here? I HAVE googled "how to install .tar files" and found one sort of helpful site but even following the instructions there, I had little luck installing programs.

Well, if I can't answer your question here, I'd start a new thread.

If you're downloading a .tar file (or .tar.gz, .tar.bz2, etc.) you SHOULD be able to open it with the archive manager (and subsequently extract it).  I'd extract it to the desktop, but that's just personal preference.  With a .tar* file, you're almost always going to be building from source, and while this can be extremely handy if you want to run a program that isn't available in the repositories, it DOES pose some problems as far as dependencies go (if you're not familiar with "dependencies," trust me, you soon will be).  Basically, if you don't have all the libs and soforth that the app requires, it will abort when you attempt to compile it (on the brightside, the terminal should print out which dependencies you're missing).  The typical (and ideal) installation will go something like this:

in the terminal, enter the folder containing the source (usually it comes in a "bin" sub-folder) like so (and assuming you extracted it to your desktop): ```
cd Desktop/*foldername*/
```.  Then, ```
sudo ./configure
``` (note: "sudo" may not be necessary, but I always use it, regardless), after which you'll enter ```
make
```, and assuming that everything's going as planned, ```
make install
```.  I could be leaving out a step (for obvious reasons, I manually compile programs only when I absolutely have to), but there's a million guides on the web that gives very precise instructions on what to do.  

I'm glad I was able to be of some help with the locked folder.  Hopefully you'll find this useful as well.

---

### Post by pixel :-) on 2008-05-28
i would recommend checkinstall,instaid of make install,it builds for you a package and installs it.

for installing programs use synaptic,a more newbie friendly version of it,it's "add remove programs" in the menu,you'll find 95% of what you ever need,compiling is for special cases only."Adobe Flash RPM file into a tar file",this is 32 bit,it will not work,use the command below.

for flash 
sudo apt-get install flashplugin-nonfree

There are 2 types of tar filles for instalation.the source that you have to compile.And binary ,a very primitive packages(first type that ever existed) that you can transform with alien.

Your directory was belonging at root,that why you couldn't remove it.

What other tar filles you tryied to install and didn't work,we are all ears.

---

### Post by mike_302 on 2008-05-28
thanks! It was helpful.

---

### Post by Bataille23 on 2008-05-28
> **pixel :-) said:**
> i would recommend checkinstall,instaid of make install,it builds for you a package and installs it.

Pixel's right.  checkinstall is, generally speaking, a better option.  Sorry I didn't mention that...  :-?

---

