---
title: "Printing document --&gt; Terminates Acrobat"
date: 2006-12-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by dimis on 2006-12-29
My pc in a glance:
```
$ uname -a
Linux crag-hack 2.6.15-27-amd64-generic #1 SMP PREEMPT Fri Dec 8 17:50:54 UTC 2006 x86_64 GNU/Linux
$
```
My problem in a glance: Whenever I attempt to print a document via File->Print on Adobe Acrobat 7.0.5 the program terminates and ofcourse nothing is printed. I have attempted to catch an error by opening Acrobat directly from a shell, but no problem appears on console, even though Acrobat terminates. Moreover, acroread really terminates as a
```
ps -e |grep acroread
``` shows. Moreover, I inspected various logs under /var/log/ but couldn't find anything relating to my problem.
Any ideas on how to fix this problem and be able to print documents with Acrobat ??

Thanks to anyone who might reply,
- dimis -

P.S.: Happy New Year!

---

### Post by John Jason Jordan on 2006-12-29
> **dimis said:**
> My problem in a glance: Whenever I attempt to print a document via File->Print on Adobe Acrobat 7.0.5 the program terminates and ofcourse nothing is printed. I have attempted to catch an error by opening Acrobat directly from a shell, but no problem appears on console, even though Acrobat terminates. Moreover, acroread really terminates as a
```
ps -e |grep acroread
``` shows. Moreover, I inspected various logs under /var/log/ but couldn't find anything relating to my problem.
Any ideas on how to fix this problem and be able to print documents with Acrobat ??
I don't think I have the exact solution to your problem, but I can offer a couple of observations that may help.

First, the latest version is 7.08. You might want to try that just in case it solves the problem.
Second, if you have Wine installed, you can install 7.07 for Windows. I use Crossover Office and had no problem installing it, once I found the specific instructions on Crossover's site.
Third, if you haven't already tried it, give Kpdf a go. It's native Linux and prints via CUPS. Adobe Reader is not CUPS-aware, which may be part of the problem.

I have been wrestling with printing PDF files from Linux for some time and I still have to go print them from my Windows computer. I need to print multiple copies collated and Adobe Reader (both the Linux and Windows versions) can do this only by spooling individual print jobs. That makes printing too slow, as each copy has to be re-imaged at the printer. Kpdf can do it without spooling individual print jobs, but its print speed for the first copy is glacial -- a couple of minutes per page.

---

### Post by kleeman on 2006-12-29
Another option is to select custom printer in the acroread printing dialog and in the box on the top right of the dialog select kprinter (you need it installed of course). kprinter has a ton of options for collation etc and this might stop the crashing.....

---

### Post by John Jason Jordan on 2006-12-29
> **kleeman said:**
> Another option is to select custom printer in the acroread printing dialog and in the box on the top right of the dialog select kprinter (you need it installed of course). kprinter has a ton of options for collation etc and this might stop the crashing.....
That must be a KDE only utility. I use the Gnome desktop and my Synaptic does not list kprinter.

---

### Post by kleeman on 2006-12-30
Sorry, the command is kprinter and the package (which is in the main repository) is called kdeprint.
Personally I prefer having full access to both the kde and gnome apps so I install kubuntu-desktop on top of a standard gnome Ubuntu install. It adds roughly 0.5-1GB to /usr

---

### Post by eurgain on 2006-12-30
> **kleeman said:**
> Sorry, the command is kprinter and the package (which is in the main repository) is called kdeprint.
Personally I prefer having full access to both the kde and gnome apps so I install kubuntu-desktop on top of a standard gnome Ubuntu install. It adds roughly 0.5-1GB to /usr

I think you may find that this will not work because Acroread is 32-bit so cannot load the 64-bit libraries.  There are serious a problems printing from 32-bit apps in Ubuntu 64-bit.

A

---

### Post by kleeman on 2006-12-30
> **eurgain said:**
> I think you may find that this will not work because Acroread is 32-bit so cannot load the 64-bit libraries.  There are serious a problems printing from 32-bit apps in Ubuntu 64-bit.

A
You seem to be correct although I could swear it worked earlier :confused: 
If kprinter is replaced with 

lpr -PNAME

where NAME is the name of the printer desired. It seems to work. lpr enables you to do many tricky things as long as you know the right switches.

---

