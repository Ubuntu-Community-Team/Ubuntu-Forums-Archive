---
title: "Wine - MS Office 2010 - can't open existing documents"
date: 2012-10-11
forum: Wine
---

### Post by Bella Wilfer on 2012-10-11
Hi   ):P

I'm new here as I've only just switched to Ubuntu for the first time last week. I'm using Ubuntu 12.04 LTS.

For my work, I need to be able to use MS Office 2010, so I downloaded and installed and activated Wine.

It took me a while to get it all sorted out, but eventually I managed.

Now I am able to open Word and Excel using Wine.

_**However, I can't use those programs to open existing files.**_

I *am* able to create a new document using Word or Excel and to save that document to the C drive.

But I can't open those documents again, to edit them, or to view them.

Any help would be much appreciated, as I'm starting to lose track of what I'm doing Ubuntu-wise... I'm not even sure how/ where to search for tips for this specific problem.

**[COLOR=Blue]Has anyone had this problem before or can make a blind guess as to what *might* be a solution?[/COLOR]**

Any pointers in a vaguely right direction are much appreciated :p

And SORRY if this is a really dumb question! #-o

Thanks
Bella

---

### Post by cbanakis on 2012-10-11
I'm using office 2010 through wine.

How exactly is it not opening files?

Did you navigate to and open the files through word/excel and they don't open?

Or are you trying to right-click open with excel/word?

---

### Post by newb85 on 2012-10-11
It's been a couple years since I touched Wine, but I seem to recall that programs on Wine can't be called up by the file browser in order to open a file.  You have to open the program within Wine and then use the program's Open feature to open the file.

---

### Post by cbanakis on 2012-10-11
> **newb85 said:**
> It's been a couple years since I touched Wine, but I seem to recall that programs on Wine can't be called up by the file browser in order to open a file.  You have to open the program within Wine and then use the program's Open feature to open the file.

You can right click + open with.

The glitch these days, is that there are several entries listed in "open with" for each application.

Some of them just launch the program, and some of them work.

My workaround, is navigating to /home/.local/Apps/

Then I select all the .desktop files, right click, properties.
Then permissions, and check "allow executing as a program.

Then I double click, 1 at a time, till I find an entry that launches the app, then pops up with an error.

The one that opens with an error, is the one you want, believe it or not.

So then I delete all entries for that program, except the one with the error.


As far as I can tell, wine creates several entries in /home/.local/Apps/ for each program.

There is 1 for each file extension associated with that program, and another that just launches the program.

having 1 for each extension does not seem to serve any purpose, and neither does having 1 that opens the program, but not the file.

The error that tells you, that you've got a winner, is because the program is looking for a file to open, but can't find it, because you launched the program from the .desktop file.

So double clicking directly on the .desktop file results in an error, but right click and open with that file results in success.

The whole thing is difficult to explain, but yes, it can and does work quite seamlessly.
(After you delete all the garbage from /home/.local/Apps/)

---

### Post by DuckHook on 2012-10-11
Hi Bella,

Welcome to Linux!

There is no such thing as a "dumb" question. The Linux enthusiasts on this site are happy to see you trying out Ubuntu and welcome you to the Linux world. If you were able to get *Wine* working and *MSOffice* loaded as a one-week old new user, I take my hat off to you. I have a few questions and then some suggestions and comments:

1. How are you trying to open old documents? Are you opening them from within *MSOffice* itself or are you opening them from some form of file manager/browser? If it's a manager/browser, which one are you using? The Windows file manager, or the Ubuntu one?

2. Where are your old files? When you say:

> However, I can't use those programs to open existing files.

...do you mean that you can't find them at all, or that you can see them, but they won't open when you click on them?

3. How have you set up your system? Are you dual booting with Windows or have you gone to Ubuntu entirely? Are your old Windows files on a different HD? A different partition? etc. Please provide as much info as possible on your configuration, even if it may seem obvious to you.

I have been a long-time user of both Windows and Linux (decades). Therefore, the following observations and suggestions come from both my own experience as a user and as a person who has helped countless people move from Windows to Linux (troubleshooting along the way):

