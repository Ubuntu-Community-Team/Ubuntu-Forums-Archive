---
title: "Adobe Reader 9.1 plugin for Firefox"
date: 2009-04-21
forum: x86 64-bit Users
---

### Post by Yankee_Fan on 2009-04-21
I'm running Jaunty x86_64.  I downloaded and installed Adobe Reader 9.1 and it works great as a standalone app.  However the plugin does not seem to be working in Firefox.  The following error is shown when running Firefox from a terminal:

[INDENT]**LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/nppdf.so [/usr/lib/mozilla/plugins/nppdf.so: wrong ELF class: ELFCLASS32]**[/INDENT]

Any ideas?

---

### Post by Yellow Pasque on 2009-04-21
It's a 32-bit plugin. It won't work in a 64-bit browser without nspluginwrapper.

FWIW, medibuntu has an amd64 version of Acrobat with a 64-bit version of nppdf.so. 
Unfortunately, that version is only 8.1.3 at this time. I'm not sure where medibuntu got that version, or if a 64-bit plugin is available for Acrobat 9.1 at this time.

---

### Post by Yankee_Fan on 2009-04-21
> **Temüjin said:**
> It's a 32-bit plugin. It won't work in a 64-bit browser without nspluginwrapper.


Could you point me towards any info on how to use nspluginwrapper?  Thx.

---

### Post by Yankee_Fan on 2009-04-21
Never mind...I figured it out.

---

### Post by michael37 on 2009-04-22
Just for the record, I found it to be quite inefficient and not always stable.  Unless you absolutely need to view PDF files inside your browser, consider downloading files to disk and then opening them in acrobat reader or evince.

---

### Post by Godly on 2009-04-22
Thanks for the advice. ;)

---

### Post by Arup on 2009-04-22
Adobe reader has had a spate of security issues, they have affected Windows but I would worry about Adobe's speed of patching. Since there are so many good reader options in Linux and there is also a good PDF editor included in the Ubuntu repos, I don't see the need to increase the risk un-necessarily. Also bear in mind, ndiswrapper is not recommended if you are using Adobe Flash 10x64 in your installation.

---

### Post by ArtInvent on 2009-05-11
Can you enlighten me as to how, exactly, you can use Reader 9 with nspluginwrapper for the plugin for Firefox? I have the same problem as in the first post of this thread.

I have Reader 9 installed and working I can't seem to install the plugin from Synaptic without also installing Reader 8.x, which would seem to be a mistake. Maybe you get the plugin from somewhere else - I can't seem to find it at Adobe . . . 

Here's why I need Reader 9 in Jaunty 64: I need to print postage from US Postal Service website. It only works if Reader is at least v9. Ugh. I had it working in 8.04 and upgraded 8.10 - but now I have to figure it out all over again. 

It's tiny but significant little hassles like this that have me dreading upgrading, and, especially, fresh installs.

---

### Post by ArtInvent on 2009-05-11
I've not solved this exactly, but I discovered that once Reader 9 was installed, the USPS label printing does seem to work even though the plugin isn't installed. 

I did open up Reader - Edit | Preferences | Internet and check Allow fast web view., and for the Browser Executable, entered /usr/bin/firefox

So I still haven't figured out the nspluginwrapper question. I guess the plugin really just allows the pdf to appear in the browser window rather than download and open in the Reader standalone app. It might be nice if this worked, I suppose, for other purposes like online form filling at the DMV, etc.

---

### Post by Yellow Pasque on 2009-05-11
Make sure you have nspluginwrapper installed:
```
sudo apt-get install nspluginwrapper
```
Now find the nppdf.so file that came with Reader9 (I don't know the exact path off the top of my head, so do a search for it if you can't find it)
```
sudo nspluginwrapper -i <path to nppdf.so>
```
I forget whether this installs the resulting npwrapper file automatically. If it doesn't, copy that file (npwrapper.nppdf.so) to a firefox plugin directory (e.g. ~/.mozilla/plugins )

Restart Firefox and check about:plugins to see if you succeeded.

[Personal Rant] I installed Adobe Reader 8 on my last 8.10 install this way and it seemed to work well. I'm currently on a fresh install of Ubuntu 9.04 and I'd like to avoid installing Adobe Reader if possible.
BTW, I installed it to use fillable forms to RMA a DOA video card. I never got to RMA my HIS video card because the RMA .pdf was broken (I even tried on my mom's Windows box). I wish I had saved the string of tech support e-mails because they're hilarious. To summarize:
Me to HIS tech support: I can't RMA my card because the 3rd-party RMA site you pointed me to has a borked .pdf
HIS support: Here's a link to that site. Let us know if you need more help
Me: But the .pdf is broken.... I've tried Adobe Linux, Adobe Windows, Foxit Windows, nothing works - conclusion = the RMA .pdf is borked
HIS support: Here's a link to that site. Let us know if you need more help
(/me e-mails the 3rd-party site with all the info it asks for in plain text form and receives no response)
[/Personal Rant]

---

### Post by rolandixor on 2009-06-08
I couldn't get nspluginwrapper working, I'll look it up.

---

### Post by defaria on 2009-07-19
> **Temüjin said:**
> Make sure you have nspluginwrapper installed:
```
sudo apt-get install nspluginwrapper
```
Now find the nppdf.so file that came with Reader9 (I don't know the exact path off the top of my head, so do a search for it if you can't find it)
```
sudo nspluginwrapper -i <path to nppdf.so>
```
I forget whether this installs the resulting npwrapper file automatically. If it doesn't, copy that file (npwrapper.nppdf.so) to a firefox plugin directory (e.g. ~/.mozilla/plugins )

Restart Firefox and check about:plugins to see if you succeeded.

I see it in about:plugins but when I try to use it it says couldn't open PDF file for some unknown reason...

---

### Post by modmadmike on 2009-09-20
I need acrobat reader in the browser because of the damn secure PDFs for my online Algebra 2 textbook :(. Ill try the method pointed out here, but im using Karmic x64 so i have no idea if it will work.

---

### Post by JuanCarlosThe4th on 2009-11-06
I just installed 9.10-64 bit, and got **AdbeRdr9.2-1_i486linux_enu.tar.bz2** from Adobe's site.  Note that you can also download a deb file, but that file will only work on 32-bit ubuntu.  I untarred and installed Adobe Reader in **/opt/Adobe/Reader9**. The tar file has a **ReadMe.htm** file in it with directions for installing Acrobat.  Then I ran **sudo apt-get install nspluginwrapper**.  At this point I decided to check if 
**nppdf.so** was already in the pluggins directory because of defaria's comment.
```
sudo updatedb
locate *nppdf* | xargs ls -l
-rwxr-xr-x 1 john root 179552 2009-11-06 10:26 /home/john/.mozilla/plugins/nppdf.so
-rwxr-xr-x 1 root root 179552 2009-10-07 20:31 /opt/Adobe/Reader9/Browser/intellinux/nppdf.so
-rwxr-xr-x 1 root root 179552 2009-11-06 10:26 /usr/lib/firefox-addons/plugins/nppdf.so
-rwxr-xr-x 1 root root 179552 2009-11-06 10:26 /usr/lib/firefox/plugins/nppdf.so
-rwxr-xr-x 1 root root 179552 2009-11-06 10:26 /usr/lib/mozilla/plugins/nppdf.so
```

It was, but firefox wouldn't open pdfs in the same window.

Running this made firefox open pdfs in firefox after my next firefox restart:
```
sudo nspluginwrapper -i /opt/Adobe/Reader9/Browser/intellinux/nppdf.so
```

---

