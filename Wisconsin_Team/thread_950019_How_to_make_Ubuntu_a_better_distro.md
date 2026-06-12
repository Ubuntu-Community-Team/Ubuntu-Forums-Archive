---
title: "How to make Ubuntu a better distro"
date: 2008-10-16
forum: Wisconsin Team
---

### Post by Ayuthia on 2008-10-16
I have been thinking about this for a while and wanted to gather some thoughts with the group.  I have been wondering what we can do to help make Ubuntu better.  Even though I have only been using Linux seriously since April of 2007, I have somewhat forgotten what it is like to start with Linux.  My background has been Unix so Linux was not a hard transition for me.  However, we all have different backgrounds and interests and I would like to know what you think we as a community could do to make this better.

Being a programmer and spending most of my time in the networking category, I can see that we could do a better job in pointing people to some good documentation in wireless.  I would also be nice to be able to develop some kind of "wizard" to help the new person figure out how to install something.

I would think that it would be nice to be able to have some configuration tools that are not necessarily Terminal based.  There are some advantages to using the Terminal, but to make this a user friendly operating system, some graphical tools would be nice.  The question that I have is what kind of configuration tools do you think we need?

Another thought is that we have some kind of transition document that will help a new person transition from Windows to Linux.  It could be anything like how to transition from Photoshop to GIMP and things like that.

What thoughts do you all have about this?  What areas do you think that Ubuntu/Linux can improve?  I think that we are interested in doing in making Ubuntu better because we are communicating in the Wisconsin Team so I would like to see what your thoughts are and see if there are things that we can do as a group to make it happen.  We can't let the Ubuntu developers have all the fun!

---

### Post by Liv3dN8as on 2008-10-17
I agree 100%. More GUI is definitely necessary if we want to push Ubuntu/Linux to the general user. Most people are scared to try Linux because they are afraid they won't be able to handle it because of all the horror stories they hear. But then again, with all the GUI it probably wouldn't be Linux any more.
I am not that good at programming but I will definitely post some ideas when I get some. Maybe I should let my wife have my laptop for a couple of hours and see what she thinks it needs. But she'd probably say "Windows". Ick!

---

### Post by meho_r on 2008-10-17
Maybe some kind of configuration center (something like YaST) for starters.

---

### Post by Ayuthia on 2008-10-17
> **meho_r said:**
> Maybe some kind of configuration center (something like YaST) for starters.

I did like the concept of YaST, but I did not keep suse on my laptop for too long and can't remember what was all in there. 

What kind of things can you think of configuring on a regular basis or only occasionally?  We can definitely create an application to do this.  The big question is what do we want in there?

My problem is that I know that there are things that people have a hard time recalling what I have configured in the past.

---

### Post by meho_r on 2008-10-18
We should have all that is configurable in that Control Center.

Example: To create a connection, I have to type in console: pppoeconf and then follow instructions in almost-like-MSDOS screen. Not problem for me, but a common user would like to go Control Center > Networking > Create New Connection... or similar.

If I want to see infos about my hardware, I would like to have: Control Center > Hardware where should be an entry named "Hardware info" or something like that.

Simply, YaST or Win's Control Panel concept. As a reference even kcontrolcenter comes in mind...

---

### Post by Ayuthia on 2008-10-18
> **meho_r said:**
> We should have all that is configurable in that Control Center.

Example: To create a connection, I have to type in console: pppoeconf and then follow instructions in almost-like-MSDOS screen. Not problem for me, but a common user would like to go Control Center > Networking > Create New Connection... or similar.

If I want to see infos about my hardware, I would like to have: Control Center > Hardware where should be an entry named "Hardware info" or something like that.

Simply, YaST or Win's Control Panel concept. As a reference even kcontrolcenter comes in mind...

I have started on a Hardware info version which is basically a graphical version of lspci and I have also added one for lspci, butI am currently cleaning it up.  It would be nice to have some ideas about how it should look though.

I'll have to take a look at the pppoeconf script a little further.  It is a shell script.  It should be able to be converted over to some kind of GUI version.

I will try to spend some time in suse to see what YaST looks like and see what we can do.

Another thought that comes to mind is having some kind of help wizard.  It seems that a lot of people come into the Linux world and run into problems with codecs for music and video, java, and other applications.  The part that I am trying to figure out is if it would be nice to have an application or a web page that can help guide them.  It would be nice to be able to have something that can give them information about how to get it, but it would be better if we could have them click on something and it will add the repositories needed and then install the application.  The trick is to see what can be done legally through Ubuntu.  I know that the codecs are a little sketchy, but there is medibuntu so I am not for sure about how it all fits in.

---

