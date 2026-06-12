---
title: "Cannot get WordPerfect to open in Wine"
date: 2011-09-05
forum: Wine
---

### Post by iam2 on 2011-09-05
Using wine, Word Perfect will go through the motions of installing, but when it comes time to actually open up the application to use it I get the error message: "Failed to change to directory: /home/username/.wine/dosdevices/C:/Programs.  (No such file or directory".

I would post a screenshot of the message but I just have a jpg of it and this Message Box does not give an option to post jpg images, but what I quoted is exactly what the error message says.

So I Created a Folder the normal way in /home, then another one in /home titled "username," then another one inside that named "wine", etc. and the last one inside a "C:" folder titled "Programs."  But that failed too, so I do not know what it wants or how to create what it wants so it can find it.

I read through the Linux Pocket Users Guide for "How to make a directory" for such occasion, but could only find information about what a directory is.

Will someone knowledgable on the subject please instruct me on exactly how to create this folder that wine and wordperfect are looking for?  for which I will thank you now and later.

---

### Post by Enigmapond on 2011-09-05
Is there a reason why you simply don't install LibraOffice? To try to run that under wine is going to give you a stroke....

---

### Post by drs305 on 2011-09-05
iam2,

I've removed your duplicate thread and moved this one to the Wine forum. Also we discourage other than non-standard formatting in most cases.

Hopefully you will get a good response in the Wine forum.

---

### Post by drs305 on 2011-09-05
iam2,

I've removed your duplicate thread. Also we discourage other than non-standard formatting in most cases.

Hopefully you will get an answer to your problem.

---

### Post by robbiemacg on 2011-09-05
Hi [iam2]("http://ubuntuforums.org/member.php?u=1069394"),
I would strongly recommend you use **LibreOffice** to access/edit your Word Prefect documents. 
Is there a reason why you've chosen to try to run Word Perfect via WINE instead?
What version of Ubuntu are you running? Either **LibreOffice** or **OpenOffice** should be installed by default, and both applications are capable of opening, editing, saving WPS documents. You can even save your legacy documents in newer, more easily transferable formats.

---

### Post by walt.smith1960 on 2011-09-05
there are two reasons I'd use WordPerfect over LibreOffice or Word for long or complex documents.

-stream formatting vs. styles
-reveal codes

Saving as .pdf works as long as other don't have to edit.  I have a recent version of WP in a small Windows partition in part for those reasons. The other is that recent Quattro Pro spreadsheets (QPW)won't open in Calc.  Older Quattro Pro file formats will open in Calc.  I don't know where Crossover Office stands re WordPerfect.

Edit:  Codeweavers says X3 is gold so that may be one possibility.  X5 is listed as known to not work but aside for MS file format compatibility, I don't know that there is much difference.

---

### Post by Mark Phelps on 2011-09-05
> **walt.smith1960 said:**
>  Codeweavers says X3 is gold so that may be one possibility.  X5 is listed as known to not work but aside for MS file format compatibility, I don't know that there is much difference.

According to the page I found on WineHQ, X3 is Bronze, not Gold -- see below:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=222]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=222")

Maybe it works better with more current versions of Wine ...

---

### Post by walt.smith1960 on 2011-09-05
> **Mark Phelps said:**
> According to the page I found on WineHQ, X3 is Bronze, not Gold -- see below:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=222](http://appdb.winehq.org/objectManager.php?sClass=application&iId=222)

Maybe it works better with more current versions of Wine ...

I was on Codeweavers' site so that may have been under Crossover Office, not Wine.   I think the problem with WordPerfect & Wine has been getting the installer to run.  It does seem simpler just to either have a small WinXP partition or run a VM and keep XP far away from the internet.  This from Codeweavers site:
[ATTACH]201585[/ATTACH]

---

### Post by iam2 on 2011-09-05
Problem solved. - and I know there is a 'problem solved' page somewhere or other, but ...

Whoa!  Wow.  I am so thrilled so many of you wonderful people responded and so quickly!  My many thanks to all of you for your input, including but not limited to:

**Enigmapond**: to whom I say, your mention is the first I have heard of Libraoffice, and I will check it out.

**drs305**: to whom I say, you must forgive me, I know I have a problem with small 12 pt type @1200+ by 900+ resolution so I just put every thing in larger type presuming, wrongly apparently, that it eases eye strain for everybody.  Oh well ... 12 pt. it is.  And the duplicate thread was in error.  When I thought about how to pose the question and to whom, I was thinking of WordPerfect as another OS because it has its beginnings in Windows.  After posting, I went back to the Forum to see the posting but could not find it, and in the process discovered what is not pointed out on the Post a Question page, and that is that "other OS" had to do with other Distros of Linux, not Windows software, so, not finding my posting and now thinking I messed up on getting it posted, I reposted -- or now just posted -- in the General Forum.  Oh well.  Thanks for making it right.

**robbiemacg**:  to whom I say, I like the idea of LibreOffice, but like I said earlier, this is all new to me and will check it out.  I am running Ubuntu 9.10.  Do you think LibreOffice will work with 9.10?  OpenOffice came with the Distro but I choose KWord over OpenOffice because OpenOffice, even though it will convert Wordperfect documents, it messes them up either in coming, or when transferred to my webpage.  KWord keeps everything in tact and makes it easy.

**walt.smith1960**:  Exactly! The Reveal Codes and other features to which I am accustomed are great for keeping documents clean.  I appreciate your comments.  And what did you say?  Crossover Office?  That is new to me too.  This is great!  Now I get to check out another possibility, and I know nothing about Codeweavers either.  Wow! I have a lot of homework ahead of me.

**Mark Phelps**: to whom I say, I checked out the site you listed, and it is informative.  It is good to see what works best with what.

Okay.  I said "Problem Solved."  Again, using Ubuntu 9.10, and only ever having used WordPerfect 8 for about eight or more years, that is what I first tried to load with Wine, it failed.  Even though it loaded it, it only hung up on the "cannot find the directory" thing, but it was also not listed in the Wine Programs menu so I could not uninstall it.  On hand was a recent copy of WordPerfect 12 I got a hold of, so I tried it, it loaded too, but when I attempted to start the application I again got the error message that Wine could not find the Directory.  Version 12 was listed in the Wine menu so I did manage to uninstall it.  Anyway, I kept trying to do this and that, and kept retrying version 8 and 12, but always the same thing.  That is when I posted my question.  Between the time I posted and the time I reopened the Forum to say the problem was solved and found all the wonderful advice, I had learned a little more about gksudo nautilus and how to permanently delete folders.  In the process of cleaning some stuff up I happened to stumble on the location of the Wine installs of Wordperfect 8, CorelDraw 7, and a few others, and managed to delete them too.  Then, for some reason, I was inspired to try to load Version 12 again, and it took without a hitch and opened right up in the working mode, much to my delight.  The only thing I can think of is that the 8 version that was 'lost' in the machine was interfering with the 12 version install and confused the software or something.  Because once it was out of the way, version 12 went smoothly.

I am going to check out LibreOffice and Crossover Office and Codeweavers too, it is always good to know there are alternatives and backdoors to make matters right.  Hooray for Linux! and Thank you all so much once again.  Make it a great day, (and do not let Comet Elenin disturb you too much).

---

### Post by drs305 on 2011-09-05
iam12,

Glad you solved it. :-) 

