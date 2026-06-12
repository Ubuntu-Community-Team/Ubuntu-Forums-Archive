---
title: "wine .exe problem (yeah, another one)"
date: 2008-06-11
forum: Wine
---

### Post by hockeyb47 on 2008-06-11
Sorry if this is in the wrong place, but I'm having a weird problem with a file called foo.exe. (not really, but yeah.) At first I was missing a .dll file, and I placed it in the system32 folder and did the whole library override dealio, but when I do wine 'foo.exe', the terminal looks like it's working on something for a second or two, then goes back to the prompt. No error, just. Nothing.

Any thoughts?

Oh, and I'm still on 7.10, if that's the problem.

---

### Post by molotov00 on 2008-06-11
Do:

sudo wine foo.exe

It's not ideal, but wine may be needing access to files. This was an issue for me in the past.

---

### Post by hockeyb47 on 2008-06-11
I've also tried that. Sorry I didn't mention it before.

---

### Post by molotov00 on 2008-06-12
Ok. 'man wine' reveals some debug options. See if you can get some useful output using those arguments.

---

### Post by hockeyb47 on 2008-06-12
Hmm. I did:
WINEDEBUG=warn+all
then the usual wine foo.exe deal, and no warning messages popped up.
I also tried it in one line to see if it did anything, but that didn't change anything. And just for fun, I did:
WINEDEBUG=warn+dll,+heap
because the missing DLL file was my problem before.

Soo. I hope that was useful to you? =)

---

### Post by p_quarles on 2008-06-12
Thread moved to the Wine area.

---

### Post by cogadh on 2008-06-12
[NEVER USE SUDO TO RUN WINE!!](http://wiki.winehq.org/FAQ#head-96bebfa287b4288974de0df23351f278b0d41014)

When you use sudo to run Wine it screws up the permissions on your .wine directory and allows Windows applications, including malware such as viruses and spyware, complete access to the Linux system. At best, all it will do is screw up the .wine directory and maybe some of your home directory, leaving your Windows applications unusable. At worst, it will completely hose your system. If you have used sudo to run Wine, you can try manually resetting the permissions on the .wine directory, but it is usually best to just delete the .wine directory and create a new one.

As for the problem you are having, it would help to know what you are actually trying to run. Certain applications require specific configurations in order to get them running properly, but without knowing what application you are working on, we can't really offer any kind of usable advice.

---

