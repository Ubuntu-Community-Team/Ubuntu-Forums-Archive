---
title: "Kivio on Breezy-64?"
date: 2006-01-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-01-17
I wanted to try Kivio, which is a structured drawing app that is part of the KDE office suite. I am already committed to OpenOffice.org, having used it for a long time, but I need a structured drawing app like Visio. Kivio seemed to be the best choice.

But after installing it I can't get it to run. It won't launch from the Applications menu, and when I try to launch it from the command line I get:

kbuildsycoca running ...
Reusing existing ksycoca
Kbuildsycoca: ERROR creating database'/var/tmp/kdecache-jjj/ksycoca'
Kbuildsycoca: Wrong permissions on directory? Disk full?
koffice (lib kofficecore): ERROR Couldn't find the native MimeType in kivio's 
     desktop file. Check your installation !

Does anyone know what those messages mean and how to fix them?

---

### Post by John Jason Jordan on 2006-01-17
OK, answering my own question. I got it to run, but I had to sudo it from the command line. Does anyone know the solution, given the above error messages when I just type "kivio" instead of "sudo kivio"?

---

### Post by queenorych on 2006-01-19
Do you have  permission to write to /var/tmp/kdecache-jjj/ksycoca

?

---

### Post by John Jason Jordan on 2006-01-20
[QUOTE=queenorych]Do you have  permission to write to /var/tmp/kdecache-jjj/ksycoca?[/QUOTE]
Thanks. That solved it. It just leaves two questions: 

1) I'm the sole user of this computer, usually logged in as jjj. The install utility made me the owner of that folder. But why did it not give me permission for it?
2) Why was I so stupid that I couldn't figure out the problem from the error messages and had to wait until someone pointed out to me something that should have been obvious?

OK, let's not try to answer the second question. I'm pretty sure I don't want to know. ;)

---

### Post by John Jason Jordan on 2006-01-23
I've been trying to use it, but the documentation does not answer a critical question for me. I do not need Kivio for any of the things for which the standard templates that it comes with will serve. I need to create my own custom templates. I can certainly do that easily in a drawing app (Inkscape, etc.), but how do I get the templates into Kivio?

---