### Post by meho_r on 2008-10-20
Agree. Codecs can be a huge problem sometimes. And Java and flash come in mind too. There are constantly repeating "how to install flash" posts on forum. There are many walkthroughs (in fact, too many) "do this, try that"... It'll be nice to have a repo that solves all of them automatically. Don't know if it's possible though.

About creating connections, I think openSUSE can be a good reference point, but Mandriva too (maybe even better than openSUSE).

BTW, thank you for your efforts :)

---

### Post by Ek0nomik on 2008-11-04
There is no one answer to "How to make Ubuntu a better distro?"  Some people can never get their wireless working, some people can never get their display drivers functioning, some people just can't get codecs working, etc.  Ubuntu devs, imo, need to come up with a great way to collect data from Ubuntu users.  They need a way to figure out where people are struggling.  What "Ubuntu" doesn't get working from a default install.  I'm sure Ubuntu devs are collecting data on user experiences somehow, but I haven't been involved, and that's a problem.  Why haven't all users been probed for information?  A simple, quick, and effective way of getting data from users is necessary.

Also, let's not lump (and I know you didn't Ayuthia, but just saying...) Ubuntu and Linux into the same boat.  Not everyone wants Linux to be easier, but most people do want Ubuntu to be easier.  I think I have seen Ubuntu as being the one stop shop for a Linux distro.  A place to begin, to learn.

So, for me, how can Ubuntu be better?  Wireless has always been my biggest problem with my laptop.  Aside from little hacks like ndiswrapper, not much can be done without manufacturer driver support.  If you want Ubuntu to be a better distro, put pressure on companies to release Linux drivers.  Sure, they may be proprietary, but at least it's a start.  (I know Adobe offers .deb's for Flash now)

---

### Post by Ayuthia on 2008-11-04
> **Ek0nomik said:**
> There is no one answer to "How to make Ubuntu a better distro?"  Some people can never get their wireless working, some people can never get their display drivers functioning, some people just can't get codecs working, etc.  Ubuntu devs, imo, need to come up with a great way to collect data from Ubuntu users.  They need a way to figure out where people are struggling.  What "Ubuntu" doesn't get working from a default install.  I'm sure Ubuntu devs are collecting data on user experiences somehow, but I haven't been involved, and that's a problem.  Why haven't all users been probed for information?  A simple, quick, and effective way of getting data from users is necessary.

Also, let's not lump (and I know you didn't Ayuthia, but just saying...) Ubuntu and Linux into the same boat.  Not everyone wants Linux to be easier, but most people do want Ubuntu to be easier.  I think I have seen Ubuntu as being the one stop shop for a Linux distro.  A place to begin, to learn.

So, for me, how can Ubuntu be better?  Wireless has always been my biggest problem with my laptop.  Aside from little hacks like ndiswrapper, not much can be done without manufacturer driver support.  If you want Ubuntu to be a better distro, put pressure on companies to release Linux drivers.  Sure, they may be proprietary, but at least it's a start.  (I know Adobe offers .deb's for Flash now)

I am in agreement with you.  There are several different Linux distributions that cater to different types of users.  However, Ubuntu is currently known to be one of the more user friendly versions.  It is very difficult to pinpoint some of the major difficulties for each person since hardware is constantly changing.  The only thing that I have seen that provides some info back to Ubuntu is their hardware detection application (at least I think that is what it is called--I am currently in Arch...).  The application will send your hardware information to them, but it does not tell them if it is working or not.  It would be nice if they had some kind of survey to find out what people have, if it works, and what driver it is using.

It would also be nice if they had some bug reporting application that feeds into launchpad.  I am sure that there are a lot of people that run into bugs, but don't report it because they don't know how to do it.

It would be fun if the Wisconsin group could develop something to help the community.  Even if it is a matter of us updating the community docs for wireless or even developing a configuration application to help make things easier.

---

### Post by jKeats3 on 2008-11-05
What about the number of developers engaged in the project at any given time?

It seems like there are a ton of feature requests out there, but the development team is only able to bite off so much.  So what if you add a lot more developers?  From the project page at Launchpad, there are about 50 active members of the core team contributing to ubuntu, and about 80 contributing to MOTU.  ([https://launchpad.net/ubuntu]("https://launchpad.net/ubuntu"))  It seems with the huge significance and visibility of Ubuntu right now as the FOSS desktop, we could get the numbers up closer to 500,1000, likely more.  But the question is, is it possible or feasible to coordinate the development of so many individuals at once?  If not, why?  Does a different project framework need to be adopted?

Btw, if anyone has a good source of info explaning the ubuntu project and how development is coordinated, from the 50,000-foot view, I would greatly appreciate it.

---

