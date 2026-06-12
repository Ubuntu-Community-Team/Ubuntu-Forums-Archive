---
title: "[SOLVED] Wine doesn't work for main user"
date: 2008-04-23
forum: Wine
---

### Post by GregMB on 2008-04-23
Hello. I am very new to Wine, and I am hoping someone can help me with a problem I haven't been able to fix. When I run Wine on my account on my computer, it freezes my computer and I have to manually reboot (A.K.A. hit the power switch). I googled for some info, and found that one user could use Wine on any account other than his main account. I figured it would be worth a shot to see if I had the same problem. It turns out, yes, I did. I read more about the problem, and someone suggested deleting the ~/.wine folder. It seemed to have worked for other people, so I tried it. Oddly enough, unlike my other account on my computer, I didn't /have/ a ~/.wine folder to begin with. I had three different folders, all in some kind of code, like .wine-eymZNx (that's the actual name of one of them). So I deleted all three, and tried Wine again. Close, but no cigar. My computer froze again. When I rebooted, a new wine folder (the one I mentioned above) appeared in the other three's place. I'm thinking of just copy and pasting the Wine folder from one of the other users on my computer that work fine, but before I did I wanted to know if anyone had any suggestions. If you have any tips/ideas/opinions/reasons why if I were to go ahead as planned the whole universe would explode/etc please post them. I've included a screenshot of the ghost Wine folder.

---

### Post by cogadh on 2008-04-23
When you say you were trying to run Wine, are you running "winecfg" before you try to run any applications? Those odd .wine-blAH directories are failed attempts by Wine to create a fake Windows directory, which often happens if you jump right into running an application before running winecfg to configure the .wine directory.

---

### Post by GregMB on 2008-04-23
winecfg freezes my computer too. Anything at all including Wine freezes my computer, with no error messages, or anything, on my main account at least.

---

### Post by GregMB on 2008-04-24
Any ideas? I tried Copy and Pasting a working Wine folder, but it didn't work.

---

### Post by chanhdat on 2008-04-26
Which version do you use now? If 0.9.60. Try an older version, maybe, the latest got some bugs ,
Read more here: ```
http://wiki.winehq.org/PreloaderPageZeroProblem
```
It solved my problem.

---

### Post by GregMB on 2008-05-10
> **chanhdat said:**
> Which version do you use now? If 0.9.60. Try an older version, maybe, the latest got some bugs.

How would I go about doing that? There's only one wine package listed in Synaptic (minus wine-dev, of course). Also, if it helps, it seems like the problem with wine is just creating the .wine folder.

---

### Post by GregMB on 2008-05-10
Also, the user I create just so I could use Wine, now can't use Wine! Oh, the bad luck of it all.

---

### Post by cogadh on 2008-05-10
> **GregMB said:**
> How would I go about doing that? There's only one wine package listed in Synaptic (minus wine-dev, of course). Also, if it helps, it seems like the problem with wine is just creating the .wine folder.
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by GregMB on 2008-05-10
> **cogadh said:**
> [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Thanks, I'll try that now. Two questions first: One, I assume I should remove the version of wine I have now, right? Two, is there an particular version I should install?

---

### Post by cogadh on 2008-05-10
No, you don't actually need to remove the existing Wine package, but considering the problems you have had, you might want to try that:
```
sudo apt-get remove --purge wine
```
After you follow the instructions on the Wine download page, Synaptic will automatically show the latest version only (1.0-RC1). Just install that one.

---

### Post by GregMB on 2008-05-10
Hmm... I used the command you said to, and follwed the wine instructions (changing "hardy" to "gutsy"), and reloaded synaptic, but it doesn't show 1.0 Release Candidate. I'm pretty sure it shows the same version I already had installed.

---

### Post by cogadh on 2008-05-10
Ah, didn't realize that you were using Gutsy (if you mentioned that in a previous post, I must have missed it, sorry). If that is the case, then the most recent Wine package you can get is 0.9.59. In order to get the actual current version, you will have to compile it yourself.

---

### Post by GregMB on 2008-05-11
> **cogadh said:**
> Ah, didn't realize that you were using Gutsy (if you mentioned that in a previous post, I must have missed it, sorry). If that is the case, then the most recent Wine package you can get is 0.9.59. In order to get the actual current version, you will have to compile it yourself.

I thought I said that I was using Gutsy, but looking back on my posts, I realize I didn't. Anyways, I am a total Ubuntu and Linux newbie, but I am a fast learner. How would I compile the program?

---

### Post by cogadh on 2008-05-11
Well, the process is relatively simple:
[list=1] 
[*]Download the source code from the WineHQ website
[*]Install the build-essential packages and all of Wine's dependencies. There's is a handy script that will do that for you. To get it and use it, just do this:
```
wget  http://kegel.com/wine/gutsy.sh
chmod +x gutsy.sh
sudo ./gutsy.sh
```
[*]Extract the source code then read the included readme for the configure and compile steps. Wine does come with an automated configure/make/install script, but I don't believe it actually works right with Ubuntu (installs stuff in odd places, really hard to remove if you have problems). I've always run the configure and make steps manually then, instead of using the standard install step, I use [CheckInstall](https://help.ubuntu.com/community/CheckInstall) and create a rough .deb package that I can easily remove if there are problems.
[/list]

That's really it. However, just for the sake of full disclosure, I've now run this process 4 times and each time I've ended up with a partially non-functional Wine 1.0-rc1. I can launch winecfg and installations, but once any sound is produced by the program (including testing sound in winecfg), Wine locks up completely. I'm not sure if it is a problem with the process I am using (which has worked many times in the past) or a problem with Wine itself.

---

### Post by GregMB on 2008-05-11
> **cogadh said:**
> Well, the process is relatively simple:
[list=1] 
[*]Download the source code from the WineHQ website
[*]Install the build-essential packages and all of Wine's dependencies. There's is a handy script that will do that for you. To get it and use it, just do this:
```
wget  http://kegel.com/wine/gutsy.sh
chmod +x gutsy.sh
sudo ./gutsy.sh
```
[*]Extract the source code then read the included readme for the configure and compile steps. Wine does come with an automated configure/make/install script, but I don't believe it actually works right with Ubuntu (installs stuff in odd places, really hard to remove if you have problems). I've always run the configure and make steps manually then instead of using the standard install step, I use [CheckInstall](https://help.ubuntu.com/community/CheckInstall) and create a rough .deb package that I can easily remove if there are problems.
[/list]

That's really it. However, just for the sake of full disclosure, I've now run this process 4 times and each time I've ended up with a partially non-functional Wine 1.0-rc1. I can launch winecfg and installations, but once any sound is produced by the program (including testing sound in winecfg), Wine locks up completely. I'm not sure if it is a problem with the process I am using (which has worked many times in the past) or a problem with Wine itself.

Well, I'll try that, and I hope it works, but I have my doubts (even though you probably know way more about wine than I do). EDIT: Also, when you say Wine locks up, do you have to reboot, or just close the program?

---

### Post by GregMB on 2008-05-11
Hmm... I'm looking around the wineHQ, but I can't seem to find the source code. Where exactly is it?

---

### Post by cogadh on 2008-05-11
[http://www.winehq.org/?announce=latest](http://www.winehq.org/?announce=latest)
The second and third links on that page are both for the source code tar ball. As for the lockup issue, it is not a system lock, just a Wine lockup.

---

### Post by GregMB on 2008-05-11
> **cogadh said:**
> [http://www.winehq.org/?announce=latest](http://www.winehq.org/?announce=latest)
The second and third links on that page are both for the source code tar ball. As for the lockup issue, it is not a system lock, just a Wine lockup.

That's good to hear. So many things freeze Ubuntu, it's really a pain. But even with that, it's ten times better than Windows. Anyways, I'm downloading the source code now, I really hope this works!

---

### Post by GregMB on 2008-05-11
Well, this stinks. I'm having some problems with Synaptic's repository thing, so I can't download the required packages just yet. Well, I'll try soon.

---

### Post by GregMB on 2008-06-26
YES! I uninstalled wine from synaptic, then installed wine 1.0 from wineHQ, and although it froze my computer when I first ran winecfg, after I rebooted, it works fine! Now, all I need to do is test it. Are there any good apps that work well under wine, just to make sure it works?

EDIT: I tried it with the Notepad that comes included with wine, and it works fine. I am so glad this works, as there are a few Windows programs that I can't find Linux alternatives to.

---

