---
title: "What's my incentive behind running 64 bit?"
date: 2006-03-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by harisund on 2006-03-19
Hello  people

So I got this new Compaq Presario V2000z which has an ATI Radeon Xpress 200M video card, Conexant AMD Audio sound card, a Broadcomm internal wireless card and other hardware components.. 

The processor is AMD Turion 64 ML  28. 

Now, my question is, what benefits does a 64 bit processor (or OS) offer to an average user? To a student?

I run 32 bit Windows, and am trying to get Ubuntu on it. Still some work needs to be done. 

But my question is, what is the trade of? How does 64 bit truly benefit me? What do I gain? 

Or would you advise I wait for a while till the 64 bit architecture becomes more common, drivers start coming out (specially for Linux 64 bit !), plugins and all that yadda yadda are available and so on.. 

What is your opinion? You 64 bit users out there could you please advice me on what you find different, or new that 32 bit users don't have? 

Thanks !

---

### Post by el3ktro on 2006-03-19
I'd definitely recommend you to install 32bit Ubuntu. 64bit won't give you any real benefits unless you nee more than 4 GB RAM or if you do some _really_ heavy computing, or if you really _need_ to deal with 64bit numbers for some reason. But right now, you won't be able to play some codecs (WMV, Quicktime etc.) you won't have Flash, and drivers _can_ be a problem.

Tom

---

### Post by John Jason Jordan on 2006-03-19
[QUOTE=harisund]Hello  people
So I got this new Compaq Presario V2000z which has an ATI Radeon Xpress 200M video card, Conexant AMD Audio sound card, a Broadcomm internal wireless card and other hardware components.. 
The processor is AMD Turion 64 ML  28. 
Now, my question is, what benefits does a 64 bit processor (or OS) offer to an average user? To a student? ... my question is, what is the trade of? How does 64 bit truly benefit me? What do I gain? 
Or would you advise I wait for a while till the 64 bit architecture becomes more common, drivers start coming out (specially for Linux 64 bit !), plugins and all that yadda yadda are available and so on.. 
What is your opinion? You 64 bit users out there could you please advice me on what you find different, or new that 32 bit users don't have? Thanks ![/QUOTE]
I am also a student, and I have a slightly similar laptop (Compaq R3240 laptop). It has nVidia graphics instead of ATI, but most of the other stuff is the same. I installed lots of different distros before finding and settling on Ubuntu-64. 

Why did I go 64-bit? Well, for one thing I am not entirely dependent on this laptop. I still have my Windows 2000 desktop if something absolutely cannot be made to work on the laptop. As for another thing, I wanted to learn Linux. I felt that a baptism by fire might be a good way to do it, and cutting edge 64-bit installation would make it all the hotter. And finally, I was hoping that it would improve performance.

The results are mixed. It has succeeded very well in the "leaning Linux" goal. However, the speed is not that much greater, although sometimes it is for some things. For example, if I am doing something CPU-intensive, it is a definite plus. But if I am doing something disk-intensive, forget it. The disk is the bottleneck regardless of how fast the CPU is running.

As for whether everything can be made to work, yes it can. It took me a week to figure out how to get wifi working with ndiswrapper (I also have the Broadcom chip). But I think that would have been necessary with 32-bit anyway. Broadcom simply requires ndiswrapper, and there's a serious learning curve to ndiswrapper. The only thing I had to do that I could have avoided with the 32-bit version was installing a 32-bit chroot environment for Adobe Reader 7.0, Firefox, Flash and RealPlayer. Firefox worked just great in the 64-bit world, but I couldn't get any of the above plugins to work. Again, it was a bit of a learning curve to install the 32-bit chroot environment, but worth it for the knowledge and experience.

Oh, and there is one other advantage. When someone at the university sees my computer screen and says "that isn't Windows is it?" I can smile smugly and say, "no, this is Linux -- Windows is so far behind that there isn't even a 64-bit version of it for laptops yet." 

But YMMV, etc. You asked for opinions, and that's mine. :)

---

