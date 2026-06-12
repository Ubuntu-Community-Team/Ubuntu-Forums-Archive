---
title: "Windows browser plugins"
date: 2016-04-13
forum: Wine
---

### Post by asb3 on 2016-04-13
I want to run a windows only plugin on a web browser. 
1) I've installed Firefox for windows, which I can run under WINE, but I don't know how to add a plugin to it. The downloader asks for a directory, and I don't know where to put it.

2) Can I use WINE to run a windows plugin on Firefox running native on LINUX?  

3) I have a WINE application that opens a browser to access the internet.  I will only open the default browser.  Is it possible to set the Windows Firefox as the default browser?  I tried to set Windows firefox as the default browser using system settings, but is isn't listed.  I tried to set Windows Firefox as the default browser from inside firefox, but it didn't work.

Thanks in advance.

---

### Post by T.J. on 2016-04-13
It is theoretically possible to use a browser and plugins under WINE, but it will be highly prone to crashes and security issues, which is why it is not recommended.  You may need additional patches to make the browser work correctly.  If you want to proceed, understanding that you may have serious problems, you should investigate a project called Pipelight, to do exactly what you are suggesting, except without using Windows Firefox.  [http://pipelight.net/cms/installation.html](http://pipelight.net/cms/installation.html)

In this day and age, I would suggest that if you want modern browsing capabilities that you use Chrome for Linux instead.  Firefox for Linux does not support EME for video streaming properly, and Mozilla has been dragging its feet on decent EME for over a year.    Chrome for Linux does support EME and should provide you with almost everything you need in an out-of-the-box fashion.

---

