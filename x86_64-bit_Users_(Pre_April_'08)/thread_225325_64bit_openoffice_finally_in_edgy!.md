---
title: "64bit openoffice finally in edgy!"
date: 2006-07-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by JoWilly on 2006-07-29
Finally !

The openoffice.org-experimental packages that have now arrived in the edgy repos are the 64bit version.

> soffice.bin: ELF 64-bit LSB executable, AMD x86-64, version 1 (SYSV), for GNU/Linux 2.6.0, dynamically linked (uses shared libs), for GNU/Linux 2.6.0, stripped


The standart openoffice.org packages are still the 32bit version.

---

### Post by Kilz on 2006-07-29
> **JoWilly said:**
> Finally !

The openoffice.org-experimental packages that have now arrived in the edgy repos are the 64bit version.



The standart openoffice.org packages are still the 32bit version.

Sounds great. :D  One more piece of the 64bit puzzle. Its nice to see more 64bit applications.

---

### Post by tomdkat on 2006-10-25
Great!  Will Edgy have a 64-bit version of OpenOffice 2.0.4, which is now out?

Thanks!

Peace...

---

### Post by tomdkat on 2006-11-03
> **tomdkat said:**
> Great!  Will Edgy have a 64-bit version of OpenOffice 2.0.4, which is now out?
The answer is **YES**!  :D

Peace...

---

### Post by alphomega on 2006-11-03
soon help remove more of those nasty antique ix86 binaries from my drive!!

---

### Post by mojoman on 2006-11-03
> **JoWilly said:**
> Finally !

The openoffice.org-experimental packages that have now arrived in the edgy repos are the 64bit version.



The standart openoffice.org packages are still the 32bit version.

Does this mean that the 64-bit version is more limited in scope or does it simply use 32-bit packages whenever the 64-bit package is missing? (i.e. can I do fewer things with the 64-bit OpenOffice?)

I'm still on Dapper but I'm thinking about switching to Edgy...

/Mojoman

---

### Post by Kilz on 2006-11-03
> **mojoman said:**
> Does this mean that the 64-bit version is more limited in scope or does it simply use 32-bit packages whenever the 64-bit package is missing? (i.e. can I do fewer things with the 64-bit OpenOffice?)

I'm still on Dapper but I'm thinking about switching to Edgy...

/Mojoman

Dapper has a 32bit Open office Edgy has a 64bit Open office. They both do the same things. The only difference is that in Edgy there are fewer ia32 packages installed making it harder to install 32bit applications. In this respect it was a bad thing. Sadly the developers thought this was a good thing in a discussion I had with them on the email lists last month. I believe this is affecting the installing of 32bit mplayer.

---

### Post by mojoman on 2006-11-03
> **Kilz said:**
> Dapper has a 32bit Open office Edgy has a 64bit Open office. They both do the same things. The only difference is that in Edgy there are fewer ia32 packages installed making it harder to install 32bit applications. In this respect it was a bad thing. Sadly the developers thought this was a good thing in a discussion I had with them on the email lists last month. I believe this is affecting the installing of 32bit mplayer.

So there is no difference in functionality between 32-bit Open Office and 64-bit Open Office? If so, that's a good thing. I read parts of the discussion with the developers and I can't say I understand their view on giving 32-bit priority and it made me worried that the 64-bit applications would be less updated and less maintained (considering that 32-bit system probably won't be used within not too many years I can't imagine why they take this stand either).

---

### Post by tomdkat on 2006-11-03
> **Kilz said:**
> The only difference is that in Edgy there are fewer ia32 packages installed making it harder to install 32bit applications. In this respect it was a bad thing. Sadly the developers thought this was a good thing in a discussion I had with them on the email lists last month. I believe this is affecting the installing of 32bit mplayer.I can see where the developers are coming from and I tend to lean more toward their side on this.  I fully understand the current need to maintain adequate 32-bit compatibility for some apps (like Flash, wine, Opera, what-eh-vah) but the longer people are comfortable running 32-bit apps on 64-bit hardware the less important it will be to get 64-bit native versions of those apps.

We just need to make more noise about demanding better 64-bit support from third party vendors in general.

Peace...

---

### Post by fabertawe on 2006-11-04
> **tomdkat said:**
> I can see where the developers are coming from and I tend to lean more toward their side on this.  I fully understand the current need to maintain adequate 32-bit compatibility for some apps (like Flash, wine, Opera, what-eh-vah) but the longer people are comfortable running 32-bit apps on 64-bit hardware the less important it will be to get 64-bit native versions of those apps.

We just need to make more noise about demanding better 64-bit support from third party vendors in general.

Peace...

Unfotunately this will probably not happen until Microsoft decide that 64bit is the norm. Then Ubuntu will be playing catch up.

Paul

---

### Post by Kilz on 2006-11-04
> **tomdkat said:**
> I can see where the developers are coming from and I tend to lean more toward their side on this.  I fully understand the current need to maintain adequate 32-bit compatibility for some apps (like Flash, wine, Opera, what-eh-vah) but the longer people are comfortable running 32-bit apps on 64-bit hardware the less important it will be to get 64-bit native versions of those apps.

We just need to make more noise about demanding better 64-bit support from third party vendors in general.

Peace...

While it would be nice, making proprietary companies like Adobe release 64bit versions is hard. Thats why some distro's like SuSE(who reciently made a deal with the devil), Fedora, and Gentoo are already multiarch. That the Office application is 64bit isnt the problem, removing the libraries is. Removing small library files and making it harder to install 32bit applications that are needed now is not the way to go imho. With the every 6 months release schedule those small files could easily been removed in a future version when they were no longer needed.
Im probably not going to upgrade to Edgy, if I do it will be much later. I see no need to go through the headache of making things work that already work for me now. I think the Developers could care less about the 64bit uses, they threw a wrench in the works. But I bet that little bit of eye candy makes all the trouble worth it, right?

---

### Post by tomdkat on 2006-11-08
> **Kilz said:**
> While it would be nice, making proprietary companies like Adobe release 64bit versions is hard. Thats why some distro's like SuSE(who reciently made a deal with the devil), Fedora, and Gentoo are already multiarch. That the Office application is 64bit isnt the problem, removing the libraries is. Removing small library files and making it harder to install 32bit applications that are needed now is not the way to go imho. With the every 6 months release schedule those small files could easily been removed in a future version when they were no longer needed.
Im probably not going to upgrade to Edgy, if I do it will be much later. I see no need to go through the headache of making things work that already work for me now. I think the Developers could care less about the 64bit uses, they threw a wrench in the works. But I bet that little bit of eye candy makes all the trouble worth it, right?I hear what you're saying but 6 months from now someone would want the 32-bit libs to be removed 6 months from then and the cycle would continue.

However, I *just* came across this GREAT news that might make 64-bit native Flash a reality:

[Adobe and Mozilla Foundation to Open Source Flash Player Scripting Engine](http://www.mozilla.com/en-US/press/mozilla-2006-11-07.html)

If this actually results in an open source Flash scripting engine, that could mean open source Flash players that could be bundled with Ubuntu or made available through unofficial repositories which could then mean the 64-bit Flash issue could possibly be put to rest.  Of course, that doesn't address the need for Flash on 64-bit Linux today but I think this is a step in the right direction.  

The longer 64-bit users rely on 32-bit apps and are ok with it, the longer it will take to get 64-bit native versions of those apps.

Peace...

---

### Post by John Jason Jordan on 2006-11-08
> **tomdkat said:**
> I hear what you're saying but 6 months from now someone would want the 32-bit libs to be removed 6 months from then and the cycle would continue.

The longer 64-bit users rely on 32-bit apps and are ok with it, the longer it will take to get 64-bit native versions of those apps.
That's all well and good, but some of us need functionality right away. There is a bug in OOo 2.03 in the PDF export and the only workaround is Adobe Acrobat Professional 7.0 at $160 student rate, plus I'll have to install Windows to run it. It might be fixed in OOo 2.04, but I can't install 2.04 in Dapper, and I can't install Edgy until after the first week of December (finals week). So everyone can debate whether limiting 32-bit libraries is a good idea or a bad idea, but I just want something that works now. If I had installed 32-bit Dapper I could install OOo 2.04 right now and I might have a solution today. When I do install Edgy I'll think twice before installing the 64-bit version.

---

### Post by Kilz on 2006-11-08
> **John Jason Jordan said:**
> That's all well and good, but some of us need functionality right away. There is a bug in OOo 2.03 in the PDF export and the only workaround is Adobe Acrobat Professional 7.0 at $160 student rate, plus I'll have to install Windows to run it. It might be fixed in OOo 2.04, but I can't install 2.04 in Dapper, and I can't install Edgy until after the first week of December (finals week). So everyone can debate whether limiting 32-bit libraries is a good idea or a bad idea, but I just want something that works now. If I had installed 32-bit Dapper I could install OOo 2.04 right now and I might have a solution today. When I do install Edgy I'll think twice before installing the 64-bit version.

If you have a 32bit deb of 2.04 it should work to install to dapper. Where did you get it? All I was able to find was rpm's on the oppen office site, there are also 28 of them to install.

---

### Post by John Jason Jordan on 2006-11-08
> **Kilz said:**
> If you have a 32bit deb of 2.04 it should work to install to dapper. Where did you get it? All I was able to find was rpm's on the openoffice site, there are also 28 of them to install.
Sorry, I must have read the OOo site too quickly. You're right, there's no .deb there at all; just RPMs. Someone might have created one, however. I don't normally participate in the 32-bit Ubuntu forums, so I haven't seen any chatter about 2.04.

---

### Post by Kilz on 2006-11-08
I have another question. I just looked at my Open Office since I have dapper. Its version 2.02, it exports a pdf. How did you get 2.03 installed? What problem are you experencing with this bug?

---

### Post by kuja on 2006-11-08
hmm, maybe it's in the backports or updates repository?

---

### Post by IanW on 2006-11-08
You can install RPMs in Ubuntu by first installing "alien", a package converter in Synaptic.

---

### Post by John Jason Jordan on 2006-11-08
> **Kilz said:**
> I have another question. I just looked at my Open Office since I have dapper. Its version 2.02, it exports a pdf. How did you get 2.03 installed? What problem are you experencing with this bug?
Sorry! Yet another dumbass move. Turns out I have 2.02 also.

Regarding the "bug," evidently it is not a bug. It is by design not to embed fonts for controls in a form document:

[http://qa.openoffice.org/issues/show_bug.cgi?id=42985](http://qa.openoffice.org/issues/show_bug.cgi?id=42985)

I posted my files here:

[http://www.pdx.edu/~johj](http://www.pdx.edu/~johj)

And someone on the OOo e-list that I subscribe to tried my file using OOo 2.04 and reported that the issue remains unresolved. Therefore I no longer have any need to upgrade to 2.04.

It appears that I am going to have to buy Acrobat Professional 7.0 or 8.0. I did print the form directly from OOo to a PostScript printer, after filling in some of the data, and the controls printed with the correct font. So if I create a .ps print file, the font data must become embedded. Therefore, I can distill it with Acrobat 7.0 or 8.0 and the resulting PDF should be correct. Unfortunately, there is no way to get it to run in WINE or Crossover Office. I'll have to install Windows 2000 with quemu or vmware or something. Gawd, I don't want to do that.

---

### Post by John Jason Jordan on 2006-11-08
> **IanW said:**
> You can install RPMs in Ubuntu by first installing "alien", a package converter in Synaptic.
I have tried to do that in the past and had zero success. And my attempts involved simple little apps, not an app as big as OOo.

Anyway, it turns out that 2.04 won't solve the problem anyway. Thanks for the suggestion, though. :)

---

### Post by xstaticxgpx on 2006-11-08
> **Kilz said:**
> Dapper has a 32bit Open office Edgy has a 64bit Open office. They both do the same things. The only difference is that in Edgy there are fewer ia32 packages installed making it harder to install 32bit applications. In this respect it was a bad thing. Sadly the developers thought this was a good thing in a discussion I had with them on the email lists last month. I believe this is affecting the installing of 32bit mplayer.

you don't have to now that building mplayer 1 has native wmv3 support (along with the win32 codecs)

---

### Post by Kilz on 2006-11-08
> **xstaticxgpx said:**
> you don't have to now that building mplayer 1 has native wmv3 support (along with the win32 codecs)

That may be, but I dont think I'm going to be installing Edgy. If I do it wont be for a month or so. As of now the versions I have tried with that are not installable to dapper.

---

### Post by Kilz on 2006-11-08
> **John Jason Jordan said:**
> Sorry! Yet another dumbass move. Turns out I have 2.02 also.

Regarding the "bug," evidently it is not a bug. It is by design not to embed fonts for controls in a form document:

[http://qa.openoffice.org/issues/show_bug.cgi?id=42985](http://qa.openoffice.org/issues/show_bug.cgi?id=42985)

I posted my files here:

[http://www.pdx.edu/~johj](http://www.pdx.edu/~johj)

And someone on the OOo e-list that I subscribe to tried my file using OOo 2.04 and reported that the issue remains unresolved. Therefore I no longer have any need to upgrade to 2.04.

It appears that I am going to have to buy Acrobat Professional 7.0 or 8.0. I did print the form directly from OOo to a PostScript printer, after filling in some of the data, and the controls printed with the correct font. So if I create a .ps print file, the font data must become embedded. Therefore, I can distill it with Acrobat 7.0 or 8.0 and the resulting PDF should be correct. Unfortunately, there is no way to get it to run in WINE or Crossover Office. I'll have to install Windows 2000 with quemu or vmware or something. Gawd, I don't want to do that.

Have you tried other applications to make the pdf like abiword?

---

### Post by John Jason Jordan on 2006-11-08
> **Kilz said:**
> Have you tried other applications to make the pdf like abiword?
Abiword cannot create forms. Nor can Scribus, or anything else I know of on Linux. I'm open to suggestions, however.

What I am trying to create is a PDF form that is editable. Editable PDF forms became possible after the release of Adobe Reader 7.0 and Acrobat 7.0 Professional. In an editable PDF file you can have controls, like text boxes, radio buttons, check boxes, drop-down lists, and others. The controls can even be tied to a database. Now, forms like this have existed in the world of word processing for a long time. Companies would create a form and lock it so that employees could only enter data in the controls, then print it out and send it to someone (management, etc.). Now we have Acrobat 7.0 and Reader 7.0, so management can now make the form a PDF file.

I wish to use this technology to create editable PDFs as student exercise tools. Think of drop-down boxes where the student chooses the correct answer from a list. Or think of multiple-guess questions where students click on a radio button in front of the correct answer. Or an essay question with a text box where students can type their answer. This can be used for exams, but an even better use would be practice sheets. Instead of making flash cards, the professor can make an editable PDF for the students to practice on. They can print their answers, but cannot save a copy or overwrite the original PDF. So after they finish the practice form they can correct it and, if they didn't get a good enough score, reopen the PDF and start over again with a fresh copy. Over time a professor can create a library of such editable PDF forms which can be recycled each time the professor teaches the course.

A professor is supposed to do this using MS Word (for the forms) and Acrobat 7.0 Professional (for the PDF creation). But I thought it should be possible under Linux. OpenOffice.org can create the form, but when the form is exported to PDF OOo sets the font for all controls to Helvetica, regardless of what the user set in the Properties sheet for the control. When Adobe Reader 7.0 opens the resulting PDF file, it doesn't have Helvetica, so it substitutes its own font. And its internal font lacks a lot of characters I need for linguistics work (characters in the International Phonetic Alphabet).

So there's the problem. AbiWord cannot create forms, so it is not a possibility, and I don't know of any other Linux software besides OOo that can create form documents. If anyone knows otherwise, I'd be eternally grateful for a suggestion. (OK, eternity is a very long time; but I'd be very, very, very grateful.)   :)

---

### Post by Kilz on 2006-11-09
> **John Jason Jordan said:**
> Abiword cannot create forms. Nor can Scribus, or anything else I know of on Linux. I'm open to suggestions, however.

What I am trying to create is a PDF form that is editable. Editable PDF forms became possible after the release of Adobe Reader 7.0 and Acrobat 7.0 Professional. In an editable PDF file you can have controls, like text boxes, radio buttons, check boxes, drop-down lists, and others. The controls can even be tied to a database. Now, forms like this have existed in the world of word processing for a long time. Companies would create a form and lock it so that employees could only enter data in the controls, then print it out and send it to someone (management, etc.). Now we have Acrobat 7.0 and Reader 7.0, so management can now make the form a PDF file.

I wish to use this technology to create editable PDFs as student exercise tools. Think of drop-down boxes where the student chooses the correct answer from a list. Or think of multiple-guess questions where students click on a radio button in front of the correct answer. Or an essay question with a text box where students can type their answer. This can be used for exams, but an even better use would be practice sheets. Instead of making flash cards, the professor can make an editable PDF for the students to practice on. They can print their answers, but cannot save a copy or overwrite the original PDF. So after they finish the practice form they can correct it and, if they didn't get a good enough score, reopen the PDF and start over again with a fresh copy. Over time a professor can create a library of such editable PDF forms which can be recycled each time the professor teaches the course.

A professor is supposed to do this using MS Word (for the forms) and Acrobat 7.0 Professional (for the PDF creation). But I thought it should be possible under Linux. OpenOffice.org can create the form, but when the form is exported to PDF OOo sets the font for all controls to Helvetica, regardless of what the user set in the Properties sheet for the control. When Adobe Reader 7.0 opens the resulting PDF file, it doesn't have Helvetica, so it substitutes its own font. And its internal font lacks a lot of characters I need for linguistics work (characters in the International Phonetic Alphabet).

So there's the problem. AbiWord cannot create forms, so it is not a possibility, and I don't know of any other Linux software besides OOo that can create form documents. If anyone knows otherwise, I'd be eternally grateful for a suggestion. (OK, eternity is a very long time; but I'd be very, very, very grateful.)   :)


A quick google search tells me that Scribus will do what you need. I have never used it, but there is a version, and a development version in the Dapper repo's.

---

### Post by xstaticxgpx on 2006-11-09
> **Kilz said:**
> That may be, but I dont think I'm going to be installing Edgy. If I do it wont be for a month or so. As of now the versions I have tried with that are not installable to dapper.

why not? I built and installed mplayer 1.0 rc1 on dapper, are you getting a error or something?

---

### Post by Kilz on 2006-11-09
> **xstaticxgpx said:**
> why not? I built and installed mplayer 1.0 rc1 on dapper, are you getting a error or something?

I havent tried to build it, I tried a few deb's but the requirements must have been for Edgy. Its not a biggie. So far the older version of mplayer32, mplayer plugin, and w32codecs works fine for the few sites I visit that use windows media formats.

---

### Post by the_burk on 2006-11-13
isnt the thing about open source to make new versions of old buggy programs... for free..  moreor less.. if something isnt working fix it... so ... as long as you have the source you can rebuild the programs with 64 bit native support... 

i mean.. theres a few people sitting on 64 bit os .. using 32 bit applications ... when they would use 64 bit if there were some... 

i meant ... porting programs is what linux / unix users do ... why complain now... when we made 64 bit versions of programs .. win users will want it to ... aso..

---

### Post by iLoVe.cF- on 2006-11-13
well.. yes..

You use ALOT OF 32Bit stuff..

But.. this is ALOT BETTER than windows in 64 bit.. since its like.. ohh i cant use that blabla.. i tried it .. :P
Was a HELL

but.. its nice to use 32 bit apps for 64 bit =)

well.. for as long as 64 bit support 32 bit completly.. noone will use 64 bit 
linux if you cant do much in 64 bit :p

So, this will go like.. piece by piece.. "i think" but... seems like it is like it.. but 64 bit have still some problems with stuff :p but i havnt met many problems yet ;D

Install the most smooth with dpkg -i --force-architecture


USE = --force-architecture
<3<3
Remember that command if it says blalbal cant balbla 64 bit.. =)

---

### Post by Kilz on 2006-11-13
> **the_burk said:**
> isnt the thing about open source to make new versions of old buggy programs... for free..  moreor less.. if something isnt working fix it... so ... as long as you have the source you can rebuild the programs with 64 bit native support... 

i mean.. theres a few people sitting on 64 bit os .. using 32 bit applications ... when they would use 64 bit if there were some... 

i meant ... porting programs is what linux / unix users do ... why complain now... when we made 64 bit versions of programs .. win users will want it to ... aso..

The problem isnt the open source applications. Those we can compile to work just fine on 64bit. The problem is the few proprietary things a lot of us cant do without that the source is not available for. Things like Flash that is owned by Adobe or some codecs like wmv or wma that are owned by Microsoft. These are only available as 32bit.

---

