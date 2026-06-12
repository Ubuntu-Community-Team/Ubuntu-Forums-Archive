---
title: "Opera issues"
date: 2006-11-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Case_f on 2006-11-07
I'm having some issues with Opera (9.02, but it doesn't really matter anyway). I can run it just fine in chroot, there's no problem with that. But if I run it directly in 64bit, it says (in console) that 'Qt: Locales not supported on X server'. It still runs, but when I try to use accented keys, it prints out the non-accented - for example pressing accute dead key and 'a' types out plain 'a', instead of 'á'. I've tried specifying locale directly when starting Opera, I've tried several locale variants, several keyboard maps...doesn't matter. And it doesn't matter if it's shared Opera or statically linked, it's always the same.

Or alternativaly, is there at least a way to make Opera running in chroot work with file associations of the 64bit environment, so it's possible i.e. to open downloaded files directly from Transfers window in Opera? It tries to open them in the chroot environment, which of course is quite 'plain' and doesn't contain the needed applications, so it spits an error message about 'file not found' and does nothing, which is quite annoying.

Thanks for any ideas.

---

### Post by kuja on 2006-11-07
áéóúí

Hmmmm, I'm probably not doing things the way you intend, but I seem to be able to get special letters and the like spit out, in opera of course.

I'm using the US_English layouts international variant... and I get a variety of things by holding in right alt and pressing other keys. I figure I'm probably taking the wrong approach though.

---

### Post by Case_f on 2006-11-07
Yeah, it works just fine with accented characters that can be typed 'directly'. It's deadkey accents that are problematic - the dead key seems 'dead' all right when you press it, but the resulting character is not accented at all.

---

### Post by kuja on 2006-11-07
Okay, seeing as I don't really do anything with special characters when typing well, ever, it took me a while to figure out what you meant by the deadkey thing, but I'm getting the same behavior. The deadkey is in fact dead, and I also get a healthy number of error-ish messages in the terminal, as well as a wait cursor when I do things involving the dead keys. 

> 
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
Qt: Locales not supported on X server
QInputContext: no input method context available
QInputContext: no input method context available
QInputContext: no input method context available
QInputContext: no input method context available
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2


---

### Post by ispmarin on 2007-01-24
Same problem here, on ubuntu 6.10 on amd64 (64 bits version). Opera does not work properly: the transfer window does not show anything, and the progress bar appears with strange chinese caracters (well, strange to me, anyways). I use pt.BR_UTF-8 as my default locale, and seting LC_ALL to C solved the problem of the progress bar and the transfer window, but NOT the accented characters. The same opera works fine on a ubuntu 6.4. 

Any clues?

---

### Post by kuja on 2007-01-24
Thanks for the transfer window fix! That had been bugging me for months and months. How to set it globally? (I just exported it in the /usr/bin/opera script). As per the accented character problem, I've still not heard of any fix ... maybe someone on the opera forums knows?

---

### Post by ispmarin on 2007-01-25
Glad that worked for you, but this was no fix for me, because I use the pt.BR_UTF-8 locale... and the accents, not here or in the opera forums I had any luck. Still searching...

---

### Post by suribe on 2007-02-04
same for me, I can not make any tilde mark, for example: ´a´e´i´o´u
This is just in Opera, all the rest of the programs works fine. Is any way of reconfigure the qt locales?

---

### Post by John Jason Jordan on 2007-02-04
> **suribe said:**
> same for me, I can not make any tilde mark, for example: ´a´e´i´o´u
This is just in Opera, all the rest of the programs works fine. Is any way of reconfigure the qt locales?
I have several e-mail accounts and I use Slypheed for all but my university account. For the university account I use webmail. I just opened the webmail page for my university account in Opera and opened a Compose window. I could not type special characters with the usual Ctrl+Shift+u plus hex code. The same thing happens when trying to post a message here.
However, using Character Map I was able to paste in any character -- áéíóúüñ. 

I don't know why Ctrl+Shift+u does not work. I do have Opera set to UTF-8, but there must be something else wrong. Here is what About Opera says:

Version 9.00 
Build 344
Platform Linux
System x86_64, 2.6.17-10-generic
Qt library 3.3.5
Java No Java Runtime Environment installed

It is the 32-bit static .deb installed on 64-bit Edgy.

---