### Post by Steve1961 on 2006-03-19
I tried the 64 bit version of Hoary but installed 32 bit breezy when it came out because I wanted things like flash and codecs to just work.  Can't say I've noticed much of a speed difference and I'll probably stick with 32 bit when Dapper is officially released.

---

### Post by Bokonon on 2006-03-19
I would go with 32 bit as well.  A lot more users = a lot more help and even some of the hard core 64 bit guys don't have everything running on AMD64.

I am going to wait a bit before going to Dapper because I want to feel out how everyone else is doing with 64 bit.  I definately want to move over, but it was a PITA getting some stuff to run and since I want my Ubuntu box to be my personal desktop, it just wasn't worth it.  No major problems since going to 32 bit (k7-smp) kernel.

I am steering clear of Vista for quite a while, but I assume when Vista comes out, there will be more support for 64 bit systems in general which should help everyone getting their systems setup the way they would like--including us.  Until that day comes, I will be running 32 bit Ubuntu.

---

### Post by Jason_25 on 2006-03-19
If you can live without flash and wmv, go with the 64 bit version.  I feel like not having to see flash is a blessing.

---

### Post by harisund on 2006-03-20
Hmm.. thank you for your opinion people.. 

Personally I agree to some extent with John Jason Jordan ... about the nice "No, it is not Windows feeling". As a student too, I agree with a lot of other aspects, such as the laptop not being the main platform (yes, I have university computers and work computers, and a desktop for the vacation time too.) Regarding the learning curve, yes, there definitely is one. But I know how to work my way through ndiswrapper for sure .. and I know it works on my machine since I got it working with 32bit mepis.. 

And I am pretty sure you must have learnt a lot while chrooting too !

Hmmm.. ok thanks again .. I think  my final decision will be to wait for a while and stick with 32 bit for now ... .

---

### Post by Jason_25 on 2006-03-20
Just wanted to add, I have gotten all but the above (flash, wmv) working and I have never done a chroot and barely know what it is.

---

### Post by drl on 2006-03-20
Hi.

If you have the time, install them both and then choose.  I did that and I saw that there were some visual differences, probably because of different driver versions.  For that aspect I liked the 32-bit better.  The updates in both cases seemed the same.

The classical method for choosing an aspect of a solution is to have a sample of something you really need -- for example, an application.  Then look for for a platform (hardware, OS, desktop, etc.) on which it runs the best and with which you are comfortable.

In the case of Ubuntu/32 and /64, the installs are a bit time-consuming, but otherwise they were painless for me.  If you have the space, for example, you could try re-compiling a kernel on a test install (*test *because you would not want to screw up your production system).  That was where I noticed the biggest difference when I got a 64-bit box some time ago (OK, a *long *time ago with a DEC Alpha workstation) ... cheers, drl

---

### Post by harisund on 2006-03-20
Thank you again for your feedback. 

I think I agree with the install both and choose option. After all, isn't Linux all about choice? 

Recompiling the kernel.. that would be an awesome thing to do, but again, your "if you have the time" is a big if. Probably will give it a try over the Spring break or something like that. 

And also, maybe the other posters here are right. In my laptop, I can live without flash and codecs and whatever it is I can not live with. I do have other machines for that purpose, and my university's Windows machines are something I can always remote desktop into. 

Ok .. that's it then .. I am going to have 32 till my next big break (which I guess is Spring break) and over that time I am going to try a 64 bit install and see how things go ... 

Thanks again !

---

### Post by John Jason Jordan on 2006-03-20
[QUOTE=harisund]Ok .. that's it then .. I am going to have 32 till my next big break (which I guess is Spring break) and over that time I am going to try a 64 bit install and see how things go.[/QUOTE]
I think that's the best decision. One installation you can count on and the other to mess around with. And spring break is also a good idea. I had a whole bunch of things I was going to do to my computer over spring break, but it turns out that my last exam is this Wednesday and Thursday I have a 6:30 am flight to Mexico. I have never estado en México con computadora, so I'm not sure how many of the projects are going to happen. Still, I know that nada is going to happen until spring break! (Well, except for reading Ubuntu forums, 'cause that is just *required*.)     :)

Good luck!

---

