---
title: "firefox not starting"
date: 2006-02-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by mikenam on 2006-02-02
brand new install of ubuntu 5.10 for my dual core amd64.  at the beginning everything was working even mozilla firefox.  after searching the web and leaving it on for a couple hours firefox suddenly stops working. i close firefox to try and reopen it but it just says "starting firefox webbrowser" for like 1min.  then then closes.  firefox doesn't start up at all.  

when i click on system/about ubuntu i get the error message "The Application "yelp" has quit unexpectedly."  same thing happens when i click on "get help with gnome" icon.

i don't know what to do.  i tried a fresh new install but that i still get the same problems.  could some one please help.  first time using linux.

thank you

---

### Post by wjp.reg on 2006-02-02
Have you tried running firefox from console and passing -profilemanager parameter to setup a new profile?

This has worked for me in the past when having trouble loading

---

### Post by mikenam on 2006-02-02
thx for the reply.

im new at linux.  first time ever using it.  don't even know how to run firefox from command.  don't even know where command prompt is.  

thanks again

---

### Post by rplantz on 2006-02-02
[QUOTE=mikenam]thx for the reply.

im new at linux.  first time ever using it.  don't even know how to run firefox from command.  don't even know where command prompt is.  

thanks again[/QUOTE]

Assuming that you're running Gnome (the default), you need to open a terminal window. You can probably find it at Applications->Accessories->Terminal.

When I've been messing around with my system, installing Firefox 1.5, etc., I've "broken" the default Firefox (1.07) installation, giving the same symptoms you describe.

I've discovered that removing the file compreg.dat has restored functionality to Firefox. Here are the steps to take:
1. Open a terminal window (as described above).
2. ```

cd .mozilla/firefox
ls -l

```
3. You should see a listing that includes a directory that ends in .default. For example, mine is xfi6xbsb.default. The silly mix of characters changes every time I mess around with Firefox. For the next step, I will call this xxxxx.default.
4. ```

cd xxxxx.default
mv compreg.dat ../../../
ls -l
cd
ls -l

```
At this point you should see that the file compreg.dat has been moved form the xxxxx.default directory into your home directory.
5. To start Firefox from the command line, just type "firefox" (without the quotes) in a terminal window.

---

