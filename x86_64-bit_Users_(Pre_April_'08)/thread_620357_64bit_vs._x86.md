---
title: "64bit vs. x86"
date: 2007-11-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by whitenerdy92 on 2007-11-22
Stupid Question:
What's the main difference between x86 and 64bit machines? I've noticed that 64bit has less available applications, so what are its advantages?

---

### Post by rsambuca on 2007-11-22
x86 architecture is 32bit, whereas the 64bit machines are obviously 64bit.  64bit machines can utilize much more RAM than 32bit OS's, and due to the registers, can execute instructions much more quickly.  For things like internet surfing, email, and word processing, you won't see much difference between the two, but for tasks that utilize the cpu significantly, you can notice upwards of 30% gains in a 64bit computer and OS.  Things like video transcoding (ie. backing up DVD's), audio transcoding (ripping CD's to a different codec), and 3D Rendering (using Blender for 3D images).  There are many other areas as well, but these are some of the more common areas of improvement.

It used to be the case that 64 bit systems were more difficult to maintain, but lately, due to a lot of hard work by the developers and members of the Ubuntu community, one is almost as easy as the other.

As far as numbers of programs, the repositories are almost identical, so that really isn't an issue anymore.  There are 23,112 packages in the Gutsy amd64 repos, versus 23,454 in the 32bit repos.  Unless you are going really obscure, you should be fine.

---

### Post by Ehtetur on 2007-11-22
NOT a stupid question.. and welcome to the world of x64...
Many x64 questions are addressed in the sticky thread:
 [*****Announcement: Intel/Amd 64-bit Users Please Read*****]("http://ubuntuforums.org/showthread.php?t=185303")

---

### Post by rsambuca on 2007-11-22
> **Ehtetur said:**
> NOT a stupid question.. and welcome to the world of x64...
Many x64 questions are addressed in the sticky thread:
 [*****Announcement: Intel/Amd 64-bit Users Please Read*****]("http://ubuntuforums.org/showthread.php?t=185303")

I don't think that is the correct link.  Try[ this one instead]("http://ubuntuforums.org/showthread.php?t=368607").

---

### Post by Kilz on 2007-11-22
> **whitenerdy92 said:**
> Stupid Question:
What's the main difference between x86 and 64bit machines? **I've noticed that 64bit has less available applications,** so what are its advantages?

Exactly where did you notice this very common piece of misinformation?

---

### Post by Sukarn on 2007-11-22
> **Kilz said:**
> Exactly where did you notice this very common piece of misinformation?
Well, getting java to work with FF requires using the 32 bit version of FF, and the same goes for flash 9 unless you use nspluginwrapper.

---

### Post by Kilz on 2007-11-22
> **Sukarn said:**
> Well, getting java to work with FF requires using the 32 bit version of FF, and the same goes for flash 9 unless you use ndiswrapper.

The original poster said that applications were not available. You have proven that the applications you have pointed out are available. Not only that but flash can be installed with synaptic in gutsy. You can even try icedtea java with synaptic.
But if icedtea doesnt open your site , yes you are right, a 32bit browser is needed. 
[sarcasm] Its just way to difficult for the average person to have to double click on a file to install it.  Those few yes or no questions. How can we expect someone who went to public school know how to answer those? [/sarcasm]

So instead of running a 32bit browser on a 64bit install (if you need a java plugin, lots of people dont), where everything else is 64bit. With the possibility of performance increases. Are you suggesting someone would be better off running a complete 32bit system that has no performance increese?

Think twice about that before answering.

---

### Post by dralokyn on 2007-11-23
> **Kilz said:**
> So instead of running a 32bit browser on a 64bit install (if you need a java plugin, lots of people dont), where everything else is 64bit. With the possibility of performance increases. Are you suggesting someone would be better off running a complete 32bit system that has no performance increese?

Think twice about that before answering.

not to mention we've been promised a 64-bit java from sun on their next release. with the notable exception of java, i've had the EXACT SAME issues with 64-bit as i did with 32-bit; mainly with wireless drivers. gutsy 64 is a lot smoother and more reliable than fedora core 32 and debian etch 32.

---

### Post by dptxp on 2007-11-23
64 bit so cool.
AMD and INTEL do not make 32 bit series process anymore and when it comes to 64 bit OS, Linux rules.

---

### Post by whitenerdy92 on 2007-11-23
1. I've found less 64-bit application support on sites like GetDeb
2. How long ago have Intel and AMD been using 64bit? Obviously AMD64 means 64, but I'd like to know how many of my older Intels have 64bit also
3. Thanks guys, I was going to install 64bit Gutsy on by brothers Athlon 64 (I think) Gateway Laptop, so I wanted to know the advantages of both types. The Vista he has now is 32bit, and that made me wonder why it didnt use 64. (BTW, laptop has pretty similar specs to mine)

---

### Post by rsambuca on 2007-11-23
> **whitenerdy92 said:**
> 1. I've found less 64-bit application support on sites like GetDeb
2. How long ago have Intel and AMD been using 64bit? Obviously AMD64 means 64, but I'd like to know how many of my older Intels have 64bit also
3. Thanks guys, I was going to install 64bit Gutsy on by brothers Athlon 64 (I think) Gateway Laptop, so I wanted to know the advantages of both types. The Vista he has now is 32bit, and that made me wonder why it didnt use 64. (BTW, laptop has pretty similar specs to mine)

1.  Don't go by one site.  As I showed earlier, the packages are almost identical in the repos between the 32bit and 64bit version.  In the strange event that you can't find a .deb, then you can always compile any opensource program, although that is very rare.
2.  The Intel Core2Duo's use the 64bit architecture, as well as a few others, but not many.  For instance, the Core Duo chips are NOT 64bit.  Some of the newer Pentium 4's are 64bt.
3.  64bit support in Windows is light years behind linux at the moment.  Most vendors just aren't interested in supporting the 64bit versions in Windows since it is much less popular.

---

### Post by kuja on 2007-11-23
AMD has been since April2003 (which is when the K8s made their debut) 
"Intel 64 was originally implemented on the E revision (Prescott) of Pentium 4 line of microprocessors, which were supported by i915P (Grantsdale) and i925X (Alderwood) chipsets in June 2004." Later Pentium D's CPUs supported it, Core CPUs did not .. Core 2 CPUs do.

---

### Post by whitenerdy92 on 2007-11-23
How about a 2-year-old 1.7Ghz Pentium M? Would that be 64bit? Intel should do a better job of advertising which ones are 64bit or not

---

### Post by whitenerdy92 on 2007-11-23
Also, anyone know any other good sites to find .deb's?

---

### Post by rsambuca on 2007-11-23
> **whitenerdy92 said:**
> Also, anyone know any other good sites to find .deb's?

What are you looking for that isn't in the repos?

---

### Post by whitenerdy92 on 2007-11-23
Nothing really in particular, maybe some good games or something to improve system performance.
It's just nice to have some places to find something new is all.

---

### Post by Arkainium on 2007-11-23
> **whitenerdy92 said:**
> How about a 2-year-old 1.7Ghz Pentium M? Would that be 64bit? Intel should do a better job of advertising which ones are 64bit or not

No, that's not 64-bit.

---

### Post by rsambuca on 2007-11-23
Have you searched through the 23,000+ packages in Synaptic?

---

### Post by kuja on 2007-11-23
> **whitenerdy92 said:**
> How about a 2-year-old 1.7Ghz Pentium M? Would that be 64bit? Intel should do a better job of advertising which ones are 64bit or not

Anything I didn't list (with the exception of the final generation of Celeron-D's) are not 64-bit. That would include all mobile CPUs before the Core2.

