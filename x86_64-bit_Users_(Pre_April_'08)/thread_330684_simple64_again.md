---
title: "simple64 again"
date: 2007-01-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by kuja on 2007-01-03
A while ago I'd worked on it, a neat little python script for installing a handful of apps (Mainly everything mentioned in the sticky thread). I eventually got frustrated with it and didn't know what to do with it. Last night I dusted it off and made it usable again, I think. The changes are countless. Take a look if interested, else, let me know, and it can go back on the shelf :rolleyes: 

I can't promise I've worked out all the kinks, seeing as I made a lot of changes, but, give it a whirl, I can at least guarantee the parts I tried work ...

Want it? Follow the instructions on [this page](http://www.xnowherex.net/simple64/) and it will be yours!
To run it: Select Simple64 from the menu, or type simple64 in a shell.

What to do if something goes wrong: Reply telling what you did, how it didn't work, and attach the file /var/log/simple64.log if applicable/necessary.

Suggestions & Feedback welcome.

---

### Post by pross on 2007-01-03
update broken?
```

###        Starting Simple64 Update Process         ###
Checking For Simple64 Updates...
downloading http://www.xnowherex.net/ubuntu/simple64.conf
server: simpleVersion 0.8.99
server: simpleDataVersion 0.4.0
Traceback (most recent call last):
  File "./simple64.py", line 1282, in ?
    MainLoop()
  File "./simple64.py", line 87, in MainLoop
    handleSelection(selection)
  File "./simple64.py", line 134, in handleSelection
    updateSimple64()
  File "./simple64.py", line 221, in updateSimple64
    upToDate = checkVersion("simpleVersion",serverVersion)
  File "./simple64.py", line 248, in checkVersion
    version = simpleConfig[short]
NameError: global name 'simpleConfig' is not defined

```

---

### Post by kuja on 2007-01-03
eh heh, I broke a lot of things. A clean install should fix things. (looks like you're using an older version no?) Anyhow, I'll have that fixed before long. I was more concerned with the rest of it really. Anyway, I'll be sure to overhual the simple64update code for 0.9.1.

---

### Post by pross on 2007-01-03
i used the version you posted above..

---

### Post by kuja on 2007-01-03
really? That's odd .... I'll look into that too then.

---

### Post by apapww on 2007-01-03
Thanks ever so much[.](http://hk.yahoo.com)[.](http://www.ec2biz.com)[.](http://www.rthk.org.hk)[.](http://www.ads28.com)[.](http://www.ec2biz.com)[.](http://www.top1.com.hk)[.](http://www.ads28.com)

---

### Post by kuja on 2007-01-03
Alrighty Pross, 0.9.1 is up, and I've think I've got the Self Updating thing fixed, I completely rewrote that part ... I'll test it in a few minutes I suppose.

---

### Post by pross on 2007-01-03
nice one..i used it to install rar :)

---

### Post by kuja on 2007-01-04
Okay, 0.9.2 is up, along with data 6. I've  updated the wine link, fixed & improved the wine installation procedure, changed some text related things, and changed aptitudes behaviour, though the logs it emits are inferior now, at least it shows the progress, right? ;)

---

### Post by kuja on 2007-01-09
simple64 0.9.3 is up, along with data 7 ... the update feature won't work for updating simple64 this trip around because I moved where I keep it on the server (for sensibility reasons). There are a slew of problems fixed and it should prove to be significantly more usable now, I think.

---

### Post by kuja on 2007-01-09
If anyone cares, I've got simple64 0.9.5 up, with several more fixes.

---

### Post by noenter1 on 2007-01-10
Cant open it thru the system menu, but i can open it thru the shell. Other than that working great so far. :D

---

### Post by schumifer on 2007-01-22
Apart from firefox everything else installed like a charm. Dude you rock

---

### Post by kuja on 2007-01-22
schumifer, apart from firefox? Something went wrong? Do tell.

---

### Post by t_anjan on 2007-01-23
> **noenter1 said:**
> Cant open it thru the system menu, but i can open it thru the shell. Other than that working great so far. :D

Same here, opening thru the menu does not work. But, other than that, the program is amazing. Dunno why more people don't use it.

---

### Post by t_anjan on 2007-01-23
I installed WINE using Simple64. It works perfectly, but now I'd like to know how to uninstall any program that was installed using simple64. The program doesn't show in Synaptic.

---

### Post by geekphreak on 2007-03-02
Run simple64, enter 17 and then the number of the application you wish to uninstall.

---

### Post by schumifer on 2007-03-29
Sorry for the much delayed answer. The first time i used simple 64 the firefox debs woulkdn't download. After that a couple of times that i tried it it seemed perfectly allright

---

### Post by jimbobjones on 2007-03-29
how do you use this ?

i've installed it ok but its not in the menus anywhere ?

---

### Post by StandardBlueCaboose on 2007-03-29
> **jimbobjones said:**
> how do you use this ?

i've installed it ok but its not in the menus anywhere ?

> **kuja said:**
> 
To run it: Select Simple64 from the menu, or type simple64 in a shell.


That should work. If it doesn't, I can't help you. Seeing as you only have 2 beans, I thought I would point out what Kuja said in his original post.

---

### Post by Cederien on 2007-03-31
I've run into a similar problem, a closer look showed that simply copying and pasting all the lines into the console at once didn't do the trick. The line after the python install was not executed.
Simply try to paste and execute that last line again. I had to reget the files first for some reason (and with sudo as it would not allow me to write them otherwise), so you might have to do that as well.

---

### Post by UltimaDude on 2007-03-31
Any chance of supporting Nvu?
Oh and I love the program, I can finally use Wine!

Edit: I can't find WINE after I installed it :(

---

### Post by Cederien on 2007-03-31
That's normal, wine does not add itself to any application menu AFAIK.
Just type 'wine <application>' in the console to run a windows exe or type 'winecfg' to set up your preferences.
Of course you can add Wine to the menus manually if you like.

---

### Post by jimbobjones on 2007-03-31
found it in the admin menu


great app nice work. does the flash player work ok in 64bit firefox?

how do you uninstall the apps if required ?

---

### Post by kuja on 2007-03-31
> **jimbobjones said:**
> found it in the admin menu


great app nice work. does the flash player work ok in 64bit firefox?

how do you uninstall the apps if required ?

Well, if you want it to work in 64-bit firefox, you'll have to run it thru a wrapper called nspluginwrapper. Check the first and second pages of the 64-bit forum, I'm pretty sure the thread has been talked in recently.

---

### Post by tjotser on 2007-04-02
wget [http://www.xnowherex.net/simple64/simple64_0.90_amd64.deb](http://www.xnowherex.net/simple64/simple64_0.90_amd64.deb)
--23:19:22--  [http://www.xnowherex.net/simple64/simple64_0.90_amd64.deb](http://www.xnowherex.net/simple64/simple64_0.90_amd64.deb)
           => `simple64_0.90_amd64.deb'
Resolving [www.xnowherex.net](www.xnowherex.net)... 70.86.137.98
Connecting to www.xnowherex.net|70.86.137.98|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
23:19:22 ERROR 404: Not Found.

I posted this in the other "old" thread also (by accident). 
Please make it available so i can test this again.. Thank you
:KS

---