1. Most people who think that they need *MSOffice* really don't. They are just assuming that the equivalent Linux tools won't do the job. The most powerful Linux office suite is *LibreOffice* and it comes pre-installed on your system if you are running Ubuntu. If you are running another variant of Ubuntu, then it can easily be installed through the *Software Center*. It is true that *MSOffice* macros, scripts and other high-level functions won't transfer to *LibreOffice*, but 95% of the people using the Windows product do not use these functions. With a little practice, they find that they can do exactly the same things with LibreOffice as they could with MSOffice. I would recommend that you at least give it a try.

2. The reason for this is as follows: while it is possible and even easy to run heavy-duty Windows programs in *Wine*, my experience is that, sooner or later, you run into problems. Usually, it occurs when either *Wine* or the Windows program gets updated. For example, you may wish to upgrade Ubuntu to version 12.10 later this month. *Wine* gets upgraded along with Ubuntu, and suddenly, *MSOffice* stops working. This is not likely to happen, but it is a valid example because it has happened to me in the past.

3. *LibreOffice* will save your work in *MSOffice* format. It will also read *MSOffice* documents pretty well, though sometimes its behaviour in this regard is a little flaky. I use nothing but *LibreOffice* and I transfer spreadsheets and word processor documents with my Windows-only friends without any problems. You can set up your preferences so that it saves in *MSOffice* format by default. The upside to making this transition is that, if you find yourself happy with *LibreOffice*, it eliminates another layer of complexity from your life. Whenever possible, it is always better to run a native Linux app than running a Windows app with *Wine*.

In the meantime, we are happy to help you with your initial problem. Please provide the requested info and we can go from there.

---

### Post by oldos2er on 2012-10-11
Moved to Wine.

---

### Post by Bella Wilfer on 2012-10-12
Hi all,

Hi [cbanakis]("http://ubuntuforums.org/member.php?u=824651"),

I've tried opening the documents both ways, but nothing happens either way.
Thanks for the suggestion re /home/.local/Apps/
I'm not sure I understand it yet, but I will sit down on the weekend and give it a try, step by step.

Hi [DuckHook]("http://ubuntuforums.org/member.php?u=1256508")

Thanks for your reply. I can see the files quite normally and I either try opening them using Word or by double clicking on them in the "Wine view C" window - but nothing happens.

I have set up the computer as running only Ubuntu - no partition.

At the moment I have only 2 files on there. One is a document that I downloaded from my mail account to see if Word was working. When that didn't open, then I tried creating a document with Word, which worked. I saved that to the same folder on the C drive.

So these 2 existing files are sitting together in their folder, looking nice and snug. Everything is great, except that when I try to open them "nothing happens".

For my work, I unfortunately *do* need MS Office - tho I would be glad if I didn't! :-)

I work freelance and have complex documents sent to me by my customers and if only even a single line or feature of formatting is altered (even minutely) by opening it in a program like Libre or Open Office, then that would be a nightmare for me and my customers because the documents usually go straight to the printer's after I've worked with them. So I simply can't afford to risk any tiny changes...
[U][COLOR=Blue][B]
A question to you both:[/B][/COLOR][/U]

Although I *did* feel proud of myself for having gotten Wine and Office to (eventually) install I am now concerned that I *will* keep running into problems with it, as you [DuckHook]("http://ubuntuforums.org/member.php?u=1256508") suggest. 
I guess I was a bit naive when I googled "Ubuntu + Office" and read that the solution was "Wine".
Having now read a bunch of entries in this forum, I'm kind of suprised that I did get it installed and running as well as I have....

The computer I've installed this on, btw, is my 2nd comp - a back up comp in case my laptop dies... 

So now I'm wondering whether it's worth the hassle trying to get Office to work on there, if it's only going to keep having glitches in future, or just leave it as a purely Ubuntu/ Linux etc. PC?

And if I do try to fix the issue of opening documents with Word, should I get a local computer shop to help me? Cos as I said, I'm starting to feel out of my depth. 

