---
title: "Unsolvable problem - please help"
date: 2007-02-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by DaRush on 2007-02-09
I've encountered a problem that I have no idea how to even begin solving.

Alright, I'm running Ubuntu 6.10 X86_64 on my laptop, with a 2.6.19.1 kernel.  I'm trying to install a screenwriting program called Celtx ([www.celtx.com)](www.celtx.com)).

After unpacking the tar.gz file (which is already compiled), instructions say to simply run run the "celtx" file from the new directory it created.  When I attempt to do this, it gives me the following message:

(after typing ./celtx in the same directory)
./run-mozilla.sh: 424: ./celtx-bin: not found

**Both of these files are present in the same directory.  **

(after trying to run this file with sh. run-mozilla.sh i get this message)
run-mozilla.sh: Cannot execute .

Being baffled by this I had my cousin attempt installing the same program (following the same two step process).  His 32 bit Kubuntu ran it instantly.  I've also attempted running this program the same way in my Fedora Core 6 X86_64 on my desktop, and after installing the 32 bit libraries It worked like a charm.  I've installed the 32 bit libraries on my laptop as well, but this doesn't change anything - making me think there is a flaw somewhere else in my system - it simply does not want to run these files (keep in mind i've tried the same thing 5 times, including downloading the tar again and i know the files are good themselves).

I've also attempted to run this locally and as root, and that again changes nothing.

This makes me thing that there is a problem with the shell itself on my system, actually I don't even know what to think :confused:  :confused:  :confused:  :confused: 

If anyone can even point me in the right direction, it would be of help.

Oh also, I could just be an idiot, but that's fine as long as I can get this to run.  (I really need this app.)

---

### Post by kevinlyfellow on 2007-02-10
> I've also attempted running this program the same way in my Fedora Core 6 X86_64 on my desktop, and after installing the 32 bit libraries It worked like a charm.

What did it do before you installed the 32bit libs?  Was it the same as the machine your working on?

> Oh also, I could just be an idiot, but that's fine as long as I can get this to run. 

Does run-mozilla.sh and celtx-bin have executable permission?

---

### Post by #Reistlehr- on 2007-02-10
download the 32-bit libraries.

type this in the terminal

sudo apt-get install -y ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk gsfonts gsfonts-x11 linux

---

### Post by DaRush on 2007-02-10
Alright thanks for the replies,

Yes the files have executable permission.  Initially the error it gave me in Fedora Core 6 x83_64 was different - it implied there was a problem lib32stdc++5 or 6 library, i believe.  Updating the 32 bit libraries did the trick in that case.

I cut and pasted the above command.  I was given this:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gsfonts is already the newest version.
The following extra packages will be installed:
  lib32gcc1 lib32stdc++6 lib32z1 libc6-i386
Suggested packages:
  ia32-libs-kde libasound2-plugins
The following NEW packages will be installed:
  gsfonts-x11 ia32-libs ia32-libs-gtk ia32-libs-sdl lib32asound2 lib32gcc1
  lib32ncurses5 lib32stdc++6 lib32z1 libc6-i386 linux
0 upgraded, 11 newly installed, 0 to remove and 19 not upgraded.
Need to get 25.0MB of archives.
After unpacking 66.0MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  linux
E: There are problems and -y was used without --force-yes

what is the command for preventing authentication?

---

### Post by kevinlyfellow on 2007-02-10
Sometimes I have that issue to, even with official security releases... Unfortunately I have no idea why

---

### Post by DaRush on 2007-02-11
Thanks for the help!

The 32 bit libraries were the problem, and after their successful installation using the above command (thanks #Reistlehr-), I was able to run this software! :) :) :) 

Btw, if anyone is interested in screen writing and needs an open-source alternative to Final Draft, this seems to do the trick ([www.celtx.com).:popcorn:](www.celtx.com).:popcorn:)

---

### Post by James Bennett on 2007-02-11
I am having a similar problem getting Celtx to load, and would like to try this method of solving it. However, when I copy-paste the apt-get for the 32-bit libraries I get this error message.

terminal:~$ sudo apt-get install -y lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk gsfonts gsfonts-x11 linux
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package lib32asound2

Is there a particular repository I need to enable?

---

### Post by DaRush on 2007-02-11
I have all of the repositories enabled.  After trying this for the second time I installed some packages but couldn't get all of them for whatever reason.   
I used the --install-missing command (or something similar to that - i forget) and added that to the above command, that installed the rest of the packages successfully and I was good to go.

---

