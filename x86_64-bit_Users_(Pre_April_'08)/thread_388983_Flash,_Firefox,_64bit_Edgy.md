---
title: "Flash, Firefox, 64bit Edgy"
date: 2007-03-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Xetroc on 2007-03-20
Hey,

When i'm entering a site with flash firefox locks and i can't do anything except force quit.

Does anyone know a solution to this ?

---

### Post by Kilz on 2007-03-20
> **Xetroc said:**
> Hey,

When i'm entering a site with flash firefox locks and i can't do anything except force quit.

Does anyone know a solution to this ?

How did you install Flash, With nspluginwrapper , or with 32bit firefox?

---

### Post by Xetroc on 2007-03-22
nspluginwrapper, haven't installed 32bit firefox, using 64bit

---

### Post by mouseboyx on 2007-03-22
Flash is not compatible with 64 bit I've tried it myself, sorry but if you want flash you have to run 32 bit or find some crazy thing that will let you run a 32bit add on within  64 bit Firefox.

[http://www.adobe.com/cfusion/knowledgebase/index.cfm?id=6b3af6c9](http://www.adobe.com/cfusion/knowledgebase/index.cfm?id=6b3af6c9)

[http://ask.slashdot.org/article.pl?sid=05/10/19/1959200](http://ask.slashdot.org/article.pl?sid=05/10/19/1959200)

---

### Post by Lonthong on 2007-03-22
> **mouseboyx said:**
> Flash is not compatible with 64 bit I've tried it myself, sorry but if you want flash you have to run 32 bit or find some crazy thing that will let you run a 32bit add on within  64 bit Firefox.

[http://www.adobe.com/cfusion/knowledgebase/index.cfm?id=6b3af6c9](http://www.adobe.com/cfusion/knowledgebase/index.cfm?id=6b3af6c9)

[http://ask.slashdot.org/article.pl?sid=05/10/19/1959200](http://ask.slashdot.org/article.pl?sid=05/10/19/1959200)

I installed flash with nspluginwrapper & it works perfectly

---

### Post by Kilz on 2007-03-22
> **Xetroc said:**
> nspluginwrapper, haven't installed 32bit firefox, using 64bit

nspluginwrapper is [beta software]("http://gwenole.beauchesne.info/projects/nspluginwrapper/"). It isnt perfect, its said to work reasonably well. It may crash the browser or lock it up on some sites.  
If you are unable to solve this issue, you may want to install the 32bit browser. The link in my signature is a good place to look. I have a script that will install everything in a few minutes.

---

### Post by rajeev1204 on 2007-03-22
I dont know why it is called beta still . nspluginwrapper works great for me .

I wasnt very comfortable with the idea of having 2 browsers in my system.

So even though i have once tried ur  script when i was new to ubuntu, i uninstalled it .


iam very satisfied with nspluginwrapper. Right now iam trying to use ur howto on installing wine on my amd 64 . Will ask if i have trouble . 



regards

rajeev

P.S . i want to  know how to write scripts .u can point me to some study links? Maybe in future i too can contri like u guys r doing .keep it up.

---

### Post by Kilz on 2007-03-22
> **rajeev1204 said:**
> I dont know why it is called beta still . nspluginwrapper works great for me .

I wasnt very comfortable with the idea of having 2 browsers in my system.

So even though i have once tried ur  script when i was new to ubuntu, i uninstalled it .


iam very satisfied with nspluginwrapper. Right now iam trying to use ur howto on installing wine on my amd 64 . Will ask if i have trouble . 



regards

rajeev

P.S . i want to  know how to write scripts .u can point me to some study links? Maybe in future i too can contri like u guys r doing .keep it up.

As long as it works for you, thats all that matters. You may not be going to sites that cause problems. Another reason for installing the 32bit version is java support. Nsplugiwrapper does not support the java plugin.
As for scripting, I didnt really go to any one site to learn it. I just looked at some scripts and saw that what they are doing are commands you would enter into a terminal. If there was a command I couldnt figure out , I just googled it and read whatever came up.

---

### Post by John.Michael.Kane on 2007-03-22
> **rajeev1204 said:**
> I dont know why it is called beta still . nspluginwrapper works great for me .

I wasnt very comfortable with the idea of having 2 browsers in my system.

So even though i have once tried ur  script when i was new to ubuntu, i uninstalled it .


iam very satisfied with nspluginwrapper. Right now iam trying to use ur howto on installing wine on my amd 64 . Will ask if i have trouble . 



regards

rajeev

P.S . i want to  know how to write scripts .u can point me to some study links? Maybe in future i too can contri like u guys r doing .keep it up.



This should get you started.

[**BASH Programming - Introduction HOW-TO**]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html")

[**Advanced Bash-Scripting Guide**]("http://tldp.org/LDP/abs/html/")

[**A quick guide to writing scripts using the bash shell**]("http://pegasus.rutgers.edu/~elflord/unix/bash-tute.html")

---

### Post by acp on 2007-03-22
Hi I use nspluginwrapper to install flashplayer on my amd64 during installation it works fine, but when i close firefox and open it again flashplayer wont work especially in youtube. I need to run nspluginwrapper -i for it to work again. would you know a fix? 

Thanks in advance
acp

---

### Post by rajeev1204 on 2007-03-22
k

---

### Post by lan56 on 2007-03-22
Or, you can always use Gnash, the GNU's answer to proprietary Flash. I haven't used it yet, or know if it supports 64 bit, but I feel I had to say something about it since I rarely hear anyone mention it.

---

### Post by John Jason Jordan on 2007-03-22
> **acp said:**
> Hi I use nspluginwrapper to install flashplayer on my amd64 during installation it works fine, but when i close firefox and open it again flashplayer wont work especially in youtube. I need to run nspluginwrapper -i for it to work again. would you know a fix? acp
The problem is that you need to run:

nspluginwrapper -v -a -i

From a command line every time you launch Firefox. This is annoying, so I made a fix for that. Here is what you do:

1) Open Gedit and paste the following into it:

#!/bin/bash
nspluginwrapper -v -a -i
firefox

Save the document in your home folde as firefox_launch_script. Then open Nautilus and select the file. In the Properties menu select the Permissions tab and check the Execute box.

Next, open Alacarte and browse to the launch menu item for Firefox. (Or right click on the icon if your launch item is in the panel.) Select Properties and in the Command box enter:

~/firefox_start_script

Close Alacarte or the Properties window. Now, whenever you click to launch Firefox it will run your script. The script will run the -v-a-i command and then launch Firefox.

It's kind of clunky, but at least it automates running the -v-a-i command every time you launch Firefox.

---

### Post by Lonthong on 2007-03-28
> **John Jason Jordan said:**
> The problem is that you need to run:

nspluginwrapper -v -a -i

From a command line every time you launch Firefox. This is annoying, so I made a fix for that. Here is what you do:

1) Open Gedit and paste the following into it:

#!/bin/bash
nspluginwrapper -v -a -i
firefox

Save the document in your home folde as firefox_launch_script. Then open Nautilus and select the file. In the Properties menu select the Permissions tab and check the Execute box.

Next, open Alacarte and browse to the launch menu item for Firefox. (Or right click on the icon if your launch item is in the panel.) Select Properties and in the Command box enter:

~/firefox_start_script

Close Alacarte or the Properties window. Now, whenever you click to launch Firefox it will run your script. The script will run the -v-a-i command and then launch Firefox.

It's kind of clunky, but at least it automates running the -v-a-i command every time you launch Firefox.

I just followed one of the how-to's here in this very forum (that I already forgot which one). I did not have that firefox_start_script & so far no problem with youtube.

---

### Post by wesley_of_course on 2007-03-28
> **SD-Plissken said:**
> This should get you started.

[**BASH Programming - Introduction HOW-TO**]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html")

[**Advanced Bash-Scripting Guide**]("http://tldp.org/LDP/abs/html/")

[**A quick guide to writing scripts using the bash shell**]("http://pegasus.rutgers.edu/~elflord/unix/bash-tute.html")

  Wesley here ; 

  Thank You , no misdirection intended . For the links.

---

