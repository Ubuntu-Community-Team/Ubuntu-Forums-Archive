---
title: "printer GONE!, cups cant be started.. karmic"
date: 2009-10-30
forum: x86 64-bit Users
---

### Post by binskipy2u on 2009-10-30
I've NEVER had this happen in intrepid, jaunty..
I have a pixma 210, previously ive force installed the 32bit drivers.. everything always worked.. now i did that, it seen it ONCE.. printed something..rebooted, GONE.. turn it on nothing, click on default printer "cups service is not running", click on admin > printing> new> its' grayed out.. , tried connecting to server, i get this message > There was an error during the CUPS operation: 'httpConnectionEncrypt failed'
what gives.. ????????????????????
ive googled, ive read bug reports, ive read what EVERYONE has typed, i tried restarting cupsys, ('no command found") i tried uninstalling and reinstalling everythign with cupsys in it, I've done everything in all the posts ive read.. NOTHING it no longer sees the printer, I know it works..
its almost new 
so anyone have an answer??????????????????? I don't have to have to go to windows just to print a picture.. 
anyone??????????

---

### Post by Dark_Stang on 2009-10-30
Did you do an upgrade or a clean install?

---

### Post by binskipy2u on 2009-10-30
clean install

---

### Post by Dark_Stang on 2009-10-30
Make sure you have the 'cups' and 'cups-driver-gutenprint' packages installed.

---

### Post by binskipy2u on 2009-10-30
that seemed to have helped... but the printer icon wont show up, its enabled in "startup programs", but i can configure and the printer shows up when i click on print.. etc..

hope it don't dissapear again like it already did

---

### Post by binskipy2u on 2009-10-31
it shows up, it dissapears, i reinstall cups, it shows up, i reboot it dissapears???
someone help, this is driving me crazy.. i had less headaches with that OTHER os, when it comes to printers..
ok, everytime i dont see it i reinstall cups.. so that means anytime i want to use my printer i have to reinstall cups?
this is annoying

---

### Post by Dark_Stang on 2009-10-31
Are you adding the printer manually or just letting ubuntu detect it?

---

### Post by binskipy2u on 2009-10-31
turning it on...and 1 time the p;rinter applet came up.. configured it, then dissapeared. and then when i turn it on, i have to check printer config, sometimes it's there, sometimes it's not.. reinstalling cups, and turning on the printer works..
again, just darn annoying as heck

---

### Post by Dark_Stang on 2009-10-31
So go System > Administration > Printing. And add it from there and set it as the default printer. What happens then?

---

### Post by binskipy2u on 2009-10-31
it's there, even though the printer is turned off.. hopefully it stays that way, have no clue why it dissapeared, reappeared, and had to reinstall cups 2x

---

### Post by binskipy2u on 2009-11-06
printer dissapears again and again and again.. and yet again..
how the heck do you KEEP IT?????
anyone???

---

### Post by gmos on 2009-11-06
Same problem here.   Karmic 64bit and using a Samsung Scx-4100 printer/scanner.  Have to reinstall cups whenever I need to print.    Set it as default, but it keeps disappearing after a reboot.

---

### Post by binskipy2u on 2009-11-06
any ideas at all?
wish someone did, this is friggin annoying..

---

### Post by Malta paul on 2009-11-07
I still have a problem Huston!

I lost my printer (a Cannon PIXMA ip1800) when I did a clean installation of 9.10, fortunately it was installed in a separate partition to 9.04 where the printer works normal!
I tried reinstalling the drivers and the printer is recognized but when trying to print, an icon pops up on the task bar then disappears with no printer response.

I then tried an upgrade of my 9.10 system - still no printer, next I tried a clean update using a 32bit disk instead of the previous 64 bit disk - still no printer.
So I reinstall the 9.04 (64 bit) Jaunty again and the printer works great again!!
9.10 dose work normal on my other partition but less printer installation. I'm not sure, but it looks like the 9.10 Cups is different from the 9.04 version. ?

---

### Post by astrodillo on 2009-11-14
Same problem here.When i try to configure a new printer, y click on connect to server "localhost" and iget this message "«httpConnectionEncrypt failed»."

In a terminal i write "/etc/init.d/cups start" and i get 
"cupsd: Child exited on signal 15!"

My printer is a canon pixma mp160 and i never had this problem in others ubuntu distros.

Any idea??

---

### Post by tiberius_k on 2009-11-14
Hello,

Same deal here. I have a HP PSC 1200 All-in-One. 

Cheers,

Kirk

---

### Post by darco on 2009-11-14
I too had this problem when I did a clean install of KK Beta for my HP Printer...I remember reinstalling everything hp/cups related and having to run cups manually after each reboot but it somehow worked itself out after a few KK updates. Below is a link to the bug I was following at the time..


[https://bugs.launchpad.net/ubuntu/+bug/444597](https://bugs.launchpad.net/ubuntu/+bug/444597)


darco

---

