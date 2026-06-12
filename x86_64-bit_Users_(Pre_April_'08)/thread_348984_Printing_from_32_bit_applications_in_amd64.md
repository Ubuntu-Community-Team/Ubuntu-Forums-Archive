---
title: "Printing from 32 bit applications in amd64"
date: 2007-01-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by Angafirith on 2007-01-29
A while back, I installed a 32-bit version of firefox using a guide in the FAQs and Howtos section. I recently realized that I cannot print any webpages from the 32-bit version; I have to open them in my default (64-bit) firefox in order to print them.

Does anyone have any ideas as to what I can do?

---

### Post by pseudonym on 2007-01-30
It's probably not the answer you're looking for, but if I want to print a webpage I save it first as a html document, then open it in Openoffice Writer and print from that.

There are 2 good reasons for doing it this way -

1. It's not a good idea to use your Firefox profile to run multiple versions of the browser (can cause things not to work over time). I guess you could create another profile for Firefox64 and tell it to start under that, but I've never bothered to try (I don't print many webpages).

2. Openoffice trims the page down a bit (fewer borders and frames) while still keeping it looking good. I guess this saves some printer ink :)

Of course, the real solution is to be able to print from Firefox32. I don't think you can do that, though, unless you are running it from within a chroot, which IMHO amounts to buggy overkill.

---

### Post by Kilz on 2007-01-30
It isnt possible to print out a web page from the 32bit browser. The reason is the printer driver /cups is 64bit. Pseudonym gave you a good idea. But it is also possible select "print to file" on the printer box that opens when you try to print. This will create a post script document. You can then open this document and print it in the pdf viewer..

---

### Post by Angafirith on 2007-01-31
I figured that it was something along those lines. Is it possible to install the 32-bit printer drivers on a 64-bit system? Maybe I'll see if I can figure something out.

---

### Post by scorpio810 on 2007-02-01
why wine no find printer on 64 bits , but crossover yes

---

