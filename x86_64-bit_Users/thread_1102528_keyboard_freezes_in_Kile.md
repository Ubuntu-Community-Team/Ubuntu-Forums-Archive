---
title: "keyboard freezes in Kile"
date: 2009-03-21
forum: x86 64-bit Users
---

### Post by aimonas on 2009-03-21
Hello everyone,

I have recently installed 8.10 64-bit on a Compal FL90.

I just tried to compile some latex files using kile. After compilation the keyboard doesn't work for some reason. If I click on another window and then return in starts working again. The remedy of alt+tab for which I 've read through my preliminary search for the solution doesn't work. 

I had same problems with matlab on 8.04, but in that case the problem was related to java. 

Is there any solution in this case?

greets

---

### Post by aimonas on 2009-03-24
anybody?!

---

### Post by Grab_Your_Gun on 2009-04-01
The same problem here..:( found same bug that has been reported . no solution yet

---

### Post by aimonas on 2009-04-02
> **Grab_Your_Gun said:**
> The same problem here..:( found same bug that has been reported . no solution yet
it's a pitty. ok the program is still functional, but the bug spoils the peacefull state of having everything working as they should...anyway, if you find anything new about the solution please let me know, as of course will I. by the way, do you have the address where the bug is reported and discussed? 

greetings and thanks for the response!

---

### Post by tootoo on 2009-05-14
I have the same problem. I am using Ubuntu 9.04 amdx64 on a Dell GX620. It happens to me pretty frequently when I use Matlab and Kile. 

It does not seem to be a hardware problem, b/c the keyboard lock is only application specific. For example, right now I have a Matlab running which refuses keyboard input, but at the same time typing here works perfectly fine. 

In matlab, for example the problem arise when I excute:
>> figure;
without closing the empty figure window, get back to the matlab command window with mouse click and type:
>> close; 

the command window will refuse to accept typing after excute that line. Sometimes it recovers by itself after ~1 min, sometimes I have to switch to other window using mouse click and back. There are also times when the above method do not work at all so that I have to restart matlat. 

It is interesting that if I do the following, the keyboard problem does not appear:
>> figure;close;
Basically the difference is that I do not have the chance to switch back to the command window by mouse click because the figure window is generated and closed in one line.

It look that it has something to do with how to handel the focused window(??)

In Kile, it look that if I clicked on the toolbar items with small drop arrows.

Restart the program will fix the problem, but it is such a pain.

---

### Post by tootoo on 2009-05-16
Problem solved!  well, kind of.
I switched to Fedora 10, and the keyboard problem does not show up.

---

### Post by aimonas on 2009-05-16
> **tootoo said:**
> Problem solved!  well, kind of.
I switched to Fedora 10, and the keyboard problem does not show up.

sorry you had to take such drastic measures. 

Just for the record, after the upgrade in jaunty I have had no problems with kile. The editor itself has been upgraded and everything so far works like a charm. 

About matlab, I use it only at the uni where I still run ubuntu 8.04. The misfunction with the keyboard is related to java. It has been reported as a bug and can be resolved through:

[https://answers.launchpad.net/ubuntu/+question/26562]("https://answers.launchpad.net/ubuntu/+question/26562")

So, for anyone facing similar problems in jaunty or intrepid I would suggest to give it a try.

tootoo, sorry I couldn't get to you sooner. 

greetings

---

### Post by lethalfang on 2009-05-18
> **aimonas said:**
> sorry you had to take such drastic measures. 

Just for the record, after the upgrade in jaunty I have had no problems with kile. The editor itself has been upgraded and everything so far works like a charm. 

About matlab, I use it only at the uni where I still run ubuntu 8.04. The misfunction with the keyboard is related to java. It has been reported as a bug and can be resolved through:

[https://answers.launchpad.net/ubuntu/+question/26562]("https://answers.launchpad.net/ubuntu/+question/26562")

So, for anyone facing similar problems in jaunty or intrepid I would suggest to give it a try.

tootoo, sorry I couldn't get to you sooner. 

greetings

I have Ubuntu 9.04 in 3 different computers, anhd the new Kile crashes with severe regularity in all 3 of them. I had to download and install the Kile in Intrepid repo.

---