(I don't even want to say how many hours it took me to work out where to find the Terminal window and how to use it... #-o  )

There's a nice computer store in our town that was started by  computer-crazy students and they charge fair rates. Is there a good  chance that they could fix the problem in under an hour's work?

Anyway - thanks very much for your replies!!! It's nice to not feel alone with a computer problem!

And many thanks for your kind welcom to the Ubuntu community. I have wanted to run Linux on one of my PCs for about 15 years now - finally gotten around to it!

Cheers!
Bella

---

### Post by newb85 on 2012-10-12
> **Bella Wilfer said:**
> And if I do try to fix the issue of opening documents with Word, should I get a local computer shop to help me? Cos as I said, I'm starting to feel out of my depth. 
...
There's a nice computer store in our town that was started by  computer-crazy students and they charge fair rates. Is there a good  chance that they could fix the problem in under an hour's work?

That depends on the computer store.  I took my machine to a computer shop a couple years ago, and the moment I told them I was running Linux, they told me they couldn't help me.  Your experience might be completely different.  Depending on how much hassle it is to get your machine there, you may want to call ahead and ask a few questions first...

---

### Post by Bella Wilfer on 2012-10-12
Hi [newb85]("http://ubuntuforums.org/member.php?u=833049")
that is a good point. Thanks :-)
I've made a little progress on my problem.
Before trying [cbanakis]("http://ubuntuforums.org/member.php?u=824651")'s solution I thought I'd try something a little silly and banal to see if that worked. And it did - in part.

I closed Word. And then did the "open with" option, of clicking on the file in the C drive and told it to open it with Word. And then it did!

Before, I had Word already open (in the background, so to speak) - so maybe Word wasn't feeling "activated" - because it was already open? I dunno...

Anyway, this has now worked for 2 out of 4 files... For the other 2 it's still not working, but who knows, that may be due to some other issues...

So I will keep trying around on the weekend - but I am very happy to have made this much progress at least - even if I am a little mystified why some things work and others don't - but that's life, ey?

Oh, and I wanted to say that my having gotten this far in 1 week (ie installing Ubuntu, installing Wine, installing MS Office 2010) is due partly to beginner's luck but is also thanks to the great instructions and tips on the Ubuntu pages. They are really helpful.

Cheers,
Bella

---

### Post by cbanakis on 2012-10-12
Just to be clear, you do not have to do all the stuff I was talking about.

But you'll notice, if you "right click + open with" on a file, you will notice that MS word is listed like 8 times, and the same goes for Excel.

The whole thing I was talking about, is just to get rid of all the junk, so you only have 1 listing for each program.

There is however, at least 1 copy of each program, that does not work with "open with".
(Thats why I brought it up)

What I did was verify that I had the correct one, then deleted all the others, to avoid the issue.

---

### Post by Bella Wilfer on 2012-10-13
Hi [cbanakis]("http://ubuntuforums.org/member.php?u=824651"),
thanks for clarifying - yes there are multiple versions of Word etc in the "open with" window that pops up.
I see what you mean now and will try your method for working out which is the right one to use.
Thank you!! 
:-)

---

### Post by DuckHook on 2012-10-13
Hi Bella,

Good to know that you have a PC running just Windows to fall back to. This is excellent.

> **Bella Wilfer said:**
> I can see the files quite normally and I either try opening them using Word or by double clicking on them in the "Wine view C" window - but nothing happens.

It is important to note that because you have decided to run Wine, you are by necessity dealing with something that is more complicated than a simple Ubuntu install. It's not difficult, but there is just a little more complexity.

For example, you now have 2 file managers that you can use: one is native to Ubuntu and is called *nautilus*. The other is a file manager specific to *Wine*. In Windows (XP), it would have been Windows Explorer, but Wine substitutes a Wine version of it called *Wine Explorer*. When you are looking at files:

1. Which File Manager are you using (*nautilus* or *Wine Explorer*)?, and
2. Where do you place your MS Office documents?

