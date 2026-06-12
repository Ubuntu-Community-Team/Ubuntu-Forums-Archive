---
title: "The i386 Troll"
date: 2006-07-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Kilz on 2006-07-27
Is it my imagination or does the 64bit section get a lot of 32bit Trolls? People spreading misinformation at best, or downright FUD at worst. 
The 64bit OS has some concerns over the 32bit one. But all Linux systems may have some issues the user must work out. Also 64bit Dapper has gone a long way to eliminating problems. There are howto's and scripts for most of the common problems.
I also think the title of our howto sticky leads some people to think there are real problems. When its inside is all about solving the few issues that we all face on the 64bit side.
The question is, how to best deal with this flood of misinformation? If its people who think they are helping its one thing. But some people only point out the negatives with no solutions. How can we in the 64bit section deal with the FUD?

---

### Post by _simon_ on 2006-07-27
As a 32bit user with a 32bit CPU, if I was to upgrade tomorrow to a 64bit CPU and install 64bit dapper is there anything that might no longer work?

---

### Post by Kilz on 2006-07-27
> **_simon_ said:**
> As a 32bit user with a 32bit CPU, if I was to upgrade tomorrow to a 64bit CPU and install 64bit dapper is there anything that might no longer work?

A valid question, and there may be. But consider it as a change from one distro to another because that's what it is. The 64bit distro is a different animal. Is there some oddball program going to give you problems? Will you have to do some things differently? Most likely yes. But some people come in here posting that Macromedia Flash or Wine isn't available at all. Those are untruths.

---

### Post by jamesford on 2006-07-27
having isntalled 64 bit some weeks ago it sure would have been easier if there was a centralised collection of howtos and a 64 bit ubuntuguide. or maybe there is and i havent found them

---

### Post by professor_b on 2006-07-27
> **Kilz said:**
> How can we in the 64bit section deal with the FUD?

Well, I for one think the resources here are pretty good. I came here first before I installed 64-bit to see what was up, and it helped me knowing what I was getting into going in. So I think we could perhaps point people to those resources. 

I also think it is worth talking about our successes running 64bit rather than only our failures or problems. If people pop in here and see a lot of problems, it is going to confirm the FUD without highlighting the good. I've been running 64bit Ubuntu for a few weeks now, and I love it....

I dunno, just some ideas....

---

### Post by John.Michael.Kane on 2006-07-27
Kilz you say flash is available for 64bit ubuntu? ok how does one go about using flash or any program with out the need for dpkg -i --force-architecture or need for 32bit lib's. most 64bit user's would have some expectation that the software is natively supported with out the need for ch-root or hacked scripts to force install 32bit based programs. for you to call it fud is wrong. Yes you have come up with ways to run programs that "some" user need,however. these programs are not 64bit native they are 32bit forced to run on 64bit. what is needed is for the programs that are not 64bit native to be complied to said architecture.

---

### Post by jdmpike on 2006-07-27
I for one think that 64-bit ubuntu is a great thing.

Almost every problem I have encountered has been lack of knowledge on my part, not a fault of the OS.

There are great how to's that can make almost anything happen out there too (thanks Kilz)

Cheers,

jdmpike

---

### Post by Kilz on 2006-07-27
> **SD-Plissken said:**
> Kilz you say flash is available for 64bit ubuntu? ok how does one go about using flash or any program with out the need for dpkg -i --force-architecture or need for 32bit lib's. most 64bit user's would have some expectation that the software is natively supported with out the need for ch-root or hacked scripts to force install 32bit based programs. for you to call it fud is wrong yes you have come up with ways to run programs that "some" user need,however. these programs are not 64bit native they are 32bit forced to run on 64bit. what is needed is for the programs that are not 64bit native to be complied to said architecture.

How are you going to get Marcomedia/Adobe to release a 64bit version. When we cant even get them to release a 32bit version of the latest version?
[Lets also remember that the]("https://wiki.ubuntu.com/32bitBrowserOnAmd64?highlight=%2832%29") The [spec for a 32bit version]("https://launchpad.net/distros/ubuntu/+spec/32bit-browser-on-amd64") of Firefox with its plugins for 64bit Edgy. Much like having 32bit OpenOffice packaged for 64Bit Dapper. Was ignored. That Multiarch was delayed because we are waiting on Debian. The Firefox spec wasnt ever included despite someone writing a spec for it on the wiki and launchpad. So when someone points out we have to have a work around. Remember that.
The 64bit version is ignored, We have to make howto's and work arounds for functionality, as EYE CANDY is added.

---

### Post by hizaguchi on 2006-07-27
> **Kilz said:**
>  The 64bit OS has some concerns over the 32bit one. But all Linux systems may have some issues the user must work out. Also 64bit Dapper has gone a long way to eliminating problems...

...Lets also remember that the The spec for a 32bit version of Firefox with its plugins for 64bit Edgy. Much like having 32bit OpenOffice packaged for 64Bit Dapper. Was ignored. That Multiarch was delayed because we are waiting on Debian. The Firefox spec wasnt ever included despite someone writing a spec for it on the wiki and launchpad. So when someone points out we have to have a work around. Remember that.
The 64bit version is ignored, We have to make howto's and work arounds for functionality, as EYE CANDY is added.
I'm putting those quotes together to illustrate a point:  Everybody wants a 64-bit OS to go with their 64-bit processor, and the desire is so strong that it is easy to overlook the problems sometimes.  But the problems are there, and they aren't FUD.

Many apps are simply not available in 64-bit versions, and installing the 32-bit binary is not a real solution because it defeats the purpose of a 64-bit OS.  Sometimes this is becasue they are proprietary, but sometimes (like you said above) it is just because there isn't enough focus on the 64-bit OS.  In a week of light use, I've come across a few apps already that just aren't in the 64-bit repos.  Other apps, like the synaptics driver, are there but don't work correctly.

