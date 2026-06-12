---
title: "Wine &amp; Powerpoint 2003--Everything works fine, cept Print menu"
date: 2008-03-10
forum: Wine
---

### Post by jorwex on 2008-03-10
Hey all,

so I have Office 2003 running great under Wine 0.9.56. When i go to print in Word, all of the menu's show up fine, but if I do the same in Powerpoint, the drop down menu's look weird:

Here's Word:
[IMG]http://glue.umd.edu/~jwexler/word.png[/IMG]

Here's Powerpoint:
[IMG]http://glue.umd.edu/~jwexler/ppt.png[/IMG]


Anyone heard of this problem? I can't find it documented anywhere. Thanks!

-Jordan

---

### Post by Narpa on 2008-06-19
I encountered this problem as well on wine 1.0.
I fixed it by installing msxml3, riched20 and riched30 using winetricks
[http://www.kegel.com/wine/winetricks]("http://www.kegel.com/wine/winetricks")

Just download the script, give it execute permissions and run
$ ./winetricks msxml3 riched20 riched30

---

### Post by bastos77 on 2008-08-08
Thank you very much for this hint. works perfect.

---