> At the moment I have only 2 files on there. One is a document that I downloaded from my mail account to see if Word was working. When that didn't open, then I tried creating a document with Word, which worked. I saved that to the same folder on the C drive...when I try to open them "nothing happens".


I don't quite understand. Do you mean to say that even the one you created with Word does not subsequently open? You can create it the first time but, once you close it, you cannot open it thereafter? If so, it may be a problem with permissions (one of Linux's powerful security features). However, we need clarification from you about this behaviour.

>  For my work, I unfortunately *do* need MS Office - tho I would be glad if I didn't!
...I simply can't afford to risk any tiny changes...Okay. Understand completely. No other option. Therefore, the primary goal is to create a system that plays nicely with MSOffice. This goal will have application later in my reply.

> Although I *did* feel proud of myself for having gotten Wine and Office to (eventually) install I am now concerned that I *will* keep running into problems with it, as you DuckHook suggest.
I guess I was a bit naive when I googled "Ubuntu + Office" and read that the solution was "Wine".

You were not naive. Brave, rather. The jump to Linux, especially for non-technical users is tougher than a lot of technical people think. However, now that you are here, let's explore solutions.

> The computer I've installed this on, btw, is my 2nd comp - a back up comp in case my laptop dies...


Like previously said, this is great. Here is my first really important piece of advice:

*Keep using the Ubuntu computer as your backup computer*. Do not use it for production work until we get this matter sorted out. Once you are happy with the way it works, then you can consider slowly migrating your real work to it. Until then, think of it as experimental.

> So now I'm wondering whether it's worth the hassle trying to get Office to work on there, if it's only going to keep having glitches in future, or just leave it as a purely Ubuntu/ Linux etc. PC?


For my part, I think it is worth trying, but only you can make this call. I should add that there are many alternatives to achieving what you need. If your computer is powerful enough, another alternative is to install a VM (virtual machine) running Windows. This is different than Wine because you would be running a real copy of Windows inside a "make believe" computer that, in turn, runs within Ubuntu. This normally solves many issues because you would be running MSOffice on a real Windows operating system instead of a Linux OS that has been modified to run Windows programs (Wine).

Yet another alternative is to configure your desktop computer for dual boot. This will allow you to choose between Windows or Ubuntu at boot. It is not as "elegant" a solution as either Wine or a VM (because you can't run both OSes at once), but it is also simpler and easier to use.

My suggestion: if you have both the time and the inclination, exploring the alternatives is both rewarding and educational. If you just want your computer to do real work and have no interest in fiddling with Ubuntu, then simple is best and you should run only Linux apps on Ubuntu.

> And if I do try to fix the issue of opening documents with Word, should I get a local computer shop to help me? Cos as I said, I'm starting to feel out of my depth.


If this is just a backup machine to your laptop, then don't spend the money on a computer shop. If the ship people don't know Linux, the advice you will get here is often much better.

If you are still game (and only if so), then let's role up our sleeves and get going:

1. If you know the precise model of CPU, amount of system memory and size of hard drive you have, then it's easiest to just tell us. If you don't know this info, then open up a terminal. We are going to see what sort of hardware and how much capacity you have.

Copy the following commands into the terminal and post the results back to this thread:

```
lscpu
```
```
free
```
```
df
```

2. Next, we check to see if you installed wine correctly. Again post results back here:

```
ls -ln ~/.wine
```
also, to compare to your own user ID
```
id
```

3. Next, we find where you store you MSOffice docs, in particular, one of the files that you can't open. Example: say it's "unique_document.doc", then the location can be found by typing the following:

```
locate unique_document.doc
```

this will result in a string that looks something like this: /home/your_name/Documents/unique_document.doc

Yours will look different because every user stores data in different places. The important thing is to note the full path.

4. Let's determine ownership and permissions for this document:

```
ls -ln /home/your_name/Documents/unique_document.doc
```

I know that all of the preceding is awfully arcane, but don't be discouraged. All of these things can also be done using graphical tools that you are more used to, but since the objective is to get you working first, we are using tools that are easier to work with on a help forum. That's more than enough for now. Should be enough to give us some clues.

---

### Post by lazarojhr16 on 2012-10-15
just open word or excel or whatever first. then go to file open and choose the document. that will work.

---

### Post by Bella Wilfer on 2012-10-16
Hi,
sorry, things have been a bit busy here, I've not gotten around to tackling this issue any further.
I will go and try the things you've suggested [DuckHook]("http://ubuntuforums.org/member.php?u=1256508") and report back in a few minutes.

I've reached the same conclusion as you about spending money on a computer shop.
Now that I can open 2 of 4 documents, I'm less puzzled than when it wasn't opening anything...

So I was almost going to change this thread to "SOLVED" actually! 

But I will give it another shot and see what happens...

---

### Post by Bella Wilfer on 2012-10-16
The reason I started this thread is cos I wanted to use this PC for more than just "backup".
So I was kind of "desperate" for it to work properly with MS Office 2010, but now, I've been able to change plans...
In fact, you may be horrified how computer-dumb I am...
I am running Office 2003 on my main PC and need to continue using that for work, but also need to use Office 2010 for the new file formats (docx  etc)
Anyway - I'm sooo silly, that I didn't realise that you can a) run both versions side by side, or b) download a converter tool from MS to allow Office 2003 to use all docx files...

