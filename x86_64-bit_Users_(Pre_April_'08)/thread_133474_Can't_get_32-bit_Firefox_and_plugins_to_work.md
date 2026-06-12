---
title: "Can't get 32-bit Firefox and plugins to work"
date: 2006-02-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Daggett on 2006-02-20
I am having problems getting 32-bit FIrefox to work with Kubuntu AMD64.  I am attempting this with Firefox-1.5.0.1, but 1.5 gives me the same problems.  I tried using the steps outlined for getting 32-bit Firefox to work in Ubuntu, but that procedure does NOT work for me.  If I change some things, I can get the browser to run, but neither flash nor java work at all. I simply get the "missing plugin" boxes on the web pages.

The difference between what I do and the Ubuntu instructions is that I can only get the browser to launch if I change to the browser directory.  

export GTK_PATH=/usr/lib32/gtk-2.0
LD_PRELOAD=/usr/lib32/libpangohack.so.0
cd /usr/local/firefox32
linux32 firefox $@

If I try to run it from outside the directory (as per the instructions for the shell file for Ubuntu), I get this message:

/usr/local/firefox32/run-mozilla.sh: line 166: /usr/local/firefox32/firefox-bin: cannot execute binary file

Has anyone gotten 32-bit Firefox 1.5+ & plugins to work on Kubuntu AMD 64?  If so, can you explain how you did it?

---

### Post by paul.o on 2006-02-21
try this link :-

[https://wiki.ubuntu.com/FirefoxAMD64FlashJava](https://wiki.ubuntu.com/FirefoxAMD64FlashJava)

---

### Post by Daggett on 2006-02-22
When I said "I tried using the steps outlined for getting 32-bit Firefox to work in Ubuntu, but that procedure does NOT work for me."  I was referring to that link!  I tried those steps, but they don't work for me.  I tried the PANGO_RC method, the LD_PRELOAD method, and the result is always the same:

/usr/local/firefox32/run-mozilla.sh: line 166: /usr/local/firefox32/firefox-bin: cannot execute binary file

I have all the proper 32-bit libraries and linux32 installed, so that isn't the problem.

---

### Post by tokyovigilante on 2006-02-24
I've never had problems using that HOWTO on my AMD64 install. 

Your problem may be that running Firefox as a standard user from a system directory where it has no write privileges may cause it some issues (ie installing plugins etc). Try shifting it to your home directory and running it from there.

---

