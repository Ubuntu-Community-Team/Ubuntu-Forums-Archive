---
title: "Help full links"
date: 2016-08-24
forum: Wine
---

### Post by un4givenone on 2016-08-24
Is there any sites that help someone that is fresh to Ubuntu. I'm getting tired of trying to find answers to questions that 1. don't need the entire history of how a cmd line came into existence. 2. get answers that say "why didn't you set blah blah this way. you should have set it this way" , well i didn't set anything. fresh install and no choices, or 3. they do a mix of history and then only tell you have the cmd to fix it so thats useless to me at this point. I just want to find the short but complete answers with  complete cmd to do so. I learn doing more then reading a book and only half an answer doesn't help either. 
 Im looking for something like= How to install wine 1 open terminal by right clicking desktop. 2 type sudo "this is to set you as superuser" apt-get install "tells terminal to download and install" wine "program needed" hit enter.
any help would be nice. And yes Im frustrated over this. Im new to Ubuntu and going back to Microsoft's spy-ware isn't an option. Thank you in advance for anyone who can point me in the right detection.

---

### Post by TheFu on 2016-08-24
Welcome to the forums.

I felt your pain ... 25-ish yrs ago.  As I learned more and more about Unix and then Linux, it became clear that every system is a little different, so there aren't canned answers available.  Some background and experience must be assumed, because answering all the questions for a beginner, every time, gets extremely tedious for everyone else.

A little history is meant to help you understand "why" things are a certain way.  With that and a little more experience, you'll be able to guess how new-to-you commands work and WHY they work that way.  

BTW, Ubuntu is just Linux from a different provider than Fedora. There are slight differences, but overall, inside, they are the same.  Forget the GUI.  It seems that GUIs change every few years and learning a new way to do the same old things is a complete waste of time. Long time users don't bother - we use the shell. This is for 2 reasons - the commands we learned 20+ yrs ago almost all work the same way today and the shell versions of commands have 80%-90% more power than any GUI does.

If you stay trying to accomplish things using the GUI, you'll find fewer experts trying to help because we don't use the GUI like you do.  Linux is extremely flexible, so my system is very different from yours ... or anyone elses.  

Using sudo doesn't set you as superuser. It elevates the priviledge level for the command following it to the specific userid provided in the arguement to the command. That doesn't have to be root, but that is the default.  sudo can do so many other things it isn't funny and overly simplifying the features means people don't learn all the other fantastic capabilities that little command can provide.  Pretty much every command is like that - there is the primary, common use for it - and the 50 other things it can also do well.  The manpage for every command explains this.  Manpages are installed by default for every command on a Linux system ... but not on all systems - like most cloud VPSes don't have manpages installed. Save the storage, they think.

Lastly, Linux has a culture.  Most of that culture is made up of volunteers. Nobody here is paid and very few people creating how-to articles are being paid anywhere near the effort it demands to create a good how-to.  If I said your baby was ugly, then asked for help, what are the chances you would still help me?  Please don't call my baby ugly.

Now ... after all that, here is the advice I offer to everyone in your situation: [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux)
Learning Linux is like learning a foreign language. The amount of effort required is similar - some of the words are like those from Windows, but don't mean exactly the same thing. Some of the words mean exactly the same thing and there are lots of new words - it is a different language after all.
There really isn't any substitute for experience when it comes to learning Unix systems.  If you just want to point-n-click then you'll be stuck using about 10% of the system. That's fine, if that is all you require.  My Mom did that for years.  However, if you want/need to use the other 90% of the capabilities and power that a Unix system has, then learning the shell and CLI interface are mandatory. 

Anyway, I truly hope this helps.  After all this time using Unix, I figure I know about 10%.  My goal is to get to 15% before I die. ;)

---

