---
title: "tuxguitar on 64-bit"
date: 2007-06-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by tjk on 2007-06-14
Has anyone installed tuxguitar on 64-bit feisty?  Can anyone help me install the file:  TuxGuitar-0.9.1-linux-gtk-x86_64  (unless there is a different file to use that works).  I always get the error message that it can't find the file ./configure.

---

### Post by incubus on 2007-06-14
tjk,

I don't have tuxguitar myself, but I could give it a try to help you.  Can you tell me the steps you followed to get where you got?

Wait, I just went there and they do have binaries for amd64 and they work here.  Here's what you do (you already did the first step, I believe):

```

$ tar xzvf TuxGuitar-0.9.1-linux-gtk-x86_64.tar.gz
$ cd TuxGuitar-0.9.1-linux-gtk-x86_64
$ ./tuxguitar

```

No compilation necessary.

Of course, you may want to move it to a more convenient directory and make it so you can invoke it more easily.  Or you may want to have an entry in the menu if you use gnome or kde.  Let us know if you need help with this.

incubus

---

### Post by tjk on 2007-06-15
Hey, thanks a lot.  It seems to be working fine.  

I've been using Linux for about a year now and didn't know that you could just run a package without configuring it...   one day older, one day wiser, maybe...

---

### Post by trepid666 on 2007-06-18
Tuxguitar is amazing! I love this program. Big ups to its creator! I myself had problems installing it on my amd64 laptop. Thanks  to the forums here, I was able to get it running. 

I managed to crash my system with a gnome-panel bug and have just recently reinstalled Ubuntu. So I need to get Tuxguitar again =). Ubuntu is such a great OS!

Would someone please post on how to maybe create a launcher inside of the panel? That would be great.

Thanks.

---

### Post by tjk on 2007-06-19
> **trepid666 said:**
>  
Would someone please post on how to maybe create a launcher inside of the panel? That would be great.

I run Kubuntu, so if you're using Ubuntu (gnome desktop) it will be different.  Try looking in your system settings for something that looks like "Menu Editor".

However, I would make sure that the files have been extracted in the /usr/bin/ folder before making the link in your menu.

BTW, I believe that since this package was installed manually you will have to upgrade the program manually each time -- that is if you want to keep the program up-to-date.

---

### Post by incubus on 2007-06-19
I'm using KDE too, sorry I can't offer much help.  But I also would imagine if you right-click, you should see some option for creating a link.

tjk is right that since you manually installed tuxguitar, it will remain the same in your system unless you install the next version.  But hey, "if it ain't broke..."

Maybe what we should do is request the developers to pack tuxguitar for Gutsy, what do you think?

incubus

---

### Post by incubus on 2007-06-19
> **tjk said:**
> 
However, I would make sure that the files have been extracted in the /usr/bin/ folder before making the link in your menu.

tjk,

This is a matter of personal preference, but I myself feel uncomfortable about extracting the package directly into /usr/bin.  The reason being that that directory is typically reserved for executable binaries.  Here's how I would do it:

```

$ tar xzvf TuxGuitar-0.9.1-linux-gtk-x86_64.tar.gz
$ mv TuxGuitar-0.9.1-linux-gtk-x86_64 tuxguitar
$ sudo cp -R tuxguitar /usr/local/

```

So, in words, I installed the files in the directory /usr/local/tuxguitar.

Then I would create a script "tuxguitar" in /usr/local/bin:
```

#!/bin/bash
cd /usr/local/tuxguitar
./tuxguitar

```
As you can see, all it's doing is going to /usr/local/tuxguitar and invoking the original script.

Finally, I would make it executable:
```

$ sudo chmod +x /usr/local/bin/tuxguitar

```

The reason for going through all this trouble is that the executable script that comes with tuxguitar is a little picky about its files and folders.  The advantage of this method is keeping your system clean.  The disadvantage is that it's a little bit of work.

incubus

---

### Post by trepid666 on 2007-11-07
Cool, thanks for the advice and how-to. =) I have just installed the newest Ubuntu 7.10 from 6.10 and am back to say Ubuntu rocks! I am just cruising around looking to see if we can run TuxGuitar on Gutsy yet. I have tried with source files, deb package, and binaries but when I execute tuxguitar it loads for a while, shows the opening logo then shuts down quickly. When I execute in a Terminal, the terminal gives some errors but shuts down too quickly for me to read. 

Has anyone got this running on a 64 bit yet?

---

### Post by trepid666 on 2007-11-12
hey all, so i've managed to get tuxguitar working a couple times but it won't launch the program now...

any ideas?

---

### Post by neo_001010100 on 2008-01-22
I have extracted the 64bit version as you said and with ./tuxguitar it runs fine.

The problem is that it has the problem "Unavailiable soundband error"

You might say that I am trying to run tuxguitar along with another music program. No just tuxguitar. 

I also tries aoss ./tuxguitar. I also tried to show tuxguitar where exactly are the java midi soundbanks. Nothing... 

When are they gonna add tuxguitar on gutsy???

---

### Post by sirgogo on 2008-01-26
I'm on gusty too. I hope they are going to fix those bugs soon and release the new version! ([http://packages.qa.debian.org/t/tuxguitar.html](http://packages.qa.debian.org/t/tuxguitar.html)).

Ahh. I really want to use this program, but I don't want it to screw around with my system. Hmm...

---

### Post by Grone1985 on 2008-02-27
Hey,
In order to be able to have the sound working I'm having to run this command before running tuxguitar:

```
export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.03
```

Then:

```
cd TuxGuitar
./tuxguitar
```

So, what I want is to make a script that will do all this. Anyone could help me with that?
Thanks!

---

### Post by Cappy on 2008-02-27
> **Grone1985 said:**
> Hey,
In order to be able to have the sound working I'm having to run this command before running tuxguitar:

```
export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.03
```

Then:

```
cd TuxGuitar
./tuxguitar
```

So, what I want is to make a script that will do all this. Anyone could help me with that?
Thanks!

You just put it into a file ("scriptname")
```
#!/bin/bash
export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.03
cd ~/TuxGuitar
./tuxguitar

```

which you can run using ```
bash scriptname
```
or you can chmod +x it and use ```
./scriptname
```
or you can copy it into /usr/bin and use ```
scriptname
```

---

### Post by Grone1985 on 2008-02-27
> **Cappy said:**
> You just put it into a file ("scriptname")
```
#!/bin/bash
export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.03
cd ~/TuxGuitar
./tuxguitar

```

which you can run using ```
bash scriptname
```
or you can chmod +x it and use ```
./scriptname
```
or you can copy it into /usr/bin and use ```
scriptname
```

Thank you!
Works like a charm!

---

