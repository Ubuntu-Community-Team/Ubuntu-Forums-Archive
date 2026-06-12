---
title: "Can I install amd64 kernel in i386 userland?"
date: 2007-11-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by cmost on 2007-11-04
I've done some searching on these forums and Google, but haven't found anything recent.  I'm wondering if it's possible to use the amd64 kernel on an ordinary x86 installation.  I know what many will ask:  "Why not just use the x86-64 bit version of Ubuntu?"  I have several good reasons why I am choosing not to do that (yet.)  If anyone has successfully transplanted the amd64 kernel into an i386 userland, please post a mini howto and any problems you encountered.  I do realize that I will have recompile my nvidia and vmware modules using the amd64 versions of the drivers.  Is there anything else I might have to do (e.g., edit any config files, trick Synaptic / Apt, etc?)  I appreciate any help the community can provide.  Thanks!

---

### Post by Kilz on 2007-11-04
> **cmost said:**
> I've done some searching on these forums and Google, but haven't found anything recent.  I'm wondering if it's possible to use the amd64 kernel on an ordinary x86 installation.  I know what many will ask:  "Why not just use the x86-64 bit version of Ubuntu?"  I have several good reasons why I am choosing not to do that (yet.)  If anyone has successfully transplanted the amd64 kernel into an i386 userland, please post a mini howto and any problems you encountered.  I do realize that I will have recompile my nvidia and vmware modules using the amd64 versions of the drivers.  Is there anything else I might have to do (e.g., edit any config files, trick Synaptic / Apt, etc?)  I appreciate any help the community can provide.  Thanks!

It cant be done to my knowledge. Why would you want to anyway?

---

