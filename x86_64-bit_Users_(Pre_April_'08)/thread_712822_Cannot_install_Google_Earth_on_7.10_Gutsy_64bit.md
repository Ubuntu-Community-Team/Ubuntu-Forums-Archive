---
title: "Cannot install Google Earth on 7.10 Gutsy 64bit"
date: 2008-03-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by kfir_w on 2008-03-02
Downloaded the binary, have the privileges, but when I run it I get the following error:
[PHP]~/Downloads$ sh GoogleEarthLinux.bin 
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.2.205.5730..............................................................
./setup.sh: 284: setup.data/bin/Linux/amd64/setup.gtk2: not found
./setup.sh: 299: setup.data/bin/Linux/amd64/setup.gtk: not found
The setup program seems to have failed on amd64

Fatal error, installer failed to run at all!
[/PHP]

any ideas?

---

### Post by gn2 on 2008-03-02
Use Flash Earth instead?
[http://www.flashearth.com/](http://www.flashearth.com/)

---

### Post by harvey186 on 2008-03-02
> **kfir_w said:**
> Downloaded the binary, have the privileges, but when I run it I get the following error:
[PHP]~/Downloads$ sh GoogleEarthLinux.bin 
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.2.205.5730..............................................................
./setup.sh: 284: setup.data/bin/Linux/amd64/setup.gtk2: not found
./setup.sh: 299: setup.data/bin/Linux/amd64/setup.gtk: not found
The setup program seems to have failed on amd64

Fatal error, installer failed to run at all!
[/PHP]

any ideas?

Do you have installed gtk2 ??

---

### Post by harvey186 on 2008-03-02
> **gn2 said:**
> Use Flash Earth instead?
[http://www.flashearth.com/](http://www.flashearth.com/)

I only get a black screen on your link :confused:

---

### Post by crjackson on 2008-03-02
> **harvey186 said:**
> I only get a black screen on your link :confused:

The link works fine here.  In fact it shows the exact same image of my house that Google Earth does.

---

### Post by gn2 on 2008-03-02
> **harvey186 said:**
> I only get a black screen on your link :confused:


Have you used Kilz' Flash installer script yet?
It's in a stickied thread: [http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

---

### Post by luvit on 2008-03-15
I just installed Google Earth with ease in just a few steps.
Please [see my blog ]("http://www.yay4u.com/2008/03/install-google-earth.html")for simple intructions that worked for me ;)

---

### Post by jpkotta on 2008-03-15
I prefer the Medibuntu method.  Add the repo and install the "googleearth" package.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by steveneddy on 2008-03-15
Isn't this in the repos?

---

### Post by crjackson on 2008-03-15
> **steveneddy said:**
> Isn't this in the repos?

It is.  Probably Medibuntu repo.  I just installed it and it works very nicely.

---

### Post by utUtu on 2008-03-15
> **kfir_w said:**
> Downloaded the binary, have the privileges, but when I run it I get the following error:
[PHP]~/Downloads$ sh GoogleEarthLinux.bin 
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.2.205.5730..............................................................
./setup.sh: 284: setup.data/bin/Linux/amd64/setup.gtk2: not found
./setup.sh: 299: setup.data/bin/Linux/amd64/setup.gtk: not found
The setup program seems to have failed on amd64

Fatal error, installer failed to run at all!
[/PHP]

any ideas?

What I did was 
```

#make it executable.  Assuming you are in the same directory

chmod +x Google....bin

#Then run the install

./GoogleEarthLinux.bin



```

---

### Post by agtownz on 2008-03-15
Weird, ran perfectly here.  All I did was go to its properties and turn on the thing that lets it be run, double click and just sit back.

---

### Post by crgutierrez on 2008-03-23
> **jpkotta said:**
> I prefer the Medibuntu method.  Add the repo and install the "googleearth" package.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

It worked* for me with the Medibuntu repo. Thanks!!! (*albeit on a good working Geoforce card)

---

### Post by dcstar on 2008-03-24
[http://ubuntuforums.org/showthread.php?t=601272](http://ubuntuforums.org/showthread.php?t=601272)

---

