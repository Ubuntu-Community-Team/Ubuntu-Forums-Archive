---
title: "xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_amd64.deb 403 Forbidden"
date: 2008-01-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by PenKnife on 2008-01-18
When Trying to run updates, I get this error:
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_amd64.deb)
  403 Forbidden

I cannot browse to the site listed either, is there a problem on the server, or a problem with the update that needed to be fixed, or am I wrong entirely?

---

### Post by GenuineXP on 2008-01-18
Same problem here. It was working this morning but I cancelled the download because I was running late. I tried browsing the server just now from Firefox and couldn't download any of the packages for that version (any architecture). Other versions could be downloaded just fine (including GITs).

What's going on? Is it a good thing that I didn't finish that update this morning? :-P

---

### Post by carsy on 2008-01-18
Exhibit 1 - Why use Ubuntu (Linux; open source)?

I had the same problem. Google (100% running on Linux) displayed this thread. In the proprietary world, problems like this would never see the light of day. And would take months to resolve.

Don't have an answer, but thanks for posting the issue.

Carl

---

### Post by GenuineXP on 2008-01-18
> **carsy said:**
> In the proprietary world, problems like this would never see the light of day.l
You're kidding, right?

In any case, this doesn't seem to be a disastrous issue or anything. I'm just curious why the server to the update is blocking people. (In fact, this isn't really an OS issue at all; it's the web server that's restricting access to a file, that's all.)

---

### Post by unknow2006 on 2008-01-18
if any of u didnt updated the x-server dont do it, i just did and now i cant enter in my gnome desktop, and after a couple of tries the whole system crash.

In case needed heres my comp spec:

Athlon x2 64 3800+
1Gb RAM
HD 320GB
MoBo Asus M2N-SLI DELUXE

---

### Post by nuir on 2008-01-18
I think the update had some bugs so it was removed or something like that... I read some thread where people said the update was breaking java apps. 

It probably will be available again when they fix any problem.

---

### Post by unknow2006 on 2008-01-18
Yeah, but i still cant use my linux, even remove the new x-server and reinstall the old one, i may try the live cd to see if im able to fix it.

---

### Post by Fnubey on 2008-01-18
The same problem here with normal i386 package. Tried to --fix-missing without success.

---

### Post by Lord Illidan on 2008-01-18
[http://ubuntuforums.org/showthread.php?t=671020](http://ubuntuforums.org/showthread.php?t=671020)
Should fix it.

---

### Post by GenuineXP on 2008-01-18
Hmm, I guess the problem was more serious than I thought. It's a good thing that I cancelled that installation. What luck!

---

### Post by PenKnife on 2008-01-18
Ok, so it was locked for a reason.   I did get the dev package, I guess that doesnt matter since everything is still working.  This is why I like forums, quick responses! :lolflag:

---

### Post by jaka on 2008-01-18
I have the same problem 

You don't have permission to access /ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb on this server.

---

### Post by unknow2006 on 2008-01-18
Even trying the solution from the W.McL post, im still w/ the same problem, after type my username and password the xserver restart and go back to the login screen (graphical one).

---

### Post by PenKnife on 2008-01-18
unknow2006: The fix on the top is for Gutsy, theres another apt line later in the thread for feisty...  You didnt say which you used

---

### Post by unknow2006 on 2008-01-18
Im using gutsy, and i found the problem, was my compiz, i think it got corrupt after the update, i removed it and its working now, i dont know if installing compiz again will work, ill w8 a bit more b4 try this, when they fix this patch i gonna do it. Thx for the help.

---

### Post by ebbomega on 2008-01-18
> **carsy said:**
> Exhibit 1 - Why use Ubuntu (Linux; open source)?

I had the same problem. Google (100% running on Linux) displayed this thread. In the proprietary world, problems like this would never see the light of day. And would take months to resolve.

You're right, problems like this don't happen in the proprietary world. If an update goes through that damages the install they just force it through anyways and release a patch to fix it a few weeks later.

Usually when this 403 forbidden error happens it's because the update has been pulled for bug fixing.... It's okay, your system just thinks it's not up to date until they fix the release and put out another one.

I just wish there was a better way to notify the update managers that an update has been pulled so that it doesn't keep trying to download it....

---

### Post by PenKnife on 2008-01-18
> **ebbomega said:**
> You're right, problems like this don't happen in the proprietary world. If an update goes through that damages the install they just force it through anyways and release a patch to fix it a few weeks later.

Usually when this 403 forbidden error happens it's because the update has been pulled for bug fixing.... It's okay, your system just thinks it's not up to date until they fix the release and put out another one.

I just wish there was a better way to notify the update managers that an update has been pulled so that it doesn't keep trying to download it....

I agree, I'm relatively new to the whole Linux scene, I have an MCP and I used to just turn windows updates off for fear that my machine would break with a hotfix or update from microsoft.  I've had many an experience with that  :)

---

### Post by chrono13 on 2008-01-19
I ran into this error as well.

A solution that worked for me:
In the Update Manager, click Check to re-download the package information, then click Update. This cleared the issue for me.


MCDST, MCP, A+, Network+, Security+, Linux+

---

### Post by David Jenkins on 2008-01-19
> **chrono13 said:**
> I ran into this error as well.

A solution that worked for me:
In the Update Manager, click Check to re-download the package information, then click Update. This cleared the issue for me.


MCDST, MCP, A+, Network+, Security+, Linux+

Worked for me too - I guess that they've sorted the problem (I hope... )

---

### Post by mehtuus on 2008-01-19
> **chrono13 said:**
> A solution that worked for me:
In the [Package] Manager, [reload] the package information, then click [the] Update [icon in the tray].


This worked for me as well.

---

### Post by EnkiduinNZ on 2008-01-19
> **Fnubey said:**
> The same problem here with normal i386 package. Tried to --fix-missing without success.

I assume you mean the 403 problem? 

--fix-missing is not a solution for not being able to download packages. The 403 says that you are forbidden to access that server so you can't download the packages. --fix-missing will not help with that problem.

I've not used --fix-missing, but i'd guess its main use would be to force on packages when a pre-req or co-req package can't be downloaded. It would leave a bunch of broken dependencies.

---

### Post by EnkiduinNZ on 2008-01-19
> **GenuineXP said:**
> You're kidding, right?

In any case, this doesn't seem to be a disastrous issue or anything. I'm just curious why the server to the update is blocking people. (In fact, this isn't really an OS issue at all; it's the web server that's restricting access to a file, that's all.)

I think carsy was saying that such an occurrence in the commercial world would be hidden from site, not that it would never happen! :)

---