### Post by cmost on 2007-11-04
Hi Kilz!  Well, I have 4 GB of RAM on my system.  I'm currently running the equivalent of Feisty, but it's generic kernel only recognizes 3 GB of my 4 GB.  I upgraded to the server version of the kernel and that now shows 4 GB of RAM.  I realize that 32 bit is limited to a max of 4 GB of RAM, but a 64 bit kernel has no such limitation while also having the advantage of being able to execute both 32 bit and 64 bit code.  I've read several interesting posts where users were able to shoehorn the amd64 kernel into their 32 bit userlands without issue.  Before experimenting on my own machine, I thought I would gather as much information as possible.  Here's one more recent link in which a user got this to work:  [http://ubuntuforums.org/showthread.php?p=3693052](http://ubuntuforums.org/showthread.php?p=3693052)

Any thoughts appreciated.

---

### Post by Kilz on 2007-11-04
> **cmost said:**
> Hi Kilz!  Well, I have 4 GB of RAM on my system.  I'm currently running the equivalent of Feisty, but it's generic kernel only recognizes 3 GB of my 4 GB.  I upgraded to the server version of the kernel and that now shows 4 GB of RAM.  I realize that 32 bit is limited to a max of 4 GB of RAM, but a 64 bit kernel has no such limitation while also having the advantage of being able to execute both 32 bit and 64 bit code.  I've read several interesting posts where users were able to shoehorn the amd64 kernel into their 32 bit userlands without issue.  Before experimenting on my own machine, I thought I would gather as much information as possible.  Here's one more recent link in which a user got this to work:  [http://ubuntuforums.org/showthread.php?p=3693052](http://ubuntuforums.org/showthread.php?p=3693052)

Any thoughts appreciated.

Please link to a topic of anyone who has successfully done this. I have been around a long time and have not seen it. Even if you could do it, why would you want to have a 64bit kernel and only use 32bit applications. It would defeat the purpose of having a 64bit kernel to me. It would be like putting a hemi in a yugo.
Granted, your home folder that houses settings only can be used, but not the other areas, maybe thats what you are referring to?
What reasons do you have for not installing the 64bit version and using everything 64bit?

---

### Post by dcstar on 2007-11-05
> **cmost said:**
> I've done some searching on these forums and Google, but haven't found anything recent.  I'm wondering if it's possible to use the amd64 kernel on an ordinary x86 installation.  .........!

No.

AMD64 code is not compatible with 32 bit x86 processors.

---

### Post by cmost on 2007-11-05
> **dcstar said:**
> No.

AMD64 code is not compatible with 32 bit x86 processors.

Please refer to my signature.  I have a dual core AMD X2 Athlon processor.  It's fully 64 bit compatible.

My primary reasons for wanting to do this are several: 1. for experimentation.  Since it's possible to create a fully 32 bit chroot environment within a 64 bit userland (whereby the 64 bit kernel happily executes both 32 bit and 64 bit code) it should be possible, in theory to use a 64 bit kernel in a completely 32 bit userland.  (2.) the fact that I have a mixture of Linux Mint (which is a prettied up version of Ubuntu that also has all the codecs and plugins needed for desktop use, as well as quite a few custom "mint" applications baked in).  I'd like to be able to demonstrate a 64 bit kernel running a 32 bit userland for the Mint community, where there are a lot of users who could benefit.  As I said, I've been doing my research and I've come across several posts where people are running 64 bit kernels in a 32 bit userland but I haven't found any posts that show specifically how it was done.  If I do figure this out, I will post a howto.  Thanks again guys!

@Kilz:  You're a very experienced Ubuntu user.  What are the drawbacks, if any of using the Server version of the kernel on a desktop system.  I've made this switch on my current workstation and it seems fine.  It does seem a wee bit slower logging in.  Are there any specific benefits to using the Server kernel?  Thanks for your sage advice.

P.S.  I keep going back and forth between 64 bit and 32 bit Ubuntu, but I somehow keep winding up with 32 bit at my primary workstation!  Each new iteration of Ubuntu for amd64 does indeed keep getting better and better and I predict this will eventually become the primary Ubuntu version.

---

### Post by Kilz on 2007-11-05
> **cmost said:**
> Please refer to my signature.  I have a dual core AMD X2 Athlon processor.  It's fully 64 bit compatible.

My primary reasons for wanting to do this are several: 1. for experimentation.  Since it's possible to create a fully 32 bit chroot environment within a 64 bit userland (whereby the 64 bit kernel happily executes both 32 bit and 64 bit code) it should be possible, in theory to use a 64 bit kernel in a completely 32 bit userland.  (2.) the fact that I have a mixture of Linux Mint (which is a prettied up version of Ubuntu that also has all the codecs and plugins needed for desktop use, as well as quite a few custom "mint" applications baked in).  I'd like to be able to demonstrate a 64 bit kernel running a 32 bit userland for the Mint community, where there are a lot of users who could benefit.  As I said, I've been doing my research and I've come across several posts where people are running 64 bit kernels in a 32 bit userland but I haven't found any posts that show specifically how it was done.  If I do figure this out, I will post a howto.  Thanks again guys!

@Kilz:  You're a very experienced Ubuntu user.  What are the drawbacks, if any of using the Server version of the kernel on a desktop system.  I've made this switch on my current workstation and it seems fine.  It does seem a wee bit slower logging in.  Are there any specific benefits to using the Server kernel?  Thanks for your sage advice.

P.S.  I keep going back and forth between 64 bit and 32 bit Ubuntu, but I somehow keep winding up with 32 bit at my primary workstation!  Each new iteration of Ubuntu for amd64 does indeed keep getting better and better and I predict this will eventually become the primary Ubuntu version.

Granted you have a 64bit processor. But I just dont see the purpose behind wanting to place a 64bit kernel in a 32bit install. Granted it might be able to be done, but Why? It will only run in 32bit mode. To me its a lot of work for no gain. The 32bit kernel runs in 32bit mode already.

I really couldnt tell you any drawbacks.  The benefits as I understand them are that on specific server hardware it may utilize resources better.

To me the 64bit version of Feisty was equal to the 32bit version. Thats one reason I ask the reason why you are doing this. If its just to see if it could be done, great. But what benifits are you looking for? What would you tell someone the reason for doing it would be? 

As I se it reason you probably dont see any howto's about it is because there is no benefit to it. Why write a howto to do something that the 32bit version already does.

---

### Post by dcstar on 2007-11-06
> **cmost said:**
> Please refer to my signature.  I have a dual core AMD X2 Athlon processor.  It's fully 64 bit compatible.
........

***"I'm wondering if it's possible to use the amd64 kernel on an ordinary x86 installation"***

Make up your mind as to what you want when you ask a question - you are actually asking if you can run a 32-bit environment on a 64-bit kernel, and others have provided answers for that.

As well, a lot of us don't do forensic examinations of signatures to guess whether the poster is referring to whatever is there or to something else.

---

### Post by x0as on 2007-11-06
I've done it with debain, I see no reason why it can't be done with ubunutu.  

[http://www.debian-administration.org/users/jonesy/weblog/1](http://www.debian-administration.org/users/jonesy/weblog/1)

---

### Post by LowSky on 2007-11-06
> **cmost said:**
> I've done some searching on these forums and Google, but haven't found anything recent.  I'm wondering if it's possible to use the amd64 kernel on an ordinary x86 installation.  I know what many will ask:  "Why not just use the x86-64 bit version of Ubuntu?"  I have several good reasons why I am choosing not to do that (yet.)  If anyone has successfully transplanted the amd64 kernel into an i386 userland, please post a mini howto and any problems you encountered.  I do realize that I will have recompile my nvidia and vmware modules using the amd64 versions of the drivers.  Is there anything else I might have to do (e.g., edit any config files, trick Synaptic / Apt, etc?)  I appreciate any help the community can provide.  Thanks!

What are your Reasons for not using 64 bit ubuntu... 

I can do everything that a 32bit user can do

Save your files and reinstall what you need into 64bit ubuntu

---

### Post by Kilz on 2007-11-06
> **x0as said:**
> I've done it with debain, I see no reason why it can't be done with ubunutu.  

[http://www.debian-administration.org/users/jonesy/weblog/1](http://www.debian-administration.org/users/jonesy/weblog/1)

Since you are in fact forcing the 64bit kernel to run in 32bit mode. What did you get out of it other than saying its done? Did the kernel in fact make use of the extra ram, or did it just say it was there? From your link, you were running a server. What downsides did you have to running the full 64bit install?

---

### Post by x0as on 2007-11-06
I didn't write it, its the guide I followed.  It was a temp fix to a booting problem on a box that couldn't be reinstalled at the time.  The box needed acpi disabling under 32bit which caused other problems but booted & ran fine with a 64bit kernel.

The kernel still ran in 64bit mode, the few 64bit apps we installed we ran fine.  The box had 1GB of ram so ram wasn't a problem anyway.

FWIW the box has since been reinstalled with 64bit Debain.

---

### Post by Kilz on 2007-11-06
> **x0as said:**
> I didn't write it, its the guide I followed.  It was a temp fix to a booting problem on a box that couldn't be reinstalled at the time.  The box needed acpi disabling under 32bit which caused other problems but booted & ran fine with a 64bit kernel.

The kernel still ran in 64bit mode, the few 64bit apps we installed we ran fine.  The box had 1GB of ram so ram wasn't a problem anyway.

FWIW the box has since been reinstalled with 64bit Debain.

No, if the applications were all 32bit, its a 32bit install. So the kernel had to run in 32bit mode to run said 32bit applications. It could not run in 64bit mode. 
But I see you did go back to a 64bit install. :)

---

### Post by psychicist on 2007-11-06
Wow, I see a lot of misinformation in this thread. I don't know if it has to do with ignorance or misunderstanding but I'll add my own insights.

I've got two Sun SPARC based machines that are running 64-bit kernels with 32-bit user lands since they can't even run 32-bit kernels. I wouldn't know why an AMD64 host can't run a 64-bit kernel with a 32-bit user land and I think it would even run better than a 32-bit PAE-enabled kernel (with support for 64 GiB of RAM) since it wouldn't have to page out to get access to more than 4 GiB.

I'm not really an Ubuntu user, even though I have Kubuntu 7.10 installed on my Ultra 10 at the moment, but I'll try to boot a 64-bit kernel with a 32-bit user land and see if everything works as expected. I'll post my findings as soon as I have enough time to find out.

---

### Post by soul_rebel on 2008-03-19
Yes, a lot of disinformation. A 64 bit kernel and 32 bit userland is the best thing for computers with around 4gb of ram. 64bit computing does not offer any big advantages except memory addressing, which comes at the cost of using much more memory for pointers.
Bottom line: most programs in the 64 bit version use one third more memory than the 32 bit version, or worse.
A 64 bit kernel in a 32 bit userland could require some extra libraries and might be a problem for some drivers, especially those that need compiling, so I don't think it will be well supported, but I hope they give it a try.

---

### Post by Kilz on 2008-03-19
> **soul_rebel said:**
> Yes, a lot of disinformation. A 64 bit kernel and 32 bit userland is the best thing for computers with around 4gb of ram. **64bit computing does not offer any big advantages except memory addressing**, which comes at the cost of using much more memory for pointers.
Bottom line: most programs in the 64 bit version use one third more memory than the 32 bit version, or worse.
A 64 bit kernel in a 32 bit userland could require some extra libraries and might be a problem for some drivers, especially those that need compiling, so I don't think it will be well supported, but I hope they give it a try.

I know where to find misinformation :roll: .

---

