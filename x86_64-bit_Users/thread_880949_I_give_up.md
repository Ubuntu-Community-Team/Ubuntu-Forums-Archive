---
title: "I give up"
date: 2008-08-05
forum: x86 64-bit Users
---

### Post by jaca on 2008-08-05
I have been trying to install Ubuntu on my desktop computer for months now. I even send a bug report but no one would listen. There is a problem with the live CD for, at least certain AMD 64 systems.
I am running an ASUS A8V with Atlon(tm) 64 processor 3000+ with dual channel DRAM 128 
Every time I download the live CD image, and burn it into a CD it will give between 25 and 31 errors when checked, wouldn't proceed to install if it doesn't pass the check. I downloaded the alternate live CD, checked that the MD5sum was correct, it is. 
I burned it into a CD (I have used 3 different brands of blank CD media, so do not blame it). So, when I check the CD, it stops with a message that reads more or less like this:
./dists/hardy/main.binary-amd64/Packages.gz file failed the MD5 checksum verification.
Then, I go into my Debian system, and check if this is true, and it isn't. I can check the MD5 checksum of the mentioned file on the CD, and extract that file from the CD image, the checksum gives the same result and, what is more, the same result listed in the md5sum.txt of the live CD. 
I did this with both ECC option enabled and disabled, made a memory check, you name it.
So, either there is a problem with the live CD of Ubuntu is not for my desktop, so I can no longer recommend Ubuntu, despite it is working nicely in my laptop.

---

### Post by stchman on 2008-08-05
> **jaca said:**
> I have been trying to install Ubuntu on my desktop computer for months now. I even send a bug report but no one would listen. There is a problem with the live CD for, at least certain AMD 64 systems.
I am running an ASUS A8V with Atlon(tm) 64 processor 3000+ with dual channel DRAM 128 
Every time I download the live CD image, and burn it into a CD it will give between 25 and 31 errors when checked, wouldn't proceed to install if it doesn't pass the check. I downloaded the alternate live CD, checked that the MD5sum was correct, it is. 
I burned it into a CD (I have used 3 different brands of blank CD media, so do not blame it). So, when I check the CD, it stops with a message that reads more or less like this:
./dists/hardy/main.binary-amd64/Packages.gz file failed the MD5 checksum verification.
Then, I go into my Debian system, and check if this is true, and it isn't. I can check the MD5 checksum of the mentioned file on the CD, and extract that file from the CD image, the checksum gives the same result and, what is more, the same result listed in the md5sum.txt of the live CD. 
I did this with both ECC option enabled and disabled, made a memory check, you name it.
So, either there is a problem with the live CD of Ubuntu is not for my desktop, so I can no longer recommend Ubuntu, despite it is working nicely in my laptop.

What burning program on Windows (I am assuming you are using Windows to create the LiveCD) to create the CD.

I recommend Infrarecorder.

