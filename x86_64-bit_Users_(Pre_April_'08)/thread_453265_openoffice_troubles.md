---
title: "openoffice troubles"
date: 2007-05-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by brazzmonkey on 2007-05-24
hi everyone,
i just got feisty 64bit installed but a few troubles prevent me from using it on a daily basis. a few of them are openoffice-related :

OOo crashed whenever i try to install additional dictionaries.
when copy-pasting from Calc to Writer, the pasted object goes to the very first cell ; i then have to manually edit this object to scroll down to the propers cell.

am i the only one to encounter such troubles ?

cheers

---

### Post by brazzmonkey on 2007-05-24
no one ?

---

### Post by dabl on 2007-05-24
I'll try it this evening from home, and post the results -- where do I find the "additional dictionaries"?  I finally got Beryl working correctly a couple days ago on my 64-bit Ubuntu, so I'm looking for something else to break ...

:D

---

### Post by brazzmonkey on 2007-05-24
thanks dabl, that's very nice from you ;)

for the dictionary thing, open writer, the File > Wizards > Install new dictionaries. it just makes OOo crash in my case (it is supposed to open a text file from which macros will install dictionaries).

could you try this copy/past thing as well, please ? just launch calc and writer ; in calc, write something, say in A10, A11, A12 ; select these cells, copy them and paste them in writer. Do you see those cells in writer ?

many thanks again. should you encounter similar bugs, i'll do a bug report.

cheers.

---

### Post by dabl on 2007-05-24
OK, found it and clicked it, and got the choice of a lot of languages.  I didn't take it any further -- I'll attach the screenshot.  It seems fine here .... let me know if you want me to choose a dictionary to install, and I'll do it.

---

### Post by brazzmonkey on 2007-05-25
ok thanks, so this issue is probably specific to me. could you try the copy/paste thing, please ?

---

### Post by dabl on 2007-05-25
OK, I filled in 6 cells in the spreadsheet, and then did a copy/paste into the writer.  Screenshot attached.  I haven't used OOO that much, and so I'm not experienced, but I was surprised at the way it executed this -- instead of making a table out of the 6 cells, it is more like a "picture" or something -- it seems to have embedded the spreadsheet piece into the document.  I'd have to play with it to figure out how to make a table out of it, I guess.  :?:

---

### Post by brazzmonkey on 2007-05-25
those cells you copied are from the very first rows, right ?

here's what i get when i copy cells from much below in my spreadsheet.

ok, nevermind, i guess i don't have time to waste with 64-bit any more.

thanks for your assistance dabl

---

### Post by dabl on 2007-05-25
I see what you mean -- the 6 cells were not the extreme upper left corner of the spreadsheet, but they were close to it.  So, even though I only highlighted those 6 cells for the "copy", it acts like it copied the entire spreadsheet, and you have to scroll around in the pasted object to get your chosen cells to appear.  That's not good!

But, are you sure this "feature" only exists in the 64-bit version?  I've got Kubuntu 32-bit as well -- I"m going to try that one when I'm home this evening, to see if it is different on this OOO problem.

---

### Post by brazzmonkey on 2007-05-25
sorry if i didn't make it clear at first ;)
it behaves properly on 32bit.

---

### Post by dabl on 2007-05-25
I wonder what happens if you make a graph and then paste that?  Guess I'll have to do some experiments.  :p

---

### Post by Hagar Delest on 2007-05-25
Have you tried to install OOo from the official RPMs (not the Ubuntu ones). Many bugs have been reported for OOo on this Feisty  release. There are some threads about the manual install.

For the dictionary wizard, try to launch it in root running OOo with sudo (just once to install the dics).

---

### Post by brazzmonkey on 2007-05-26
@dabl :
i think copy/pasting graphs behaves correctly (i'll need to check that, though).

@hagar :
(i think we already _met_ on the french OOo forums a few months ago...;) )
i haven't tried official rpms on 64bit yet. feisty version works fine on 32bit.
same thing happens as root with dictionary wizard. maybe i should point out that my user home is shared between 64 and 32bit ubuntu. somehow this is maybe related.

---

### Post by dabl on 2007-05-26
I confirm that pasting cells from Calc into Writer works correctly in 32-bit Feisty, but has the bug described above in 64-bit Feisty.  I haven't tried the graphing experiment yet.

---

### Post by brazzmonkey on 2007-05-28
bug filed : [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/117294](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/117294)

---

