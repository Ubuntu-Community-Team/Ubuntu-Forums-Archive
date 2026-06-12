---
title: "Java/Firefox"
date: 2007-11-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by veritas366 on 2007-11-05
Sometimes searching returns too MUCH info...and this is a double post from the general help area before I found this one....so apologies.

I have an amd64 chip and Ubuntu for the 64 bit. Right now, even using the blackdown java plugin for firefox doesn't seem to work.  I will try again but I think I followed directions okay.

So, what do I miss out on if I go and get the 32 bit version of ubuntu and just use that instead?  This is a new install and though I hope to make it my primary OS, until the java works I can't even consider that.  

Alternately, I've seen some scripts for pulling in the 32 bit Firefox and then adding all java that way but it seemed complicated to me.  The thread was about 116 pages long (which is one reason I said my searches gave me too MUCH info) and people were having various problems and the script was for other things like Flash which I think works in Gutsy...

---

### Post by saru411 on 2007-11-05
I'm not sure if kilz scripts work for gutsy but they work very well under feisty. I do not plan on upgrading before the Christmas break so i will not know until then anyway. Anyway, Kilz has written install scripts for java and flash in frefox(and a few other flavors of firefox, my fav being swiftweasel). You should follow his guides. They work flawlessly

---

### Post by veritas366 on 2007-11-05
Thanks for the reply.  I tried to follow directions but had the following result.  When I did what I think Kilz referred to as the "base install script" the terminal crashed to desktop.

I got as far as the following:

I was able to chose which version of ubuntu.
I was able to choose "6" when it asked which browser you want to install. That was a little confusing because six options were listed but it said choose 1 - 5.  6 was what I thought I was to choose as it was the one that said I'll install a browser later.

Then it asked if I wanted flash plugin and I said yes.  Java six and I said yes and then mplayer plugin I said yes.

Then it said it needed my username and I entered it and it crashed to desktop.  No error...the terminal just disappeared.

I tried three times.

If this is a problem someone else has had I'd appreciate hearing about it.  I can't figure out how to search a particular thread vs a whole topic so when I search I just get the entire 116 page thread on the topic.  

I may just put 32 bit ubuntu on here and be done with it, unless that leads to other issues?

---

### Post by Kilz on 2007-11-05
> **veritas366 said:**
> Thanks for the reply.  I tried to follow directions but had the following result.  When I did what I think Kilz referred to as the "base install script" the terminal crashed to desktop.

I got as far as the following:

I was able to chose which version of ubuntu.
I was able to choose "6" when it asked which browser you want to install. That was a little confusing because six options were listed but it said choose 1 - 5.  6 was what I thought I was to choose as it was the one that said I'll install a browser later.

Then it asked if I wanted flash plugin and I said yes.  Java six and I said yes and then mplayer plugin I said yes.

Then it said it needed my username and I entered it and it crashed to desktop.  No error...the terminal just disappeared.

I tried three times.

If this is a problem someone else has had I'd appreciate hearing about it.  I can't figure out how to search a particular thread vs a whole topic so when I search I just get the entire 116 page thread on the topic.  

I may just put 32 bit ubuntu on here and be done with it, unless that leads to other issues?


Choosing to install a browser later will only install the 32bit plugins. You will still need a 32bit browser to use those plugins, they will not work with the 64bit browser that comes with Ubuntu. You can chose any of the browsers linked to on the howto page. But only those packages will work with the plugins you installed. 
It did not crash the desktop. If you start a script by double clicking on it and choose run in terminal, when it is finished running the terminal closes. If you want to keep the window open, navigate to the script and start it with ./scriptname .

---

### Post by orthopod on 2007-11-05
He even states that you shouldn't.   On Gutsy, you should be able to get flash by choosing it in Synaptic

I got java to work (most of the time),  by choosing  the iced tea java version  (select packages,iced tea; bin, jre and plugin)

see also
[http://ubuntuforums.org/showthread.php?t=580792&highlight=java](http://ubuntuforums.org/showthread.php?t=580792&highlight=java)

---

### Post by saru411 on 2007-11-05
iced tea= no security. i would prefer to use the 32 bit java applet and browsers than run the risk of opening a site that erased my hard drives!

---

### Post by veritas366 on 2007-11-05
So far, I've only tried hushmail and it didn't work with iced tea so I know that doesn't work for me.

Thanks for the information about crashing to desktop not being crashing to desktop.  It asked for my  username so I was expecting it to ask for a password. Since it didn't I assumed it hadn't finished.

Also, I'm a little slow and the Flash issue is confusing.  I'm installing Firefox in a sort of different way, but I can still use the flash that's in the repos without having to use the script?  I think that's what you were saying.  Looking forward to trying it.

---

### Post by Kilz on 2007-11-05
> **veritas366 said:**
> So far, I've only tried hushmail and it didn't work with iced tea so I know that doesn't work for me.

Thanks for the information about crashing to desktop not being crashing to desktop.  It asked for my  username so I was expecting it to ask for a password. Since it didn't I assumed it hadn't finished.

Also, I'm a little slow and the Flash issue is confusing.  I'm installing Firefox in a sort of different way, but I can still use the flash that's in the repos without having to use the script?  I think that's what you were saying.  Looking forward to trying it.

You can use the flash in the repos (wrapped 32bit flash). But thats not what you installed with the script. 

Also you cant use the java or any of the plugins the script installed with any other browser but a 32bit one. You need to install one of the browsers on the howto page, you cant get a 32bit browser from the repos.

---

### Post by veritas366 on 2007-11-05
> Also you cant use the java or any of the plugins the script installed with any other browser but a 32bit one. You need to install one of the browsers on the howto page, you cant get a 32bit browser from the repos.

Okay...I got that part.  And I was pretty sure about the Flash part..

I haven't had a chance to switch over and try these things yet.

---

### Post by rsambuca on 2007-11-05
> **veritas366 said:**
> 

If this is a problem someone else has had I'd appreciate hearing about it.  I can't figure out how to search a particular thread vs a whole topic so when I search I just get the entire 116 page thread on the topic.  

There is a link that says "Search this thread" for all threads on the top right side of the page.

---