So, I bought a 2nd hand DELL as a backup and have installed Ubuntu, Wine and Office 2010 on that...

In the meantime I've managed to get both Office 2003 and 2010 working on my main PC, so the backup PC has become less "important" at the moment...

So, I'm going to try those commands suggested above... and then you may also be horrified what a stupid 2nd hand PC I've bought.... Ugh! Me and computers is not a match made in heaven! :-P

---

### Post by Bella Wilfer on 2012-10-16
Okay, so now, bit by bit...

> For example, you now have 2 file managers that you can use: one is native to Ubuntu and is called *nautilus*. The other is a file manager specific to *Wine*. In Windows (XP), it would have been Windows Explorer, but Wine substitutes a Wine version of it called *Wine Explorer*. When you are looking at files:

1. Which File Manager are you using (*nautilus* or *Wine Explorer*)?, and
2. Where do you place your MS Office documents?

 	Quote:
 	 	 		 			 				At the moment I have only 2 files on there. One is a document that I  downloaded from my mail account to see if Word was working. When that  didn't open, then I tried creating a document with Word, which worked. I  saved that to the same folder on the C drive...when I try to open them  "nothing happens". 			 		 	 	 
I don't quite understand. Do you mean to say that even the one you  created with Word does not subsequently open? You can create it the  first time but, once you close it, you cannot open it thereafter? If so,  it may be a problem with permissions (one of Linux's powerful security  features). However, we need clarification from you about this behaviour.

I'm not sure about Nautilus - when I click on the icons next to the "Dash" icon, one of them is called "Home Folder" - this is what I was using as a File Manager generally. To open MS Office Programs or Files, I was using the Wine Explorer.

Yes, as you asked, I was (successfully) creating a document using Word. Then closing the document. And then not able to re-open it. (I had left Word open.)

Now that I've found the "solution" of also closing Word and then opening the document using the Wine Explorer, I can at least open that document. But I guess I can't open a 2nd document, cos then Word is already open (tho I will check that again, too).

My MS documents are in "Documents" which is in "My Folder".

---

### Post by Bella Wilfer on 2012-10-16
This is the result for "lscpu"

Architecture:          i686
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    2
Socket(s):             1
Vendor ID:             GenuineIntel
CPU family:            15
Model:                 6
Stepping:              5
CPU MHz:               2990.232
BogoMIPS:              5980.74
L1d cache:             16K
L2 cache:              2048K

---

### Post by Bella Wilfer on 2012-10-16
this is the result for "free"

                       total       used       free     shared    buffers     cached
Mem:        497048     480524      16524          0       4208     231692
-/+ buffers/cache:     244624     252424
Swap:       511996     393000     118996

---

