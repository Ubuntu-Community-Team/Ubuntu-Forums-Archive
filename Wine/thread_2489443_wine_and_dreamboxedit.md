---
title: "wine and dreamboxedit"
date: 2023-07-30
forum: Wine
---

### Post by hu016865 on 2023-07-30
I installed the wine program to run the dreamboxedit program on Ubuntu 22.04, but when I install the program, the dreamboxedit program does not run.
I installed the netscanner program to test it. It was installed and run, but the program does not display any network information.
Since I am new to Linux, I said that maybe the wine version was installed, it is not correct because I had previously installed the dreamboxedit program on KDE and it worked.
what should I do now ?

```
eza@reza-vaio:~$ wine --version 
wine-6.0.3 (Ubuntu 6.0.3~repack-1)

```

---

### Post by DuckHook on 2023-07-30
I'm perplexed. You state the you are new to Linux, yet you've been a forum member since 2009.

WINE is a complex platform that does not work consistently with Windows apps and should not be considered a reliable substitute for Windows.

Since you are new to Linux, you may find it worth your while to read the link in my sig: Linux Is Not Windows.

I successfully use WINE for many Windows programs, but I have realistic expectations and approach it with the attitude that I am lucky when it works. For truly mission critical Windows apps, I run them in a Virtual Machine of Windows, which guarantees that the app will work. The only Windows apps that I run on WINE are games and other non&#8209;essentials that don't bother me greatly if they fail.

Other forum members have had good results running the commercial version of WINE, CrossOver. Others have also had good luck with the WINE derivative, Proton, but that is mainly (only?) for games.

My own experience with WINE is that it often contains regressions such that a newer version of WINE will fail to run something that an older version runs successfully. Moreover, the same version of WINE will run an app on an older kernel/display server/video driver but not a newer. Last but not least, WINE will sometimes run apps without full functionality. This last is especially troublesome for important work since the broken functionality can be subtle and yield unreliable results.

The best advice I can give you is to use a Windows Virtual Machine for truly important apps. WINE should be thought of as a convenience, not as a reliable platform for mission critical apps.

---

### Post by hu016865 on 2023-07-31
Yes, you are right. 
I got acquainted with Linux years ago. But due to lack of time and other problems such as lack of mastery of English and my job being unrelated to computers (although my main interest is it), I could not learn it fundamentally (although Maybe it's a bit hard for me to learn at my current age).And I only know how to install Linux and run the command line.
I tried different distributions along with different desktops, and I had Windows and Linux side by side at the same time, and whenever I had a problem that could not be solved on Linux, I solved it on Windows. ).
At the suggestion of a friend to learn Linux better, I deleted Windows and now I only use Ubuntu. Before this I had Kubuntu 23.04 and the dreamboxedit program was installed and run without any problems using wine and it worked.
That's why I thought wine has different versions.
Or maybe the program is completely installed and I can't find it and run it.
In any case, I'd rather go back to Debian 12 with kde desktop than go back to Windows because now that I'm going to learn more, it's better to move on.

---

### Post by hu016865 on 2023-07-31
Solved.
I reinstalled and changed the installation directory to gnome desktop and luckily now it works without any problem...

---

### Post by DuckHook on 2023-07-31
I'm happy for you that you found a way to get it working.

Cheers!

DH

---