### Post by John Jason Jordan on 2007-02-04
I just discovered View > Encoding where you can set it to UTF-8. Now, when I press Ctrl+Shift+u it gives me code [ U ] and [ / U ] around the cursor. I'm going to see what happens if I post accented a, e, i, o, u and so on:

_E1_
_E9_
_ED_
_F3_
_FA_
_FC_
_F1_

Edit: That didn't work. Oh well. I have no idea what the problem is. I just use Firefox-64, where it works properly.

---

### Post by Colonel Kilkenny on 2007-02-05
I don't know any fixes to your issues but I'd suggest upgrading to newest build of Opera.
9.10 is last stable and newest weekly builld is 9.20. All builds since 9.00 have fixed a quite a big amount of bugs.

---

### Post by Nameless_one on 2007-02-12
How can we do that? The latest .deb available is 9.10 and the source is not available :)

---

### Post by Colonel Kilkenny on 2007-02-12
> **Nameless_one said:**
> How can we do that? The latest .deb available is 9.10 and the source is not available :)

John Jason Jordan talked about 9.00.
And there are weekly builds with version 9.20 available as a deb.

---

### Post by Nameless_one on 2007-02-12
Right you are. I had never seen the desktop team's blog with the weekly builds. 

One last thing: as I had installed Opera using simple64, I don't know how to install the fixed .deb on my amd64 edgy. I have seen many solutions but haven't really figured out what I must do exactly. My guess is to use dpkg with the --force-architecture option, but I am not sure. Am I correct?

---

### Post by Colonel Kilkenny on 2007-02-12
> **Nameless_one said:**
> My guess is to use dpkg with the --force-architecture option, but I am not sure. Am I correct?

Yep. sudo dpkg -i --force-architecture opera*something*.deb should do the trick. If you already have earlier version installed it should work without any additional packages. Although I guess it depends on whether you install static or shared version of Opera. The newest weekly is shared only but I guess we're having new build on friday and static version returns also.

---

### Post by Nameless_one on 2007-02-12
I know I might be getting annoying, but I was also wondering what a static build is, as opposed to a shared build :) 

And, about the force-architecture question, I am sorry, I read the ***please read this first*** thread a bit too late :) I found the answer there too.

Edit: and the new builds didn't solve the locale problem :( I am still typing a dead key and I get a character.

---

### Post by Colonel Kilkenny on 2007-02-12
> **Nameless_one said:**
> I know I might be getting annoying, but I was also wondering what a static build is, as opposed to a shared build :) 
Edit: and the new builds didn't solve the locale problem :( I am still typing a dead key and I get a character.

Well actually I don't know what are the differences between static and shared but it has something to do with linking the gui-libraries to the program I guess. And with shared version it's possible to make the interface look better (with Qt-themes).

But if the problem isn't fixed yet you can only hope that it will be fixed soon :(

---

### Post by Case_f on 2007-04-21
To answer my original question (it's been quite a long time, I know):

I've sort of solved this in Feisty x86_64 (so I don't know if this works in Edgy as well, sorry). First, I had to symlink the /usr/lib/locale directory as /usr/lib32/locale. This solved a few issues with accented characters not showing, and, consequently, in static version of Opera, all accented characters now work, including those typed using dead keys.
With shared Opera, which I prefer, I had to replace the libqt-mt.so.3.3.7 library placed there by ia32-libs-kde package by libqt-mt from another distro. I've used Arch Linux. You can get the qt package for Arch Linux here (or use any other mirror available) [ftp://mir1.archlinuxfr.org/archlinux/extra/os/i686/qt-3.3.8-3.pkg.tar.gz]("ftp://mir1.archlinuxfr.org/archlinux/extra/os/i686/qt-3.3.8-3.pkg.tar.gz"). Then, extract the libqt-mt.so.3.3.8 from it and place it in /usr/lib32, then point all those .so, .so.3 and so on symlinks to this new library. And voila, you can run shared Opera in 64bit Ubuntu without chroot and still type all accented characters and use dead keys to type them.

I know it's not much of a solution, more of a hack, but, you know...if it works... Note though, that you really need to get the Qt library from some distro other than Ubuntu, using the one from Ubuntu i386 libqt-mt package does NOT solve the dead keys issue.

And of course, try at your own risk (I'm using it for a few days now and didn't encounter any problems, but that doesn't mean there can't be some).

---