---

### Post by Mr_bleu on 2007-11-24
**"but I'd like to know how many of my older Intels have 64bit also"**
How many older intel cpus do you have and which ones?  DOes it really matter about your older ones, or are you just being difficult?  I think you are.
***"How about a 2-year-old 1.7Ghz Pentium M? Would that be 64bit? Intel should do a better job of advertising which ones are 64bit or not"***
Learn to read.  INtel has the specs for each processor they make on their website.  You should search the forums before posting questions.  This question has been discussed at length already.  Intel doesn't need to do alot of advertising.  The companies they sell to do that for them. Dell, Gateway, Hp, Tiger direct, Newegg, many many more.

---

### Post by Kilz on 2007-11-24
> **whitenerdy92 said:**
> Also, anyone know any other good sites to find .deb's?

[Here is a great site]("http://packages.ubuntu.com/"). :D

---

### Post by Yellow Pasque on 2007-11-24
Another good one:
[http://ubuntuforums.org/showthread.php?t=432642](http://ubuntuforums.org/showthread.php?t=432642)

---

### Post by whitenerdy92 on 2007-11-25
Believe me, I love the repositories, but most applications have several packages associated with them, so 23,000+ packages does not mean 23,000+ applications. Although I never actually counted, I'd say that theres about half of that. Divided amongst 20 catagories, that leaves only about 1,000 packages per catagory, and a few hundred applications. I know that's alot, but then there's maybe only a few that actually fit what you're actually looking for.

P.S.
Yes, I am trying to be difficult. :)

---

### Post by whitenerdy92 on 2007-11-25
Also, I know that Kilz and rsambuca are going to say something to make me wrong again. :)

---

### Post by rsambuca on 2007-11-25
> **whitenerdy92 said:**
> Believe me, I love the repositories, but most applications have several packages associated with them, so 23,000+ packages does not mean 23,000+ applications. Although I never actually counted, I'd say that theres about half of that. Divided amongst 20 catagories, that leaves only about 1,000 packages per catagory, and a few hundred applications. I know that's alot, but then there's maybe only a few that actually fit what you're actually looking for.

P.S.
Yes, I am trying to be difficult. :)

I don't know what you want me to say.  The point that you do not seem to get is that those numbers are virtually the same for both the 32bit and 64bit versions.  So please don't pretend to make that an issue.  Frankly, the repos for Ubuntu are much better than most other distros out there.

---

### Post by Sockerdrickan on 2007-11-25
Well some games are released for 32bit today, even most of them. But they can often be played great anyway.

---

### Post by Kilz on 2007-11-25
> **whitenerdy92 said:**
> Also, I know that Kilz and rsambuca are going to say something to make me wrong again. :)

Not wrong, its just that the first place you or anyone running Ubuntu should look is in the repos. New users especially those coming from Windows are used to looking all over creation for applications. I know I have answered a ton (and Im sure everyone who answers questions on the forum has) of posts where the person looking for an application, or having problems compiling never looked in the repositories. 
Also let me give you some insight I have gained. If you like looking for applications , great. But in linux beware of the development or beta releases.  Especially if you do not have a firm grasp of how to troubleshoot a broken system. The reason is , that the linux development model uses the user to troubleshoot and find bugs. Beta are just barely working most of the time. Dont expect anything but problems from them. Thats why I always suggest new users think twice about replacing a version of something that works.

---

