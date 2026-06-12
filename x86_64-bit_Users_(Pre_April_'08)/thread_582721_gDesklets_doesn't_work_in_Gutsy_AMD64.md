---
title: "gDesklets doesn't work in Gutsy AMD64"
date: 2007-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by limaunion on 2007-10-20
Hi all! Any idea why gDesklets doesn't work in Gutsy?, I'm getting the following error:

Log messages of /home/user/.gdesklets/logs/gdesklets%3A0.0.log
/usr/lib/gdesklets/main/__init__.py:118: GtkDeprecationWarning: gtk.threads_init is deprecated, use gtk.gdk.threads_init instead
  gtk.threads_init()

==========================================================[10/19/07-07:53:34]===
Could not import tiling module!

-------------------------------------------

There's a bug report but nobody cares, what can I do? Should I open a new one ?
[https://bugs.launchpad.net/ubuntu/gutsy/+source/gdesklets/+bug/83922](https://bugs.launchpad.net/ubuntu/gutsy/+source/gdesklets/+bug/83922)

Thanks!

---

### Post by pilotet on 2007-10-20
Same problem.
I remember in Festy there was a link to fix it but now I can't find it.
May be Automatix can help.

---

### Post by tarekeldeeb on 2007-10-24
Grrrr.... same here !

any help ?

---

### Post by dagrump on 2007-10-24
They work on my system but, I can't remember where the .deb came from. I think maybe from debian repos, but I'm not positive. I do believe I down loaded a .deb file though.
Well after looking it's a ubuntu  .deb so I might have used the one from fiesty. Yeah version numbers look to be feisty, but seems to work.

---

### Post by chris062689 on 2007-10-25
Has anyone got this working?
Can you supply the .deb file?

---

### Post by CosminGC on 2007-10-25
same for me: gdesklets not starting :(

---

### Post by dagrump on 2007-10-25
I'm still at a loss as to where the .deb I used came from, but you might look at [www.gdesklets.org](www.gdesklets.org)

---

### Post by kansukee on 2007-10-25
I had the same problem and found a solution;don't remember the exact webpage but basicallly what it boils down to is that gdesklets use the python 2.4 libraries and 2.5 is the default in Gutsy. So,what needs to be done and worked for me is to replace the first line in these files:
/usr/lib/gdesklets/gdesklets
/usr/lib/gdesklets/gdesklets-shell
/usr/lib/gdesklets/gdesklets-daemon
/usr/lib/gdesklets/gdesklets-migration-tool

 that says "#! /usr/bin/env python" and just add "2.4" so it looks like "#! /usr/bin/env python2.4".
Of course you would have to have python 2.4 installed to make this work.Good luck!

---

### Post by CosminGC on 2007-10-26
cool that worked

---

### Post by Merlintrix on 2007-10-26
brilliant solution!
had this problem with feisty too.:(

---

### Post by G.N.I.L.F on 2007-10-31
Found The Old Fix!



- Installed gdesklet and gdesklet-data using synaptic
- Download Dizzi's package
- Extract 'lib' folder from the package
- Copy it onto /usr/lib/

---

### Post by tekhawk on 2007-10-31
another issue with gdesklets is the fact it wont work with xgl... in case the above doesnt work for someone reading this later that might be good to know : )

---

### Post by ArchangelUriel on 2007-11-14
> **kansukee said:**
> I had the same problem and found a solution;don't remember the exact webpage but basicallly what it boils down to is that gdesklets use the python 2.4 libraries and 2.5 is the default in Gutsy. So,what needs to be done and worked for me is to replace the first line in these files:
/usr/lib/gdesklets/gdesklets
/usr/lib/gdesklets/gdesklets-shell
/usr/lib/gdesklets/gdesklets-daemon
/usr/lib/gdesklets/gdesklets-migration-tool

 that says "#! /usr/bin/env python" and just add "2.4" so it looks like "#! /usr/bin/env python2.4".
Of course you would have to have python 2.4 installed to make this work.Good luck!
Thanx kansukee. This also worked for me...

---

### Post by RavanH on 2007-11-14
> **kansukee said:**
> I had the same problem and found a solution;don't remember the exact webpage but basicallly what it boils down to is that gdesklets use the python 2.4 libraries and 2.5 is the default in Gutsy. So,what needs to be done and worked for me is to replace the first line in these files:
/usr/lib/gdesklets/gdesklets
/usr/lib/gdesklets/gdesklets-shell
/usr/lib/gdesklets/gdesklets-daemon
/usr/lib/gdesklets/gdesklets-migration-tool

 that says "#! /usr/bin/env python" and just add "2.4" so it looks like "#! /usr/bin/env python2.4".
Of course you would have to have python 2.4 installed to make this work.Good luck!

That worked! Thanks :)

---

### Post by odiseo77 on 2007-11-18
Hi, I followed the method suggested by kansukee in order to make gdesklets work, but every time I try to start a hardware monitoring desklet (like the SideCandy CPU , SideCandy RAM or SideCandy network), it throws an error window telling me something like the desklet couldn't be opened because the interface couldn't be found (in case of the network desklet). In case this helps, I'm using Gutsy 64 bits on a Core 2 Duo. Has anyone the same problem?

Thanks in advance.

---

### Post by Ubun2User on 2007-11-24
I used GNILF's old fix but the problem I am having now is that there is this background magnification box that stays around the desklet.  Anyone have any ideas?

---

### Post by muncrief on 2007-11-24
I'm running Ubuntu Gutsy AMD64 and had to add "python2.4" to the following files also. After this, the desklets I've tried so far, including Side-Candy CPU, are working. If anyone has any other gdesklet problem I would look for  "#! /usr/bin/env python" in any files having to do with it and change it to "#! /usr/bin/env python2.4". Remember you must also "sudo aptitude install python2.4" to install the correct python because the gdesklets package doesn't have its dependencies set up correctly.

Here are the extra files I had to change:

/usr/lib/gdesklets/ctrlinfo
/usr/lib/gdesklets/gdesklets-logview
/usr/lib/gdesklets/test-control.py

And here are the files, originally identified by kansukee, that also need to be modified:

/usr/lib/gdesklets/gdesklets
/usr/lib/gdesklets/gdesklets-shell
/usr/lib/gdesklets/gdesklets-daemon
/usr/lib/gdesklets/gdesklets-migration-tool

---

### Post by apothecaryaaron on 2007-12-07
python2.4 worked for me as well!

---

### Post by Gourgi on 2007-12-07
> **apothecaryaaron said:**
> python2.4 worked for me as well!

the workaround worked for me also.

---

### Post by Victormd on 2007-12-17
Awesome!
One question though (I'm very new at all this) why do they release a newer version if it's not backward compatible? Or forward compatible for that matter (gdesklets -> Python)?

Thanks for the fix!!!

---

### Post by Luis Macias on 2007-12-23
thanks!!

---

### Post by radstrat on 2008-02-12
Thanks kansukee! That worked like a charm.

---

### Post by yasman on 2008-02-21
Worked for me too!
Thanks man!

---

### Post by hairshirt on 2008-03-16
> **muncrief said:**
> I'm running Ubuntu Gutsy AMD64 and had to add "python2.4" to the following files also. After this, the desklets I've tried so far, including Side-Candy CPU, are working. If anyone has any other gdesklet problem I would look for  "#! /usr/bin/env python" in any files having to do with it and change it to "#! /usr/bin/env python2.4". Remember you must also "sudo aptitude install python2.4" to install the correct python because the gdesklets package doesn't have its dependencies set up correctly.

Here are the extra files I had to change:

/usr/lib/gdesklets/ctrlinfo
/usr/lib/gdesklets/gdesklets-logview
/usr/lib/gdesklets/test-control.py

And here are the files, originally identified by kansukee, that also need to be modified:

/usr/lib/gdesklets/gdesklets
/usr/lib/gdesklets/gdesklets-shell
/usr/lib/gdesklets/gdesklets-daemon
/usr/lib/gdesklets/gdesklets-migration-tool

GREAT! did the trick for me ... many thanks indeed.

---

### Post by ironjon on 2008-04-12
> **G.N.I.L.F said:**
> Found The Old Fix!



- Installed gdesklet and gdesklet-data using synaptic
- Download Dizzi's package
- Extract 'lib' folder from the package
- Copy it onto /usr/lib/

thanks!!!  :)

---

### Post by Jimmy9pints on 2008-04-13
I have the same problem here. When I start gDesklets a window pops up but it is blank. After a while it greys out.

> **kansukee said:**
> I had the same problem and found a solution;don't remember the exact webpage but basicallly what it boils down to is that gdesklets use the python 2.4 libraries and 2.5 is the default in Gutsy. So,what needs to be done and worked for me is to replace the first line in these files:
/usr/lib/gdesklets/gdesklets
/usr/lib/gdesklets/gdesklets-shell
/usr/lib/gdesklets/gdesklets-daemon
/usr/lib/gdesklets/gdesklets-migration-tool

 that says "#! /usr/bin/env python" and just add "2.4" so it looks like "#! /usr/bin/env python2.4".
Of course you would have to have python 2.4 installed to make this work.Good luck!

Please can somebody explain this advice to me? Sorry, I am a newbie. 

1. How do I replace the first line in these files?
2. How do I make sure python 2.4 is installed?

Thanks in advance...

---

### Post by podfish on 2008-04-16
2.  use synaptic, and install the package "python-all".
1.  open a terminal, and use nano to physically edit the files, as follows:
```
steve@pitchblende:~$ sudo nano -w /usr/lib/gdesklets/gdesklets
steve@pitchblende:~$ sudo nano -w /usr/lib/gdesklets/gdesklets-shell 
steve@pitchblende:~$ sudo nano -w /usr/lib/gdesklets/gdesklets-daemon 
steve@pitchblende:~$ sudo nano -w /usr/lib/gdesklets/gdesklets-migration-tool 
```
as the previous poster says, just add 2.4 after python in the first line of each file so it reads "python2.4" along with the rest of the line.  That first line tells the system which python interpreter to use, and this version of gdesklets is using the wrong one!

Make the first line of each of those files look like this:
```
#! /usr/bin/env python2.4
```

The Podfish

p.s. muncrief, youdaman

---

### Post by hellmet on 2008-04-29
It doesn't work. gDesklets keeps trying to establish some connection!!

---

### Post by semgok on 2008-05-26
Solved.

Hi.I am using Core 2 Duo 64 bit and ubuntu 8.04 64 b&#351;t and i had a problem gdesklet.

But i solved this problem with pyton2.4(change gdesklets file python2.4 from python ) and download gdesklets3.5 for amd 64 from below link:

[http://ubuntuforums.org/showpost.php?p=3676373&postcount=11]("http://ubuntuforums.org/showpost.php?p=3676373&postcount=11")

thanks G.N.I.L.F for deb file.

---

### Post by NNG on 2008-06-20
> **G.N.I.L.F said:**
> Found The Old Fix!



- Installed gdesklet and gdesklet-data using synaptic
- Download Dizzi's package
- Extract 'lib' folder from the package
- Copy it onto /usr/lib/
The attached file was the only fix that worked for me 

Using Hardy Heron AMD64

---

### Post by echeddar on 2008-06-26
Hi, I'm a total newb to Linux and Ubuntu, and decided to try the advice on this thread to put widgets on the desktop.  Without knowing quite what I was doing, I managed to get a terminal and edit the first lines of the files to [FONT="Fixedsys"]python2.4[/FONT].  I only got a blank window called gdesklets Shell, so then I also installed the python-all package.

When that didn't do it, got the file from Dizzi's post, managed to unpack the lib folder to my desktop, and set about copying it (via drag and drop) to /usr/lib.  But I don't have permission.  I learned while editing the files about sudo, so I suppose I could get permission that way to move the files, but I don't know how to find the folder (which is on my desktop) in the terminal interface.  

It looks like I'm on my desktop already (in the terminal, my prompt is 
[FONT="Fixedsys"]user@user-desktop:~$[/FONT]
so I guess that means that's where I'm at.)  I tried ls to see if I could see the files on my desktop, but got a list of words that looks like my "places" menu items (desktop, videos, etc.) and I was not able to find my way into those places within the terminal.  

I think I'm lacking some basic understanding of the structure and function of the file system in linux.  Any good beginner tutorials or pages?  Should I be looking just for Ubuntu, or will other kinds of Linux work pretty much the same way?

Thanks,
echeddar

---

### Post by stumbleUpon on 2008-07-23
> **NNG said:**
> The attached file was the only fix that worked for me 

Using Hardy Heron AMD64
This was the only one that worked for me too...!!
I am using Hardy 64-bit
Thanks.

---