You can mark it so via the 'Thread Tools' link to the upper right of the first post. As far as the fonts/duplicate posts, we are a forgiving bunch but like to point it out from time to time just as a gentle reminder. ;-)

Happy Ubuntu-ing !

---

### Post by iam2 on 2011-09-05
Thank you again.  And I do appreciate your gentle reminders.

---

### Post by clearwood on 2012-01-15
At work I have some tekst in word perfect with maths in them, and it does not come up well in open og libra or anything else than word perfect :(

So I really have to have it installed somehow in linux possibly in wine.  Know that I could use a wm but that is a bit of an effort to get up and running and maintain last time I did it.

---

### Post by iam2 on 2012-01-22
[SIZE=1]Hello Clearwood.
[/SIZE]   	 	 	 	p { margin-bottom: 0.08in; }   	 	 	 	p { margin-bottom: 0.08in; }   	 	 	 	p { margin-bottom: 0.08in; }  [SIZE=2]It is true that Open Office and LibreOffice and a score of other Word processors will open WordPerfect Documents, but that is not all I want to do.  For WordPerfect does some things that the other word processors cannot and do not do.  For example:[/SIZE]
 

 [SIZE=2]Parallel Newspaper style columns.[/SIZE]
 [SIZE=2]Columns that are parallel newspaper style, meaning the two columns are independent of each other, not sequential.  Sequential, meaning, once the first column reaches the bottom of the page the text wraps over into the other column at the top of the page.  Parallel, meaning, each column continues as its own column onto the next page.[/SIZE]
 

 [SIZE=2]Sorting by the first letter or word in each paragraph through all paragraphs in the document, so that all paragraphs are arranged alphabetically from top to bottom in a sequential order.  Open Office, Koffice, LibreOffice, and even Microsoft Office cannot do this.  Only – and only – in WordPerfect can this be done.[/SIZE]
 

 [SIZE=2]There are probably a few other unique features of WordPerfect that other processors cannot do, but that gives an idea of just two.  And those two, I depend upon in order to do the work that I do.  So, just being able to open and read a WordPerfect document in no way replaces the functionality of WordPerfect.  (Corel owes me a copy of their next Linux version or something that will work on Linux for that promotion – if they are reading this.)[/SIZE]
 

 [SIZE=2]The solution for me has been a dual boot system, and/or two separate computers linked together on an Intranet.  My Microsoft OS of choice, since it is the last OS that the user can control and reinstall with ease and without hassle or obligations to Microsoft, is, believe it or not, Windows 98.  The point is, control and ownership, and I like to control the machine I paid for and customize things on that machine the way I want them to be, not the way somebody else something thinks I should – if you get my meaning.  Enough about that. Windows98 is limited in regards to Internet use, but that is what I have Linux for.  The two work perfect together (no pun intended).[/SIZE]
 

 [SIZE=2]Also, I have a copy of Acrobat 4 that allows me to write, read, edit, and manage all PDF documents.  On Linux, all you can hope for is a PDF reader.  So, again, a Windows OS is useful.  Both Acrobat Writer and Word Perfect, with all their unique capabilities, only work in the Microsoft OS system.  [/SIZE] 
 

 [SIZE=2]However, I should mention that I have a copy of Word Perfect 12 that I was able to load on Linux using Wine, but it seems a little unstable so I only use it when I have to for short sessions of sorting, which, as was said, OpenOffice, etc. cannot do.  For the more complicated tasks I use Win98 platform.[/SIZE]
 

 [SIZE=2]I do not know about the math, but wish you well.[/SIZE]

---

