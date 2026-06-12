---
title: "wine and MS Office Word Problem"
date: 2007-12-30
forum: Wine
---

### Post by rick_woodham on 2007-12-30
Greetings forum.  I have installed wine 9.46 on my current version of Ubuntu.  The installation goes smoothly, without errors.  However, when I start to run Word (or any of the other applications), I get an error from the application that says "This has not been installed for the current user, please run setup.....).  When I did the install from the command line, I did it as the user I normally use.  I have uninstalled, run under root, I've reinstalled several times with the same results.  I have  modified the system.reg file to reflect my user ID, paying attention to case sensitivity.  I'm open to suggestions on what I might be able to try to get past this little challenge.  Thanks in advance for the help.

---

### Post by word20 on 2007-12-30
Hi,
Do you have OpenOffice, the latest version?
OpenOffice should be able to read word documents.

word20

---

### Post by word20 on 2007-12-30
Hi,
in open office you should find *.doc.
this will be able to read word documents.

word20

---

### Post by jeffus_il on 2007-12-30
Openoffice Writer and abiword will read word documents easily.
There is no need to battle with wine and word.

You can install openoffice.org-writer using synaptic or
sudo apt-get install openoffice.org-writer
at the command prompt in a terminal window.

---

### Post by rick_woodham on 2007-12-30
Yes, I do have OpenOffice installed and I like using it.  My main purpose for going down the MS Office path was primarily Powerpoint.  I do a lot of presentations and have had problems in the past with  moving .ppt files across to OO and not have formatting problems.

---

### Post by rick_woodham on 2008-01-01
I have reinstalled MS Office, once again.  This time all is working well.  Wish I could tell you what I did differently.

---