### Post by Bella Wilfer on 2012-10-16
okay, that didn't keep the formatting

the word "total" should be above the number 497048
and so on...

---

### Post by Bella Wilfer on 2012-10-16
maybe this will work:

....................total       used       free     shared    buffers     cached
Mem:        497048     480524      16524          0       4208     231692
-/+ buffers/cache:     244624     252424
Swap:........511996     393000     118996

---

### Post by Bella Wilfer on 2012-10-16
this is the result for "df"

Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda1       76417088 5269808  67265452   8% /
udev              241232       4    241228   1% /dev
tmpfs              99412     816     98596   1% /run
none                5120       0      5120   0% /run/lock
none              248524      80    248444   1% /run/shm

---

### Post by Bella Wilfer on 2012-10-16
this is the result for 
ls -ln ~/.winetotal 4140
drwxrwxr-x 2 1000 1000    4096 Oct  9 15:26 dosdevices
drwxrwxr-x 6 1000 1000    4096 Oct  9 14:29 drive_c
-rw-rw-r-- 1 1000 1000 3950414 Oct 16 23:09 system.reg
-rw-rw-r-- 1 1000 1000  272871 Oct 16 23:14 user.reg
-rw-rw-r-- 1 1000 1000    2150 Oct  9 12:38 userdef.reg

---

### Post by Bella Wilfer on 2012-10-16
this is the result for "id" (whereby I'm going to replace my name with XXXX cos I don't want to post my name on the internet...)

uid=1000(XXX) gid=1000(XXXX) groups=1000(XXXX),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),109(lpadmin),124(sambashare)

---

### Post by Bella Wilfer on 2012-10-16
Regarding the 2 last suggestions re locating a document - I'm going to postpone that, because it's getting really late here and Office/ Wine/ the PC are not reacting consistently - sometimes opening a document, sometimes not... So I'll have to try and work out what's going on there.

But there do seem to be some bugs in the Office/ Wine combination.

It turns out I can open more than one document at a time (as you would expect/ hope) but Word can't change from viewing one document to the other. All I can see is the one document I opened first - the others are listed as being opened, but nothing happens when I select them...

Anyway, I will leave it there for today. 

Thanks for any ideas you have re the results from the Terminal commands.

(And hopefully no one wets their pants laughing about my daggy computer...) :-)

---

### Post by Bella Wilfer on 2012-10-16
Oh, I forgot to say thank you DuckHook, for your detailed reply. That's so nice! I really appreciate the effort!

---

### Post by DuckHook on 2012-10-16
> ...I will leave it there for today

No hurry. We can pick it up again when you have the time. Knowing that you are now set up on your other computer gives you freedom to figure things out at leisure.

> re the results from the Terminal commands

This tells us a number of useful things:

1. Your computer is powerful enough to be configured in an alternate way that can possibly simplify your computing life. However, this is a *future* consideration that doesn't need to be explored right now.
2. You have installed Wine properly. Some people install wine as the root user, which will lead to all sorts of problems. You have installed it correctly, so we don't have to worry about that problem.

As soon as you can finish the last two commands, we will be closer yet to solving this problem for you. I suspect two areas:

1. permissions
2. spaces in file names

Don't worry about making sense of either of these suspicions for now. We will track them down when you are ready to resume.

Oh, and on behalf of all fellow posters, you are more than welcome. We are glad to be of service.

---

### Post by Bella Wilfer on 2013-04-01
Hi there!
I gave up on trying to solve this problem for a while, as work got ridiculously busy and the whole Ubuntu/ WINE thing seemed too confusing.

I've since had this computer at the computer repair shop and they have installed an additional 2 GB of RAM, as the original amount (512 MB) was ridiculous.

So now, the computer is working more quickly! Yay!

Also, I just read the last post and saw "Spaces in File Names" as an idea... I just deleted the spaces from my file name and WOOHOO - the document opened fine!

Is this something to watch out for generally? Are you not allowed to put spaces in file names???

Thanks for a reply after such a long time!!!!!

XXX
Bella - who is still hanging in there ;)

---

