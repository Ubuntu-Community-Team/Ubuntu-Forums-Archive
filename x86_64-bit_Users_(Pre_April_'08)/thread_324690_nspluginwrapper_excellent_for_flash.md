---
title: "nspluginwrapper excellent for flash"
date: 2006-12-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by rajeev1204 on 2006-12-24
hi

nspluginwrapper works beautifully with flash 7 so u can watch ur favourite youtube clips


Here is the link for step by step install for our systems

[http://plugindoc.mozdev.org/linux-amd64.html](http://plugindoc.mozdev.org/linux-amd64.html)

follow it completely and u r good to go!

important is to download both player and viewer ,also remember to use /usr/lib/mozilla-firefox/plugins as the path cos that is where our 64 bit firefox is located.

you will need the alien package to convert the rpm to debs .but that is available in repos. So for all those who had issues installing in the past with imcomplete instructions ( me included), this link will solve it.


regards


rajeev

---

### Post by xopher on 2006-12-24
I've even made debs for you folks who are too lazy to alienate the rpms, check this thread out, installation instructions in the first post:

**[http://ubuntuforums.org/showpost.php?p=1615252&postcount=1](http://ubuntuforums.org/showpost.php?p=1615252&postcount=1)**

And the packages in my last post:

**[http://ubuntuforums.org/showpost.php?p=1919913&postcount=29](http://ubuntuforums.org/showpost.php?p=1919913&postcount=29)**

Have fun! And Merry Christmas!

---

### Post by Pawel Stolowski on 2006-12-24
Yeah, it works for me with flash9.

---

### Post by rajeev1204 on 2006-12-25
hi

flash 9 also works? isnt that beta?

anyways , is flash 9 working ok? maybe i will try that



regards

rajeev

---

### Post by rajeev1204 on 2007-04-03
Hi

a small update .

All those getting the error  ... this is not a valid NPAPI plugin 

perform the final step of install with sudo 

sudo nspluginwrapper -i  /usr/lib/firefox/plugins/libflashplayer.so

Basically run all steps as sudo 


regards

rajeev


P.S works in feisty too !:)

---

### Post by Kilz on 2007-04-03
The only problem I can see with nspluginwrapper is the lack of support for the java plugin. I wonder if thats the only other plugin it doesnt support.

---

### Post by jamesford on 2007-04-03
this has matured a bit hasnt it? i remebmer trying it before xmas some time and it didnt perform too well, but seems pretty good now.
anyone got debs for the very latest version (0.9.91.4.)?

---

### Post by rajeev1204 on 2007-04-04
> **Kilz said:**
> The only problem I can see with nspluginwrapper is the lack of support for the java plugin. I wonder if thats the only other plugin it doesnt support.

hi
i have a question . I dont have any java plugins installed but i dont recall any websites asking for the plugin . When is the plugin needed? 

Iam a little confused . We have j2re blackdown in synaptic . Do i need that?


regards
rajeev

---

### Post by Kilz on 2007-04-04
> **rajeev1204 said:**
> hi
i have a question . I dont have any java plugins installed but i dont recall any websites asking for the plugin . When is the plugin needed? 

Iam a little confused . We have j2re blackdown in synaptic . Do i need that?


regards
rajeev

The plugin is needed whenever there is a java applet on a webpage. A google search for java applets or java games should bring up quite a few sites. There is no 64bit java plugin in the repo's. Well there is an old Blackdown one on the net but it causes Firefox to crash.  I cant even open a page with an applet on without Firefox crashing. But there is some good news for the future, now that java is gpl some people have started work on a 64bit plugin, but its only in the planning stages.

---

### Post by rajeev1204 on 2007-04-04
oh ok  so thats why my firefox used to crash all the time 

I had that installed in my dapper . I think that plugin crashed the browser even otherwise. 

This time iam on feisty and not installed the plugin . Firefox is much better this way.

---

### Post by Kilz on 2007-04-04
> **rajeev1204 said:**
> oh ok  so thats why my firefox used to crash all the time 

I had that installed in my dapper . I think that plugin crashed the browser even otherwise. 

This time iam on feisty and not installed the plugin . Firefox is much better this way.

:)  Except if you go to sites with java applets.

---

