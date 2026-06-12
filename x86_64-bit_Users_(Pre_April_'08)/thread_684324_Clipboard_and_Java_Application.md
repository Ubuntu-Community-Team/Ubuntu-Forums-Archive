---
title: "Clipboard and Java Application"
date: 2008-02-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2008-02-01
I have installed an application written in Java on my Gutsy x86_64 computer. Everything is working fine, except I cannot copy and paste to and from the clipboard. The application is TreeForm:

[http://www.ece.ubc.ca/~donaldd/treeform.htm](http://www.ece.ubc.ca/~donaldd/treeform.htm)

On Sun's site I found these instructions for copying and pasting to and from the Linux clipboard:

[http://java.sun.com/developer/technicalArticles/Programming/linux/](http://java.sun.com/developer/technicalArticles/Programming/linux/)

However, I cannot figure out the instructions. I did not have a ~/.Xdefaults file, so I created one with this text in it (from Sun's instructions): 

*VT100.Translations: #override \
            <Btn3Up>:                select-end(CLIPBOARD) \n\
            <Btn2Up>:                insert-selection(CLIPBOARD) \n

Then I ran the command xrdb -merge $HOME/.Xdefaults, which is supposed to reload updates in the .Xdefaults file. It made no difference.

I don't understand the text above that I put in the .Xdefaults file. What is it supposed to do? In order to copy to/from the clipboard am I supposed to use 2 and 3 or something? Maybe 2 and 3 while selecting with the mouse? Maybe holding down 2 and 3 while sacrificing a chicken?

Any enlightenment appreciated.

---

### Post by achianese on 2008-02-28
I think this is a general bug in Java on Linux. I just installed MarvinSketch, which used Java, and it runs beautifully except that copying and pasting into non-Java apps is broken. Here's a discussion I read from last month:

[http://www.chemaxon.com/forum/viewpost14960.html](http://www.chemaxon.com/forum/viewpost14960.html)

Hopefully Sun will fix it soon.

---

