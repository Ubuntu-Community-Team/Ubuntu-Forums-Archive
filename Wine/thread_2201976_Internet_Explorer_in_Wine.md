---
title: "Internet Explorer in Wine?"
date: 2014-01-26
forum: Wine
---

### Post by Victor_Jackson on 2014-01-26
I installed the wine app a while back just incase i need it later and here is what i found . it has windows in it along with IE and that makes me nervous. I hate that leaky IE and windows but is it nessecary for wine to work ?

---

### Post by monkeybrain20122 on 2014-01-26
It is fake IE. I think it needs something like that to work. Besides, no one tells you to go on the internet with it. ;)

---

### Post by ian-weisser on 2014-01-26
> **Victor_Jackson said:**
> I installed the wine app a while back just incase i need it later and here is what i found . it has windows in it along with IE

One of the goals of Package Management and Software Center is that you don't need to install anything "just in case you need it later". It will still be available if you need it later.

Wine does NOT contain an instance or copy of Windows. Not one byte.

---

### Post by RadicaX on 2014-01-26
> **ian-weisser said:**
> One of the goals of Package Management and Software Center is that you don't need to install anything "just in case you need it later". It will still be available if you need it later.

Wine does NOT contain an instance or copy of Windows. Not one byte.

And that is why I do not have Wine installed. But You do not need to worry, it is recommended, never run wine under root, and make sure you have all your security features set up, it is possible to run a virus through Wine. But if it is sitting there, it is not going to get a virus. Make sure you have an app armor profile, and you are running good browser security. (Like for example, no script on firefox.) Also, if it ask you for your password or something weird and is wanting to run, you can just stop it or not put in your password.

---

### Post by DuckHook on 2014-01-27
> **Victor_Jackson said:**
> I installed the wine app a while back just incase i need it later and here is what i found . it has windows in it along with IE and that makes me nervous. I hate that leaky IE and windows but is it nessecary for wine to work ?It is not possible to give ironclad reassurances about anything in computer-space. The IE clone in WINE is like everything else in WINE&#8212;it is an open source implementation of the app designed to ape MS IE as accurately as possible. It is necessary because of a sad historical fact: in the first browser war, MS successfully strangled Netscape by tying IE into Windows so tightly that it became impossible to make Windows work properly without IE, thereby foisting their browser onto their captive audience and rendering Netscape superfluous. So, for WINE to work at all, its developers had to include a form of IE at least sufficient to satisfy apps that expect IE to be present.

The problem is that you can't build an IE clone without also duplicating IE holes, notwithstanding that it's open source. And since MS is infamous for its security holes, you have no choice but to live with the fact that WINE's version of IE is unlikely to be much safer than MS's version (some people extend this logic to WINE itself). To add insult to injury, since the biggest security risk in any OS is the browser, the presence of IE on your system is a big open wound.

Solutions/workarounds

1. Never, ever use IE. Treat it as the monster under the bed.
2. Never, ever run WINE as root, using sudo or otherwise.
3. If you are sufficiently paranoid, then ditch WINE altogether and run your Windows programs in a Windows VM. You will always be able to roll back to a known clean snapshot should your VM become infested by malware.

**Edit**

Having said the above, I do run WINE. I use it *only* for SimCity and Civilization and for *nothing* else. If these games are infested with malware, then I'm screwed. It's a chance I'm willing to take.

---

### Post by Impavidus on 2014-01-27
> **RadicaX said:**
> And that is why I do not have Wine installed. But You do not need to worry, it is recommended, never run wine under root, ...

> **DuckHook said:**
> (...)
2. Never, ever run WINE as root, using sudo or otherwise.
(...)
I concur, but has any of you actually tried it? I remember that about a year ago some noob wanted to run his wine as root (because he wanted to run everything as root, bad idea) and failed to do so. I did some digging and found that wine is supposed to have a safeguard against it. When the wine startup script detects it is being run as root, it simply terminates. I don't have wine installed myself, so I can't easely check. Of course, disabling that safeguard would be a bad idea too.

---

### Post by RadicaX on 2014-01-27
> **Impavidus said:**
> I concur, but has any of you actually tried it? I remember that about a year ago some noob wanted to run his wine as root (because he wanted to run everything as root, bad idea) and failed to do so. I did some digging and found that wine is supposed to have a safeguard against it. When the wine startup script detects it is being run as root, it simply terminates. I don't have wine installed myself, so I can't easely check. Of course, disabling that safeguard would be a bad idea too.

Since I do not use Wine No more, no. I have not used it since I first used Ubuntu. I am on Xubuntu 12.04 now. I believe this, just because you drive a tank around, you do not taunt the enemy who uses stones and sticks. You never know when they are going to get that one lucky shot in and knock you out. In the security forums, there is a sticky that goes a little more indepth on security and Wine. And just good practice for it. Honestly, turning wine off is easy, just remember like duckhook says, not to run it as root or sudo it. You have your extra security in case some unknown hole does pop up.

---

### Post by DuckHook on 2014-01-27
> **RadicaX said:**
> ...just because you drive a tank around, you do not taunt the enemy who uses stones and sticks.:lolflag:Wonderful metaphor.> **Impavidus said:**
> ...has any of you actually tried it?...I don't have wine installed myself, so I can't easely check.Though installed, I won't be checking. Seeing as we are in the mood for metaphors: I don't use crack either, but I don't need to try it to know that it's bad for me.

---

### Post by RadicaX on 2014-01-27
> **DuckHook said:**
> ...Though installed, I won't be checking. Seeing as we are in the mood for metaphors: I don't use crack either, but I don't need to try it to know that it's bad for me.

^ 
+1

---

### Post by monkeybrain20122 on 2014-01-27
Well sometimes it can be useful if you need a few applications. Pipelight is very useful if you watch netflix or needs latest Windows flash. Otherwise I use Wine only for pdf-xchange viewers to fill forms once in a blue moon (unfortunately can't find an equivalent Linux app especially for forms with scripts) and a two old statistical programs both of which are for curiosity rather than necessity (WinBUGS and Lisrel student edition, there are Linux native applications that do the same thing like jags and OpenMX), and yeah I play plants vs zombies but I have already reached the higest level. :)

As other say never sudo with wine (I saw an online tutorial where the guy run everything wine with sudo, I sent him an email telling him that was very bad advise especially it was presented as a tutorial for newbies, he never replied)

---

