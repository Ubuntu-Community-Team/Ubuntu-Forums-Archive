---
title: "can't import firefox bookmarks from html"
date: 2009-08-28
forum: x86 64-bit Users
---

### Post by jmarks on 2009-08-28
I'm running 64 bit jaunty and can't import my firefox bookmarks which I saved from my windows machine as an html file. I can certainly view the bookmarks file in firefox, and the links on that page are active. Navigating to and importing the HTML file does not bring up an error, but no bookmarks are added.
Can anybody tell me what I am doing wrong?
thanks!
jm

---

### Post by Yellow Pasque on 2009-08-29
Interesting. Try starting firefox from the terminal and importing the bookmarks. Maybe a more helpful error will be printed there.

---

### Post by x33a on 2009-08-29
also, try importing it with febe.

[https://addons.mozilla.org/en-US/firefox/addon/2109](https://addons.mozilla.org/en-US/firefox/addon/2109)

---

### Post by yotis on 2009-09-01
If you still didn't found a solution, maybe you can try [xmarks]("http://www.xmarks.com") and synchronize your bookmarks from another PC.

---

### Post by DaithiF on 2009-09-01
just speculating, but the windows bookmarks file will have windows line endings.  maybe its those that is causing the problem.  (seems a tad unlikely for a cross-platform browser, but who knows!)

try 
```
sed 's/\r//' bookmarks.html > bookmarks2.html
```
to create a new file with unix line-endings, and see if you can import that.

---