### Post by ispmarin on 2007-04-26
I am using the dynamic opera version on feisty amd64, and the symlink worked for removing the strange characters (boxes and squares when some accent is typed) but gave no dead keys. I think that is a little risky to change libqt-mt for the entire system, but i will give it a try. Just to note, on an old dapper amd64 box, the accents and everything else works for all the libqt-mt packages (basically opera and skype). Maybe changing with this libqt-mt... or fill in a bug report! libqt-mt-i18n should'nt handle it? 

I will post the results as soon i get to my home box.

---

### Post by kuja on 2007-04-26
It isn't QT for the whole system, only for 32-bit programs. Rather than filing it on libqt-mt-i18n, file it on ia32-libs-kde

---

### Post by ispmarin on 2007-05-01
Success! Changing the libqt-mt from arch linux worked like a charm. Now all 32bits applications that uses the libqt-mt (opera and skype, in my case) are working with all the accents. And I think (and this is just a impression) that opera is more stable, althougt a little slower. Well, before the change I already noticed that when Opera stays open  for long periods, changing tabs become a very slow process. Did anybody else noted this?

---

### Post by CoolkcaH on 2007-05-01
I did the symlink and it's working fine now.
I also notice the slow tab changing. It becomes slower with prolongued use, and sometimes it even stops responding for a few seconds.

When I load a webpage with flash (9.0.31), I always get a grey box in the flash part, and if I reload it it works. But after it's woking if I change tabs and get back, I have to reload again. Anyone experience this?

Finally, I can't get aspell to be recognised...english is not my main language so it would be handy.

---

### Post by ispmarin on 2007-05-02
Yes, sometimes the flash part become grey, mainly when switching tabs. But this is not as frequent as it was with opera 9.10 (now I use opera 9.20).

---

### Post by CoolkcaH on 2007-05-03
I gave a look to dmesg and saw lots of:
[ 5621.287162] operapluginwrap[17250]: segfault at 00000000000004d1 rip 00000000f7cf6516 rsp 00000000ffc35930 error 4

I found this thread: [http://my.opera.com/community/forums/topic.dml?id=186483]("http://my.opera.com/community/forums/topic.dml?id=186483")

It appears that flash 9.0.31 doesn't work well with opera and it's causing the slow downs. I think I have to go back to flash 7 until a new version is out.

---

### Post by Colonel Kilkenny on 2007-05-03
> **CoolkcaH said:**
> Finally, I can't get aspell to be recognised...english is not my main language so it would be handy.

"sudo aptitude install aspell-en" should do the trick. Restart Opera and it is in use automatically on textfields when you right click on them and choose "check spelling".
So the checking isn't inline checking like in newest Firefox. I'm pretty sure they'll be developing it to the next version.
Inline checking is available with UserJS. Check out my.opera.com/forums and User Javascript-section in there..

---

### Post by CoolkcaH on 2007-05-03
I have aspell installed with dictionaries but opera doesn't find them.

I noticed that with flash 9 there is a memory leak besides the sigfaults, just look at the system monitor / top.

I can't find a mirror to flash 7, can anyone post a link / send me the file? Or find a fix...

---

### Post by Nameless_one on 2007-07-05
I had a friend who is on gentoo send me his own libqt-mt.so, but it didn't work for me :( However, the library he sent me was on a path under a folder named amd64 so I am not sure it was the right one. The ArchLinux link doesn't work.  Oh, and I didn't symlink the locales directory, I don't know if that matters. Did everyone for whom the hack worked do that? 

Any suggestions in general?

---

### Post by Case_f on 2007-07-05
Link to the Arch package doesn't work, because the package got updated and the filename changed. You can find that out if you omit the filename from the link, it lists the contents of the whole i686 directory. Direct link to that package is now [ftp://mir1.archlinuxfr.org/archlinux/extra/os/i686/qt-3.3.8-4.pkg.tar.gz](ftp://mir1.archlinuxfr.org/archlinux/extra/os/i686/qt-3.3.8-4.pkg.tar.gz)

---

### Post by Nameless_one on 2007-07-05
Thank you. Still didn't work, but thank you anyway :) 

I think I did everything right, I put the library into /usr/lib32 and changed the symlinks that pointed to the old file to point to the new one. Anyway, maybe it's because of Edgy, according to [this](https://help.ubuntu.com/community/OperaBrowser), (under Troubleshooting), there seems to be something different about Edgy and libqt-mt. 

:( I think I will install the i386 Feisty once I get to upgrading.

EDIT: By the way, I still get "Qt: Locales not supported on X server" when I run opera from the console.

---

