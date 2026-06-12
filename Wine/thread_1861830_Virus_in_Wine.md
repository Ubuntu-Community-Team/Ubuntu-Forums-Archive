---
title: "Virus in Wine?"
date: 2011-10-16
forum: Wine
---

### Post by voldar on 2011-10-16
ok i have a stupid question i have wine 1.3 installed and was wondering if javascript exe viruses could be accessed through a linux web browser like reqonk or chromium to infect the .wine folder

---

### Post by CatKiller on 2011-10-16
The experiment was quite a while ago, but the last time someone tried they couldn't get a virus to work properly under Wine.

---

### Post by voldar on 2011-10-16
it would be nice to see some new tests. The latest wine has extensive vb run time support, i have seen programs run that i would have never thought possible a few years back. My biggest fear is my .wine folder might be screwed up to the point of needing to delete my entire wine folder and all programs installed in it because of a web page i visited. 

I know that it can never corrupt my linux os with out root access and i wouldnt be stupid enough to give a website my password but it might be able to do a number on my .wine folder and i have a number of programs installed on it that there are no linux alternatives to. My wife also uses a windows 7 virtual box for pogo.com because some games there will not run properly with linux for some odd reason

---

### Post by mörgæs on 2011-10-16
Moved to the Wine forum.

---

### Post by CatKiller on 2011-10-16
Unless you're running a Windows browser in Wine, nothing's going to touch it. If you're really worried about it, just back up your ~/.wine directory. Or run Wine as a different user to the one that browses the Internet.

---

### Post by haqking on 2011-10-16
A friends post in this subject may be of interest.

[http://dangertux.wordpress.com/2011/09/17/the-truth-about-windows-malware-wine-and-ubuntu/](http://dangertux.wordpress.com/2011/09/17/the-truth-about-windows-malware-wine-and-ubuntu/)

---

### Post by cwwilson721 on 2011-10-16
There seems to be confusion here about:
[LIST]
[*]Possibility
[*]Probability
[/LIST]
Possibility: Is it possible? The short answer is Yes. *_IF_* you 'get' the virus in the browser, *_IF_* wine is running at the same time, and *_IF_* the virus is written to go through the browser, look for a running wine program, and the correct dll and 'hooks' in wine are running, then YES.

Probability: About as close to ZERO as possible.

---

### Post by voldar on 2011-10-16
> **haqking said:**
> A friends post in this subject may be of interest.

[http://dangertux.wordpress.com/2011/09/17/the-truth-about-windows-malware-wine-and-ubuntu/](http://dangertux.wordpress.com/2011/09/17/the-truth-about-windows-malware-wine-and-ubuntu/)

wow thanks for the link thats some pretty useful info i think i will just use virtualbox to run my programs and uninstall wine. if the vm gets infected i can just wipe it. as viruses cannot escape vm

---

### Post by haqking on 2011-10-16
> **voldar said:**
> wow thanks for the link thats some pretty useful info i think i will just use virtualbox to run my programs and uninstall wine. if the vm gets infected i can just wipe it. as viruses cannot escape vm

Well that is another misconception also.

the fact is using a VM often uses networking and shared folders so similar rules apply, especially if you are using bridged networking for example then worm propogation is as seamless as any other machine on a network.

but like WINE it is unlikely, just dont get fooled into the common misconception that certain things are 100% secure, they are not.

By definition a network is about shared resources, if you share the same air with one or many others you are susceptible to the same germs whether you are fit and healthy or not, there are just degrees of susceptability.

This is not scaremongering, it is just common sense, nothing is 100% secure unless turned off and not connected.  just use common sense and vigilence and dont do things, run things, install things unless you trust the sources and integrity of them, the biggest security flaw of any system is **PEBKAP=Problem Exists Between Keyboard And Person**

---