The bottom line is, 64-bit Dapper is very functional and fast, but lacks the polish of the 32-bit version.  That isn't a bad thing.  32-bit Linux has been around for a LONG time, while 64-bit is very new and rapidly changing.  You can't really put together an OS every 6 months and have any hope of it being 100% polished and trouble free.  The target is moving too fast.  Heh, I'm still impressed that the thing even boots.  And it definately works better than 64-bit Windows. :D

---

### Post by Kilz on 2006-07-27
> **hizaguchi said:**
> I'm putting those quotes together to illustrate a point:  Everybody wants a 64-bit OS to go with their 64-bit processor, and the desire is so strong that it is easy to overlook the problems sometimes.  But the problems are there, and they aren't FUD.

Many apps are simply not available in 64-bit versions, and installing the 32-bit binary is not a real solution because it defeats the purpose of a 64-bit OS.  Sometimes this is becasue they are proprietary, but sometimes (like you said above) it is just because there isn't enough focus on the 64-bit OS.  In a week of light use, I've come across a few apps already that just aren't in the 64-bit repos.  Other apps, like the synaptics driver, are there but don't work correctly.

The bottom line is, 64-bit Dapper is very functional and fast, but lacks the polish of the 32-bit version.  That isn't a bad thing.  32-bit Linux has been around for a LONG time, while 64-bit is very new and rapidly changing.  You can't really put together an OS every 6 months and have any hope of it being 100% polished and trouble free.  The target is moving too fast.  Heh, I'm still impressed that the thing even boots.  And it definately works better than 64-bit Windows. :D

I think that the future of 64bit in the next 5-10 years is going to be multiarch. Running both 32bit and 64bit. A lot of distro's are already multiarch. AMD 64bit processors have the capability to run both, its in the hardware. So saying that everything must be 64bit is imho wrong. Would I like it? Yes in a perfect world thats how it would be. But if I can get 32bit applications to work and install easily while waiting for 64bit versions it isnt a problem. But IMHO 64bit is a second class citizen. We have to make work arounds to get common functionality as eye candy is added. Heck we cant even get a few 32bit packages made that will install.
Have I tried, yes, I have. I think my howto's prove that all thats needed is the packaging to install the aplications. Unfortunatly I cant figure out how to do it myself(not for lack of trying) or there would be debs insted of howto's. But it is possible,. 32bit OpenOffice proves it is possible to make 32bit packages that will install to 64bit.

---

### Post by hizaguchi on 2006-07-27
But the point of the thread initially was
> **Kilz said:**
> The question is, how to best deal with this flood of misinformation? If its people who think they are helping its one thing. But some people only point out the negatives with no solutions. How can we in the 64bit section deal with the FUD?
I can't discuss the technical issues very well because they're ove rmy head, but I do understand where the FUD and disinformation come from: high expectations/hopes meeting the reality of young technology

---

### Post by Kilz on 2006-07-29
> **hizaguchi said:**
> But the point of the thread initially was

I can't discuss the technical issues very well because they're ove rmy head, but I do understand where the FUD and disinformation come from: high expectations/hopes meeting the reality of young technology

More like the technology meeting people who don't know computers. Ubuntu is supposed to be easy to use, so it tends to attract people who don't have a clue sometimes. They use the 32bit version, where a lot of work has been done. Then they think "If the 32bit version is this easy the 64bit version will be to".
Well surprise, the 64bit version is like a lot of other Linux distros. It isn't easy, it isn't handed to you in a GUI, you have to know how to use a cli. You have to do some manual setup.
I read people say "Ill use it when its ready". That isn't going to happen without more people using it. Development is being done on the 32bit version because people are using it. When we do get work done on the 64bit version its nice. But IMHO it isn't what needs to be done.
An example is 64bit OpenOffice. The 32bit version runs ok on amd64. We really don't need it right now. What we need is a browser with plugins that are easy to install. What we need is wine to be installable. What we need is a media player that works like the 32bit versions. For the most part it would be ok if they were 32bit until they got around to 64bit versions. But instead we are left with holes the user has to fill.
The holes are fill able , its just not going to be able to be done by Joe Windows. Who expects everything to "just work". People who don't want to spend an hour learning something. They expect its going to work, for free! Not one of them says "What can I do to make it better". Its just "Ill give up on this so I don't have to put in any effort."
Sad to say, I'm sick of Joe Windows!

---

### Post by penvzila on 2007-02-20
Actually, the 64-bit version pretty much worked out of the box for me on my new laptop.  The subsequent kernel update that got installed broke things, so I spent most of today fixing it.  Whereas automatic updates are nice in Windows, I'd stay the hell away from them on Ubuntu for the time being.

---

### Post by Kilz on 2007-02-20
> **penvzila said:**
> Actually, the 64-bit version pretty much worked out of the box for me on my new laptop.  The subsequent kernel update that got installed broke things, so I spent most of today fixing it.  Whereas automatic updates are nice in Windows, I'd stay the hell away from them on Ubuntu for the time being.

Yes sometimes updates do break things. What exactly did this one break? 

Also this is one old thread, I remember it now. It looks like the i386 trolls are still around though.

---

### Post by penvzila on 2007-02-20
> **Kilz said:**
> Yes sometimes updates do break things. What exactly did this one break? 

Also this is one old thread, I remember it now. It looks like the i386 trolls are still around though.

My soundcard and wireless card stopped working.  Apparently the wireless thing is a bug in some dependency.  The update before this most recent one screwed up my NVIDIA drivers, but that was on a 32-bit machine.  I've figured out how to install the NVIDIA drivers now so that a kernel update doesn't remove them.

---