[http://infrarecorder.sourceforge.net/](http://infrarecorder.sourceforge.net/)

Also follow my tutorial on how to create an Ubuntu CD.

[http://www.stchman.com/create_cd.html](http://www.stchman.com/create_cd.html)

---

### Post by jaca on 2008-08-05
> **stchman said:**
> What burning program on Windows (I am assuming you are using Windows to create the LiveCD) to create the CD.

I recommend Infrarecorder.

[http://infrarecorder.sourceforge.net/](http://infrarecorder.sourceforge.net/)

Also follow my tutorial on how to create an Ubuntu CD.

[http://www.stchman.com/create_cd.html](http://www.stchman.com/create_cd.html)


Sorry, but the last 100 times I tried I was burning the CD on Debian using GnomeBaker, so you were guessing wrong. It is true that I tried to do it another 100 times burning it on windows with Nero, with the same result. The only thing I got out of this is that I wasted around 200 blank CDs.
I am installing openSUSE. I don't like the fundamentalism of Debian, well... I don't like any fundamentalism and I grew tired of it.

---

### Post by loboc on 2008-08-05
If you are doing a 64 bit install dont you need the alternate cd

---

### Post by Friqenstein on 2008-08-05
Perhaps you have an error during download. It's not always caught by MD5 checks. I had a problem similar to this with a Gentoo LiveCD once.

Can't always chalk it up to the OS or the burning program.
Just a thought.

---

### Post by cariboo on 2008-08-05
If i had created that many coasters, I would have throw my cd burner as far as I could and tried a new one.

Jim

---

### Post by tuxxy on 2008-08-05
31 errors damn, are you using the ubuntu mirrors or torrents for this download

---

### Post by guinness1759 on 2008-08-05
Why not order the cd from Ubuntu?

[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

---

### Post by Yellow Pasque on 2008-08-05
If the CD drive is making a lot of coasters, it could have read errors too. If so, it could be a bad driver (this IS VIA we're talking about), a bad IDE cable or a bad IDE controller.

---

### Post by stchman on 2008-08-06
> **jaca said:**
> Sorry, but the last 100 times I tried I was burning the CD on Debian using GnomeBaker, so you were guessing wrong. It is true that I tried to do it another 100 times burning it on windows with Nero, with the same result. The only thing I got out of this is that I wasted around 200 blank CDs.
I am installing openSUSE. I don't like the fundamentalism of Debian, well... I don't like any fundamentalism and I grew tired of it.

Is it POSSIBLE that your CD burner is bad.  They do go bad.

---

### Post by alt3rn1ty on 2008-08-06
I just had a similar problem setting up the desktop, and can concur with Stchman a dodgy CD/DVD drive may be your problem. I was lucky to have a second combo drive which I could change my bios to have as the boot cd drive, then did a fresh download of the ubuntu iso, burned at a very low speed with verify on completion, then just for good measure after booting from the ubuntu iso did its own disk verify before finally rebooting and going through the guided to free contiguous space option.

Unfortunately for me previously I had done all the usual preps... partition free space, defrag C drive, unplug external devices... then got half way through the guided ubuntu and it failed with an error. On rebooting not only was ubuntu not installed but all four xp users in my house had their OS trashed
:lolflag: It was about time I did a fresh re-organise of XP anyway.

So it turns out my problem was the top CD/DVD drive, it seems fine for doing the normal checking of game installation cd's when people are playing (but now I wonder how many hidden errors there are within previous game installations which havent shown up maybe because they only affected graphics or sound data), or for burning photo cds, but for critical installs I wont trust it again.

Edit: On XP I use Nero (quite an old oem version with the 6.6.1.4 patch), on linux I use K3B
Edit2: And just to be sure I changed my download location, previously used either oxford or kent, for latest I used canonical.

---

### Post by jaca on 2008-08-06
Thank you guys, but you have it all worng.
1.- I did order one Ubuntu CD, and I got it some 3 weeks later: exactly the same result.
2.- Please read. It could hapen that the CD driver has a problem, yesss, it could hapen. But it hasn't, why do I know? Because I said that I checked in my late Debian System the md5sum of the individual files, if the CD drive works to read the files correctly withing Debian (and Windows by the way), it works, what it doesn't work is the live CD.
You are doing like most computer geeks, do not listen, but I am use to it. I reported a bug time ago and "because ubuntu is so great", there must be a fault of anything else, despite everything else working like a charm other wise (I just installed openSUSE and worked perfectly). There are lots of reports of the same problem on this forums and other places on the net, yet there must be a prfblem with the downloads, the CD drive, etc., anything else but properly investigating it. Sorry I am not such a good programmer and I am not so skilled ad programming installer aplications.

My guess? My guess is that whoever created the precedure that checks the md5 checksums of the live CD didn't properly test it at least on AMD64 machines, it has a bug, and gives unpredictable results, most of the time the results wouldn't match the md4 sums in the control file, and wouldn't let you proceed with the installation. This explains why the same CD can give you a different number of errors when is checked several times, the procedure do not yeld the same checksum every time. And that is why the same CD, by chance can give you no erros once, as it hapened to me on my laptop (another AMD64 system) and get to install it, as it eventually happened to me in the forementioned laptop. Guessing further, I suspect that it is an issue with memory handling.
Anyway, this all look very amateuristic, and I don't think ubuntu can be recomended as this stage for serious jobs.

---

### Post by Growbag on 2008-08-06
Good riddance I say!

He has 3 posts to his name in total and all of them were to whine, there was not one actual call for help.

Plus a bad attitude, quote: "You are doing like most computer geeks, do not listen, but I am use to it".

He stuffed up 200 CDs?

You would think that anyone with an ounce of intelligence would think to themselves: "OK, I've done this the same way 3 times already, something is not right here.  Maybe I should ask for help, or try another approach to the problem".

But no, he continued to feed CDs into the drive and make coasters.

It reminds me of Homer Simpson when he's trying to take hot donuts out of the deep fryer with his bare hand, ouch, ouch, ouch, ouch, ouch!

Keeps doing the same thing over an over again.

Oh go on, tell me that you said "doh" after each one, please, at least it would explain the problems.

And please don't try openSUSE, it's rubbish and it has a nasty colour on their desktop, and it will infect your computer with viruses, and your dog will die, and your car will mysteriously stop working, you will lose your job, and your hair, your girlfriend will think you're gay and dump you, it's communist, they are in an evil deal with Microsoft, it's a corporate sponsored distro, their logo is a lizard and we all know that is a symbol of the devil, ....

...quick help me out here, think of more "good" reasons why he should stay away from Linux, it will save us all a lot of headaches!

But what gets me the most is that he keeps coming back to read all the replies to his rants, I wonder why?

Seems like the same old story, the wittwe boy throws his toy on the floor and sticks his bottom lip out:  "I'm not playing anymore, it's not fair, I never win and they all cheat", wah, wah, wah.


...oh look out, here he comes again.....:rolleyes:

---

### Post by jaca on 2008-08-06
> **Growbag said:**
> Good riddance I say!

He has 3 posts to his name in total and all of them were to whine, there was not one actual call for help.

Plus a bad attitude, quote: "You are doing like most computer geeks, do not listen, but I am use to it".

He stuffed up 200 CDs?

You would think that anyone with an ounce of intelligence would think to themselves: "OK, I've done this the same way 3 times already, something is not right here.  Maybe I should ask for help, or try another approach to the problem".

But no, he continued to feed CDs into the drive and make coasters.

It reminds me of Homer Simpson when he's trying to take hot donuts out of the deep fryer with his bare hand, ouch, ouch, ouch, ouch, ouch!

Keeps doing the same thing over an over again.

Oh go on, tell me that you said "doh" after each one, please, at least it would explain the problems.

And please don't try openSUSE, it's rubbish and it has a nasty colour on their desktop, and it will infect your computer with viruses, and your dog will die, and your car will mysteriously stop working, you will lose your job, and your hair, your girlfriend will think you're gay and dump you, it's communist, they are in an evil deal with Microsoft, it's a corporate sponsored distro, their logo is a lizard and we all know that is a symbol of the devil, ....

...quick help me out here, think of more "good" reasons why he should stay away from Linux, it will save us all a lot of headaches!

But what gets me the most is that he keeps coming back to read all the replies to his rants, I wonder why?

Seems like the same old story, the wittwe boy throws his toy on the floor and sticks his bottom lip out:  "I'm not playing anymore, it's not fair, I never win and they all cheat", wah, wah, wah.


...oh look out, here he comes again.....:rolleyes:

Sorry I heart your feelings, but the thing stands.
1. - I sent a bug report, nothing was done about it.
2. - I requested a live CD that was sent to me, same problem, between 25 and 31 file errors every time is checked. Mind the non constant number of errors, meaning that some files give an error only every now and then.
3. - I did the checks that had to be done before the live CD was released and they weren't done. THERE IS A BUG IN THE INSTALLATION CD for AMD64, you like it or not. And yet, nobody is listening, is this a reliable distribution? I doubt it. 
4.- I check all the threads with the same issue, and all responses were the same: there must be something wrong with the downladed file, with the CD drive, etc. Well:
4.1 there is nothing wrong with the download since the checksum is correct.
4.2 there is nothing wrong with the CD drive since, withing LINUX, I can read the files, compute the md5 checksum and they give the correct result, both directly from the CD and extracting the files from the CD image.
5. You may say a lot about my intelligence or lack of it, but what can it be said about this community that can have an issue like this for at least two years and keep blaming the rest of the world for it?
Yeah, you may be right about openSUSE and viruses and all that, which I sincerely doubt it, but it has an obvious advantage when it comes to my machine: it works!, I only needed to try once and is installed. Besides, I like the graphics, I must have better taste than you.

---

### Post by jerome1232 on 2008-08-06
> **jaca said:**
> Thank you guys, but you have it all worng.
1.- I did order one Ubuntu CD, and I got it some 3 weeks later: exactly the same result.
2.- Please read. It could hapen that the CD driver has a problem, yesss, it could hapen. But it hasn't, why do I know? Because I said that I checked in my late Debian System the md5sum of the individual files, if the CD drive works to read the files correctly withing Debian (and Windows by the way), it works, what it doesn't work is the live CD.
You are doing like most computer geeks, do not listen, but I am use to it. I reported a bug time ago and "because ubuntu is so great", there must be a fault of anything else, despite everything else working like a charm other wise (I just installed openSUSE and worked perfectly). There are lots of reports of the same problem on this forums and other places on the net, yet there must be a prfblem with the downloads, the CD drive, etc., anything else but properly investigating it. Sorry I am not such a good programmer and I am not so skilled ad programming installer aplications.

My guess? My guess is that whoever created the precedure that checks the md5 checksums of the live CD didn't properly test it at least on AMD64 machines, it has a bug, and gives unpredictable results, most of the time the results wouldn't match the md4 sums in the control file, and wouldn't let you proceed with the installation. This explains why the same CD can give you a different number of errors when is checked several times, the procedure do not yeld the same checksum every time. And that is why the same CD, by chance can give you no erros once, as it hapened to me on my laptop (another AMD64 system) and get to install it, as it eventually happened to me in the forementioned laptop. Guessing further, I suspect that it is an issue with memory handling.
Anyway, this all look very amateuristic, and I don't think ubuntu can be recomended as this stage for serious jobs.

Does anyone else smell a troll?

---

### Post by Vishal Agarwal on 2008-08-06
> **guinness1759 said:**
> Why not order the cd from Ubuntu?

[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)


I am with guinness1759,

Order a CD to UBUNTU, and install from that. It will surely help. I have installed Ubuntu in my ASUS F5RL, without any problem, Except that the wireless card. that was also solved using this Post.
[[COLOR="Blue"]How To:MadWifi Support for AR2425 (AR5007EG) on 64bit Ubuntu !!![/COLOR]]("http://ubuntuforums.org/showthread.php?t=816780")

Don't be dishearten. After using the UBUNTU, you will dislike other OS.

---

### Post by jaca on 2008-08-06
> **Vishal Agarwal said:**
> I am with guinness1759,

Order a CD to UBUNTU, and install from that. It will surely help. I have installed Ubuntu in my ASUS F5RL, without any problem, Except that the wireless card. that was also solved using this Post.
[[COLOR="Blue"]How To:MadWifi Support for AR2425 (AR5007EG) on 64bit Ubuntu !!![/COLOR]]("http://ubuntuforums.org/showthread.php?t=816780")

Don't be dishearten. After using the UBUNTU, you will dislike other OS.

I did that, I ordered a CD from ubuntu, I got it one month ago. AND THE RESULT WAS THE SAME!!, I already said it, another proof that people here do not listen, or do not read.
Some guys here smell a troll, fine, go on, bury your heads in the sand. There is a bug in the process that checks the CD that has to do with memory management, it gives more errors for the same CD in systems with 1Gb of RAM (my desktop) than on those with 2Gb of RAM (may laptop).
But go on, blame me, call me an idiot a troll or whatever. Blame the CD drives, blame the CD media. Ubuntu is great bless its name and anything else is a blasphemy, from what I saw this problem has been around for at least two years, I read all the threats and I consider that there is no point of asking for help to get replies like the ones here that exactly the same as the ones posted two years ago: check your download, check your CD drive, use the alternate CD, etc.
This threat is just to let you know, or anyone else that comes across the same problem: is not your fault, is not your CD drive fault, is not the downloaded file fault, THERE IS A BUG.
The community wants to listen? fine, it doesn't, fine as well.

---

### Post by Vishal Agarwal on 2008-08-06
Be patient and cool. Pls Don't blame the community. 

What Os u are using ? are u not getting the problem in that OS ?

There can be several reasons for errors. It can be H/W or S/W fault/Bug.

---

### Post by alt3rn1ty on 2008-08-06
Guys I wouldn't be so quick to jump on Jaca as a potential troll, who is just out to downface Ubuntu.

I think he has a genuine concern there is a bug, (and excessive effort to try the OS before jumping to Suse) and as such (for my own curiosity and future reference) how do we go about reporting such (ie the correct channels) and how would you normally expect to receive feedback on bug reports, obviously it would take time.

@ Jaca, who did you report this to. Not meaning to question your actions, I am a noob in the linux world myself.

---

### Post by jaca on 2008-08-06
> **Vishal Agarwal said:**
> Be patient and cool. Pls Don't blame the community. 

What Os u are using ? are u not getting the problem in that OS ?

There can be several reasons for errors. It can be H/W or S/W fault/Bug.

I have a double boot system with Windows XP and, formerly Debian now openSUSE, no problems with any of those operating systems, burning CDs DVDs or reading them. Yet, I don't know what this has to do with it, the problem appears when you boot the system from the live CD, so no OS involved but the one loaded from the CD, and you click on check CD for defects, both with the standard and the alternate CD. It didn't happened to me only, it happened to many others, do a search in google and  you'll see, that is why a blame the community, since I do not know the structure of how the jobs were carried out:
There is obviously a problem hanging out for quite some time now that affect 64 bits machines, and as time goes on, nobody bothers to check on it, just the same old replies: the download went wrong, write at a lower speed, use another CD burning software, in summary all conspires against an smooth ubuntu installation on amd64 machines: the software vendors, the CD drives manufacturers, the state of the net, all but the obvious. 
Could you imagine that someone builds a car and gets broken every time it is taken to the road and them blaming the state of the road, the poor handling of the car by the driver, etc.? this is what is happening with the live CD for amd64 in this community, anything but checking whether there is something wrong with it.

---

### Post by jerome1232 on 2008-08-06
Well if I spoke out of turn I apologize for it. I see no link to a launchpad bug (could you link it?)

btw I thought OpenSuse+KDE 4 was pretty nice, was the first time I had any like for kde, I didn't feel like getting use to the red hat way of doing things since I'm pretty comfortable with the debian way though. I need to put that in a VM and fiddle with it some more.

So if I take this right the problem is 'check cd for defects' isn't working correctly on your amd64 machine for amd64 live cd's. Whether it is burned or from the factory, yet the cd checks out fine using other forms of integrity checking. Did this happen with 32 bit cd's as well or  were those never tested?

btw I am using athlon 64 3700+ 8.04 x86_64 and check cd does work for me, it's an abit motherboard.

---

### Post by forger on 2008-08-06
Hey Jaca, I am using Ubuntu amd64 (64-bit) and installed it in about 60 computers (friends and several companies) with about 10 different CDs of 64-bit Ubuntu.

I'm sorry about your experience, I'm also sorry that some people above didn't read the [Ubuntu Code of Conduct]("http://www.ubuntu.com/community/conduct") (you included?).. I might be wrong about this but anyway, on to solving this problem.

I'd really hate to see you go for this problem, so:
1. Where did you download your Ubuntu from?
Could it be that you downloaded it from a wrong place? There are daily builds, which most of the time don't work!

Head to: [http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/)
You have ubuntu 8.04**[COLOR="Red"].1[/COLOR]** (.1 has several bugs fixed)

This is the link to the iso cd image: [http://releases.ubuntu.com/hardy/ubuntu-8.04.1-desktop-amd64.iso](http://releases.ubuntu.com/hardy/ubuntu-8.04.1-desktop-amd64.iso)
Link to torrent: [http://releases.ubuntu.com/hardy/ubuntu-8.04.1-desktop-amd64.iso.torrent](http://releases.ubuntu.com/hardy/ubuntu-8.04.1-desktop-amd64.iso.torrent)
Link to md5sum: [http://releases.ubuntu.com/hardy/MD5SUMS](http://releases.ubuntu.com/hardy/MD5SUMS)

The md5sum for file ubuntu-8.04.1-desktop-amd64.iso is:
```
b78ef719e3361e726b89bab78c526ad0
```

2. You said you burned it with gnomebaker in debian. I wouldn't recommend old versions of such applications, and debian releases are a bit late and more server-wise (my opinion).
Do you use debian lenny (testing)? Try **brasero** or **k3b** (I recommend k3b, much better and you need some extra kde libraries in order for it to run in gnome)
```
apt-get install k3b
```

3. Burn using **really low speeds** (1x or 4x for CD)! This gives you an extra safe step to burn the CD correctly.

4. You said you checked the MD5 in debian.
a) Did you check within debian the md5 of the cd image?
b) Did you place in the cd you burned and used the md5sum inside the cd to check its files?

 As mentioned above, I also sense this is a hardware-related failure, in other words, your cd/dvd writer might be failing. How old is your cd/dvd-writer?

I urge you to burn the iso image (also low 1x or 4x speed) in another cd/dvd drive at a friend's place, or borrow your friend's cd/dvd drive and replace yours and try installing it again :)

5. Your CDs might be bad, try buying Verbatim or some other brand? Try the ones that come in their own case, don't buy a "cake" bundle.

6. Please be polite, people might be open-source and close-minded at the same time ;)
If everything else fails try posting a bug about it:
[https://launchpad.net/ubuntu/+filebug](https://launchpad.net/ubuntu/+filebug)

---

### Post by Vishal Agarwal on 2008-08-06
> **jaca said:**
> I have a double boot system with Windows XP and, formerly Debian now openSUSE, no problems with any of those operating systems, 

Dear Jaca,

To ask about other Os was that if other OS are working fine, means there could be a S/W bug in the UBUNTU OS. Although UBUNTU is working fine for me, but may be not for you. All your posts says that u have spend enough time and effort to install the system, but u were not successful. in this condition I will not suggest you any more R&D, because if I could be in your position, I would have not done this much of efforts.

Also U have mentioned that UBUNTU is working fine in your laptop, that means u are not new to UBUNTU installation. So I can not suggest U making manual partitions, checking SWAP, or going for least package installations etc.

Now it's all upon to U that how would u like to deal with your computer.

Wish u all the best for your efforts.

---

### Post by jaca on 2008-08-06
> **alt3rn1ty said:**
> Guys I wouldn't be so quick to jump on Jaca as a potential troll, who is just out to downface Ubuntu.

I think he has a genuine concern there is a bug, (and excessive effort to try the OS before jumping to Suse) and as such (for my own curiosity and future reference) how do we go about reporting such (ie the correct channels) and how would you normally expect to receive feedback on bug reports, obviously it would take time.

@ Jaca, who did you report this to. Not meaning to question your actions, I am a noob in the linux world myself.

I reported it through this website in the bug reporting database, I need to switch OS to check on the emails I got form some one, whose name I do not remember, I am now busy setting up openSUSE. Next time I swetch I let you now all the details. He esentially asked me where did I downloaded the iso image from, I told him that I downloaded from three different repositories in the UK, since I didn't have any thing else to add, and he didn't find it useful he decided to close the bug report.
If some one can search in the bug database, he can find the report, I guess it was a couple of months back, this was before I got the life CD on the mail from Ubuntu. I let ir rest for a while since I was busy doing other things, thinking that now, with the CD from ubuntu I would have no problems. To my surprise when I tried to install it from the CD I got I had the same problems. So, I gave it a few tries. Then I read on another threat someone recommending using the alternate CD, so I downloaded it, same result. This time I checked ths md5 checksums with the result that I already commented: I got the right checksums when i did it withing Debian, for the files that gave md5 checksum errors in the installation process, and compared them with the ones in the the live CD (I had already checked the md5 for the iso image agais the one reported in the ubuntu website). In any case, according to the md5sum command and the documentation there are no errors on the CD, the errors only appear when checked with the live CD, and of course it wouldn't let you proceed.

---

### Post by Vishal Agarwal on 2008-08-06
Jaca,

Just recently posted this link.

[[COLOR="Blue"]Install Ubuntu 8.04 Hardy Heron From USB [Updated][/COLOR]]("http://www.teamteabag.com/2008/03/07/install-ubuntu-804-hardy-heron-from-usb/") 

Try this, if it can help you.

---

### Post by jaca on 2008-08-06
> **Vishal Agarwal said:**
> Jaca,

Just recently posted this link.

[[COLOR="Blue"]Install Ubuntu 8.04 Hardy Heron From USB [Updated][/COLOR]]("http://www.teamteabag.com/2008/03/07/install-ubuntu-804-hardy-heron-from-usb/") 

Try this, if it can help you.

Thank you. In any cae I will stick to openSUSE for the time been on my descktop, so far I like what I see. I will keep ubuntu in my laptop, and in my other very old laptop (32bits). As I said, I posted it to help anyone who comes across the same issue and keeps blaming him/herself after reading the message boards. Eventually one day this will issue will be solved. 
Another thing that either is missing or I wasn't able to find is a network install.
Sorry if I sounded a bit harsh at the beginning, but I grew frustraded of people repeating token replies to the same problem. I had read what had been written in the forums about this issue, and I knew before I posted the first message that I would get the very same replies.
My aim is to do away with MS Windows all together, my very old laptop has only ubuntu in it, since it was going slow with windows (300 MHz, 256 Mb RAM) and works perfectly now. But, to have a professional grade, reliable distribution, the attitude of the people involved need to be more thorough. If someone reports a problem like this, as far back as 2004, and keeps creeping up every now and them, it is worth having a closer look at it. A bug in a peace of software is far more likely than having so many bad CD burns.

---

### Post by Growbag on 2008-08-06
The thing is, jaca could have done the normal/descent thing and actually asked for help.

But he was too proud/scared/inept to ask in a nice way, and instead did the all-too-common thing these days, and came in threatening to quit using Ubuntu, insulting/crying/attacking so that he would get attention and help.

Why do you think he is still replying here?

He said he was going to openSUSE, so why is he still here?  He said it worked better, so why is he still here?

The more you lot actually help these socially inept people, the more you help proliferate this kind of behaviour.

He never asked for help, so don't give any unless he actually asks in a polite fashion.

He has clearly stated that Ubuntu doesn't work for him and is moving on.

---

### Post by philinux on 2008-08-06
I've never burnt a coaster as i use cdrws. And they were pcworld cheapies.

Never had a problem.

Try your cdrs on another pc.

---

### Post by jaca on 2008-08-07
Again and again, blame the conduct, blame whatever. Some of you do nor pay attention.
Yes, I am not new to using and installing ubuntu. Yes, I installed in my mad64 laptop, which has 3Gb RAM memory. At the time it took me several tries and several burnt CDs to do it, it would give me something between 3 to 7 errors typically. When tried to install it on the desktop, a amd64 with 1Gb RAM, the number of errors went up to 25 or 31. On the laptop I used Roxio to burn the CDs, on the desktop I used Nero, and GnomeBaker within Debian, same result.
More over, I checked if what the install procedure did what it said it did. 
1.- I md5sum the downloaded iso image, got the correct answer according to what is posted in the ubuntu website.
2.- I can put the CD in the CD drive and read individual files from it,as does the installation program. The I can md5sum every individual file, without copying them (md5sum /CD/....) and check against the md5 hash codes in the mad5 text file contained in the CD. Result correct.
If any of you have time and is any good at doing shell scripts, can easily replicate the check-CD-for-defects (CCFDP) procedure and test it within other operating system.
3.- Most likely, the bug has to do with memory management of the CCFDP, that is why it gives more errors on lower RAM, also the bug has to have some randomness in it. The very same CD gives different number or errors in the same machine when checked several times. And that's why, if one tries many times, and the RAM memory is big enough one eventually ends up installing the dam thing. I bet that with 4Gb amd64 machines no one would notice this problem. And that is why there are fewer questions about this issue as time goes by, because people tend to have more memory in their machines. It can also depend on the type of memory/motherboard, but I am not so sure of that. My guess is that at some point, results from the md5 checks are sometimes overwritten on top of each other. I understand that this is a bug hard to catch by trial and error if whoever is in charge of this piece of software works in a nice, fat memory, machine. He needs to either take some memory sticks out or try pure logic, which I don't think is safe enough due to Murphy's law: when you find a bug, there is always another one.
What remains a fact, is that the CCFDP gets different results (md5 hashes) than the md5sum for the same files of the same CD, depending on the environment where it is run, i.e. the system, RAM, etc., and a random variable, i.e. some files some times yield the correct hash, and some other times they don't.
I think I have done enough research into this. I am normally busy, as I guess you all are, and I wasted enough time with this already. If someone with enough knowledge, time and resources wants to follow up on this, good. Any other message recommending to  try again with this burner or that CD brand, or check this or that, or blaming me for being me for the lack of etiquette, which I may have but at least I check things before talking, are a waste of time.

---

### Post by AlecJ on 2008-08-07
I've been here with a machine before, but only trying to install MS office in a "fully working" windows machine, Office would not install or run the same as you report. That same machine was filed to the "i'll fix it later" pile where I tried to install Red Hat and had similar problems, yet it still allowed me to install and run XP, explorer and the novell client worked great?

Finally after much ado, I found a bootable floppy mem test disc (from down the back of the desk) and once cleaned, it told me that 1 ( not 2 or 100) 1 address was damaged. That address clearly was not touched by XP but Red hat and office really rather liked it.

I have 2 pc 64bit amd's both started with Edgy now upto Hardy, not had a problem with ubuntu, had a few with mythbuntu mind.

---

### Post by Roaster on 2008-08-07
> **jaca said:**
> I did that, I ordered a CD from ubuntu, I got it one month ago. AND THE RESULT WAS THE SAME!!, I already said it, another proof that people here do not listen, or do not read.
Some guys here smell a troll, fine, go on, bury your heads in the sand. There is a bug in the process that checks the CD that has to do with memory management, it gives more errors for the same CD in systems with 1Gb of RAM (my desktop) than on those with 2Gb of RAM (may laptop).
But go on, blame me, call me an idiot a troll or whatever. Blame the CD drives, blame the CD media. Ubuntu is great bless its name and anything else is a blasphemy, from what I saw this problem has been around for at least two years, I read all the threats and I consider that there is no point of asking for help to get replies like the ones here that exactly the same as the ones posted two years ago: check your download, check your CD drive, use the alternate CD, etc.
This threat is just to let you know, or anyone else that comes across the same problem: is not your fault, is not your CD drive fault, is not the downloaded file fault, THERE IS A BUG.
The community wants to listen? fine, it doesn't, fine as well.

I feel much the same as you do after experiencing almost exactly the same problems. 
Why is it that you can ask a question on this forum and get more flames than answers? 
If the folks here have good answers, then by all means answer, but if you are just trying to get your post total up there or if you don't have a clue, please refrain from the insults and and idiotic suggestions. Most people that post here are NOT complete computer newbies, just new to Ubuntu. JMO, flame away!

---

### Post by Friqenstein on 2008-08-08
...

---

### Post by Uzelth on 2008-08-08
Okay, jaca... Just confirm a few things with a simple yes or no answer (nothing more, nothing less... Just 'yes' or 'no'):

[list]
[*]The CDs burn without error?
[*]You can boot to the Live CD, but the **installation** process fails?
[/list]

As for blaming the conduct, we have every right to. You have just whined, complained and outright attacked, yet not asking for help. If you want help, you ask and you ask politely. You don't make insulting remarks due to **your** lack of providing details or failing to understand whatever replies are posted.  You won't get anywhere in life being as rude as you have on these forums where people have tried to help, despite your lack of requesting help.

---

### Post by cariboo on 2008-08-08
I going to don my flameproof underwear and say that from my point of view there sure do seem to be a lot of problems with Ubuntu and Asus motherboards. They seem to be pretty good gaming boards under windows, but with Ubuntu they don't work very well. Dare I say they may have the same problems as Foxconn had.

Jim

---

### Post by Roaster on 2008-08-08
> **cariboo907 said:**
> I going to don my flameproof underwear and say that from my point of view there sure do seem to be a lot of problems with Ubuntu and Asus motherboards. They seem to be pretty good gaming boards under windows, but with Ubuntu they don't work very well. Dare I say they may have the same problems as Foxconn had.

Jim
There well may be a case to be made as far as Asus motherboards and this problem, but not this Asus motherboard, as I had 8.04 64bit running on this computer before upgrading the graphics card and am now running 8.04.1 32bit on this same computer but I cannot for the life of me get the 64bit live cd or the alternate cd to install again! Sorry, I do not want to hijack this thread! I'll just observe from this point on! Thanks,

---

### Post by Electric Bill on 2008-08-08
Well I'm new to the Ubuntu forum but not new to computers.
When your accessing a drive, either hd or optical, all the data you're reading is loaded on to RAM first.
Since most of us don't have any problems with the ISO download or CD I suspect a problem with RAM, BIOS memory settings or voltage.
Of course there's always data corruption due to an overclock.

Just my 2 cents.
Bill

---

### Post by Roaster on 2008-08-08
> **Electric Bill said:**
> Well I'm new to the Ubuntu forum but not new to computers.
When your accessing a drive, either hd or optical, all the data you're reading is loaded on to RAM first.
Since most of us don't have any problems with the ISO download or CD I suspect a problem with RAM, BIOS memory settings or voltage.
Of course there's always data corruption due to an overclock.

Just my 2 cents.
Bill
That may well be my problem, as I also added ram (went from 2g to 4g) and OVERCLOCKED when I upgraded the graphics card!! I most certainly will check this out! If, I find that the extra ram is at fault ( it passes memory test ) what do I do then? Well, I'll cross that bridge when I get to it! Thanks so much for bringing that to light! Maybe that is the answer. Thanks again

---

### Post by erickghint on 2008-08-09
> **cariboo907 said:**
> I going to don my flameproof underwear and say that from my point of view there sure do seem to be a lot of problems with Ubuntu and Asus motherboards. They seem to be pretty good gaming boards under windows, but with Ubuntu they don't work very well. Dare I say they may have the same problems as Foxconn had.

Jim


I've always had decent luck with Asus mobos. I'm currently using an Asus M2N-SLI... which models seem to have trouble? Not saying that you're wrong, just wondering for future reference. 

 Also, @ dude that started this thread... Have you only tried the 64-bit version of Ubuntu? Which versions of OpenSUSE and Debian are you running (ie. 64 or 32 bit)?

---

### Post by lisati on 2008-08-09
> **Electric Bill said:**
> Well I'm new to the Ubuntu forum but not new to computers.
When your accessing a drive, either hd or optical, all the data you're reading is loaded on to RAM first.
Since most of us don't have any problems with the ISO download or CD I suspect a problem with RAM, BIOS memory settings or voltage.
Of course there's always data corruption due to an overclock.

Just my 2 cents.
Bill
This may well be something to keep in mind, and to not take the "behind the scenes" activity of our computer gear for granted.

---

### Post by cariboo on 2008-08-09
THere doesn't seem to be any specific models, aside form a lot of eeepc posts, there seems to be a lot of people having problems getting there asus mb's and peripherals running properly. This might mean that there are just a lot of asus mb's out there, which I suspect is what is happening.

Jim

---

### Post by Growbag on 2008-08-09
> **Roaster said:**
> That may well be my problem, as I also added ram (went from 2g to 4g) and OVERCLOCKED when I upgraded the graphics card!! I most certainly will check this out! If, I find that the extra ram is at fault ( it passes memory test ) what do I do then? Well, I'll cross that bridge when I get to it! Thanks so much for bringing that to light! Maybe that is the answer. Thanks again

It might be your power supply.

Adding more RAM and a big bad video card is a hell of a drain.

Especially if it is a cheap power supply.  It's quite common for people to run 500w power supplies today.

Try taking the extra RAM out, and use the onboard graphics card (if it has one), or a old cheap one.

If it works, then I would look at the power supply.

---

### Post by AlecJ on 2008-08-09
Let's try to bring this back to the real world here.
So the guy can't run ubuntu (64bit) on his system, most of us can so, law of averages says it's his fault.
we blame the hardware, he blames the software.
yet he can run Suse? (32 or 64 bit?)
I have to admit it does sound like a hardware problem.
I guess what we all upset about is the general slating of ubuntu, and I have to admit it rattles me as to the amount of people doing this, like it's a fret that they won't use ubuntu because this or that don't work quite like they expect.

News flash!
It's free software! there's no money back, no law suit's, no buy one get one free.
I know I couldn't do any better, yet this crowd (in my option) outstrip Microsoft!

Could this be the end of this thread....Please

---

### Post by slowcoach on 2008-08-09
If I have cool&quiet on I get poor burns, the CD/DVD *may* install once but will give read errors if tried later. Asus A8V DeLuxe.

---

### Post by Vishal Agarwal on 2008-08-10
> **Vishal Agarwal said:**
> Jaca,

Just recently posted this link.

[[COLOR="Blue"]Install Ubuntu 8.04 Hardy Heron From USB [Updated][/COLOR]]("http://www.teamteabag.com/2008/03/07/install-ubuntu-804-hardy-heron-from-usb/") 

Try this, if it can help you.

Repeated again,

Did u try this. This is an USB installation, SO there should be no read errors ?

---

### Post by Roaster on 2008-08-10
Hello all, how do you publicly thank someone on this forum, because I want to thank 'ElectricBill' for his response. Let me give a little background. I built this computer(my first, I've since built 3 more) about a year and a half ago. Asus P5N32 SLI SE motherboard, 2gigs of ram, nvidia 7600gt graphics card. Windows XP Pro. Core2Duo, 650w psu. At that time I also started using Ubuntu 6.04? anyway, I went from there to 8.04 x86 64bit which worked great and I loved Ubuntu (still do). About 2 months ago I upgraded the graphics card to nvidia 9600GT, installed 2 more gigs of ram and a new, much bigger  hard drive. Clean install of Windows XP Pro and tried to dual boot with 8.04 64bit. Could not install! Tried alternate cd, no joy! Tried other Linux 64bit OS and they would install no problem! After much browsing of this and other forums I came across this thread and when ElectricBill said something about the overclocking and ram issues I set the clock speeds back to default and tried to install 8.04 64bit again, no joy!! I then removed 2 gigs of ram and BINGO! success!!! So...... it appears, at least in MY experience that the 64bit live CD has problems with amounts of ram of 4 gigs. How many of you out there who have had problems like this had more than 2gigs of ram installed? Anyway my problem has been solved and many thanks to ElectricBill.

---

### Post by Electric Bill on 2008-08-10
> **Roaster said:**
> Hello all, how do you publicly thank someone on this forum, because I want to thank 'ElectricBill' for his response.I believe you just did :lolflag:.
Glad you got it sorted out.
 
I see a lot of problems being posted that are probably hardware related but since many of the people here are not builders they assume it's a software issue.
 
I'm an AMD guy so I don't know a lot about Intel builds but one of the most common problems is RAM settings.
The BIOS usually has a default Vdimm (RAM voltage) setting of 1.8V but a large percentage of performance modules require 2.0-2.1V.
Some boards won't run with 4 sticks and some BIOS's like my Abit AX78 don't set the DIMMS TRFC value correctly.
 
Another issue is with Cool'n'Quiet.
If you want to install an operating system I suggest you disable it until you're done.
And the cardinal rule is don't flash the BIOS or install an OS when OC'd.
 
Once again glad to be of assistance.
 
Bill

---

### Post by Roaster on 2008-08-10
Well, I guess my problem is NOT resolved as I thought. After the installation and updates, I shutdown and reinstalled the other 2g of ram. 8.04 64bit would NOT boot! Removed the other ram module (not the same 2g module I had removed the first time) and it booted just fine! So....... the problem would appear to be with having 4g of ram on this computer. Guess I'll just go back to using the 32bit 8.04 as I have not found Linux OS that I like as well as Ubuntu, and I am not gonna remove the extra ram. I still want to thank everyone that provided help. Perhaps this is a problem of this particular motherboard. Has anyone else had this kind of problem caused by having 4g of ram?

---

### Post by Growbag on 2008-08-11
You need to run a "pae" (Physical Address Extension) kernel when using more than 2 gigs or RAM I believe.

Not sure if the ubuntu mob provide one, but openSUSE does.

---

### Post by cariboo on 2008-08-11
I believe the OP is long gone, but I haven't seen anybody suggest using the mini iso, It installs just enough to do a net installation, that way you don't have to worry about bad cd's. The mini.iso is available here:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Jim

---

### Post by Roaster on 2008-08-11
> **Growbag said:**
> You need to run a "pae" (Physical Address Extension) kernel when using more than 2 gigs or RAM I believe.

Not sure if the ubuntu mob provide one, but openSUSE does.

I'm not computer or linux savvy enough to know what you mean, but thanks, I do appreciate the interest. As I said I did not mean to hijack this thread and I do apologize the the OP.

Anyone here know what is meant? and will Ubuntu 'mob' provide a fix? Peace

---

### Post by exziggy on 2008-08-11
i don't know exactly what are you doing, so i'm gonna tella what i did
i downloaded it directly from the ubuntu page and to burn it simply right clicked it and selected "open with..." selected nero, and it worked.
        i hope it helps.

---

### Post by cariboo on 2008-08-12
Your ram problem has something to do with your bios settings. I would suggest using the default settings and then try booting again these days most motherboard set up things automacially if you use the default settings.

Jim

---

### Post by Growbag on 2008-08-12
> **Roaster said:**
> I'm not computer or linux savvy enough to know what you mean, but thanks, I do appreciate the interest. As I said I did not mean to hijack this thread and I do apologize the the OP.

Anyone here know what is meant? and will Ubuntu 'mob' provide a fix? Peace

Search in Synaptic for **kernel** and see if there is a version with **pae** in the name.

If so, install that (assuming that you can actually get into Ubuntu first of course!), and when you reboot you should see that kernel listed at the boot screen.

Select that and see if that makes a difference with all your RAM installed.

---

### Post by Roaster on 2008-08-12
Hey all, I just wanted to update my attempts at getting 8.04.1 64bit to run on this computer. After more reading and searching I went into the BIOS and reset the memory remap setting to "enabled", it is set to "disabled" on default settings. I still could not get the 'liveCD' to install however, after trying the 'alternateCD", that I had downloaded earlier, it is now working beautifully!!I hope this will help the OP and I wish to thank the OP for getting me started on this again, because I had about given up too. And thanks to nearly everyone else that commented here. With your invaluable help this Ubuntu noobie is happy again:) Keep up the good work! Best to all,

---

