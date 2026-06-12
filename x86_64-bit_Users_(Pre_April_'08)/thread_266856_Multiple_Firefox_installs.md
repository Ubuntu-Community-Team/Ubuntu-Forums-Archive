---
title: "Multiple Firefox installs"
date: 2006-09-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by davidsampson on 2006-09-27
I currently have Firefox 1.5.0.7 32-bit edition installed, because I like flash and java.  However, I want to also install 2.0rc1 and 3.0a1 silmultaneously, and still be able to use firefox 1.5.  Is there any way to install 2.0 and 3.0 without sharing library files, so they are all completely independant?  I would love to be able to open 1.5 with 'firefox', 2.0 with 'firefox2' and 3.0 with 'firefox3'

EDIT:  If they are independant, is it possible for them to still share bookmarks?

---

### Post by enzomatrix on 2006-09-27
You can extract different versions of Firefox and use them without sharing version specific libraries.
If you start any of the firefoxes, your default profile brings the bookmarks, and every version can use them.

---

### Post by davidsampson on 2006-09-27
So, how do I install one with out wiping out the old ones?

---

### Post by RAOF on 2006-09-28
Aaargh, double post.

---

### Post by DRF on 2006-09-28
If you install another version of firefox from a .deb it might upgrade (replace) your existing firefox.

But if you download firefox as a binary or source package to be extracted you should be able to extract the file some place and either run a 'firefox' file from what you extracted or read the readme file on how to compile the source (normally something like './configure' then 'make' minus the speach marks).
But if there is a final step like 'sudo make install' then don't bother with that step as that will replace the current firefox, but the previous steps will make the firefox file to run then put it into the folder you extracted. (to compile you may well need to install some programs first using apt or synaptic, like build-essential)

Essentially read the readme file, and as long as you don't do anything via sudo you won't erase your existing firefox. (a normal user not using the sudo command can't replace firefox, but can install and run programs into and from there home folder)

It is a good thing to remember that you can mess around with any programs you like and provided you don't use sudo they can't replace what you already have setup. (Just backup your home folder as those files can be edited without a password being required)

Daniel

---

### Post by enzomatrix on 2006-09-28
Just download Firefox binaries from [www.mozilla.com](www.mozilla.com), extract the file any place you want and run ./firefox from there.
You don't need to compile or use any command after the extraction to use it.

---

### Post by kyllikki on 2008-05-05
I did exactly that but my recently extracted Firefox has no internet access... Any ideas?

---

