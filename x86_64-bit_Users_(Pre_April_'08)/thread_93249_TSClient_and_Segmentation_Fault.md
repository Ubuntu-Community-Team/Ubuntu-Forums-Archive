---
title: "TSClient and Segmentation Fault"
date: 2005-11-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by tmeier on 2005-11-21
I am running Breezy on a Tibook 1Ghz and 1Gb Ram.  have Breezy installed on a partition and everything works great, but one thing.  When I go to use Terminal Server Client it put in all the required information it just stops.  I thought I would try from the terminal to start the application and it starts just fine, but when I click on connect, I get a Segementation fault.  Not sure what is actually going on.  My computer is on my local network and both computers are on the same subnet.  I would like to be able to manage my 2003 servers from my laptop and really enjoy Breezy.  Any help is appreciated.

---

### Post by gapplewagen on 2005-11-23
tsclient is just a gnome frontend for "rdesktop".  Try running rdesktop in a terminal to connect to your remote system just to see which program is causing the problem.  

```
$ rdesktop -u USERNAME -g 1024x768 remote.box.org
```

Does it connect or segfault?

---

### Post by paulscheremet on 2005-12-22
rdesktop runs smoothly, but I've got the same problem with tsclient as tmeier. 

I straced tsclient, but there's no clue where it tries to use the invalid address.

```
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++

```

Any help is appreciated ,
Paul

---

