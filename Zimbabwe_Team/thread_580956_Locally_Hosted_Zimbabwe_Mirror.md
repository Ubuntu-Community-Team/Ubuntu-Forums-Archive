---
title: "Locally Hosted Zimbabwe Mirror"
date: 2007-10-19
forum: Zimbabwe Team
---

### Post by PlatinumPlus on 2007-10-19
I would like to believe once a locally hosted Zimbabwe mirror is setup we will have many Zim users switching to Ubuntu. There is a zw.archive.ubuntu.com repo but that is in South Africa and the connection is quite slow and it timeouts. With a local mirror, that will mean cheaper and faster downloads and I would switch most of my clients to Ubuntu just based on that fact. :KS :KS :KS :KS :KS

---

### Post by NIT006.5 on 2007-10-23
Hi,

Thanks for your comments. Yup, as mentioned in my mail to you previously, I fully agree this is something we need to do. Will keep everyone posted as and when progress is made.

As a matter of interest, when you talk about your clients, are you talking about clients on your local LAN? Or other clients outside your network? If on a LAN, there's always the possibility of setting up your own repository locally too. It doesn't necessarily have to be a full repo either - you could just update your own repo as and when updates/downloads are done from one machine. Just a thought.

---

### Post by raymond.swart on 2007-10-23
How about we chat to local ISP's to see if they are willing to "sponser" a domain for the Ubuntu Zimbabwe Site as well as space for a local repo.

I know the repo might be a long shot but whats the worst they can say, if we show Ubuntu/Canonical that we are serious the might fund a PC for us to use for the local repo, the trick would be trying to find a suitable spot for it to be setup that has    power backup as well as a decent connection to the web, obviously one of the ISP's would be the best best and who knows they might step up and surprise us... 

Worth a shot I think

Come on Ubuntu Zim lets :guitar:

---

### Post by PlatinumPlus on 2007-10-23
You will be surprised at the number of people using Ubuntu.

For some the word Linux just scares them but I think with enough awareness many will join the bandwagon.

Most people I am dealing with are on stand alone machines but if I can get the debs I can easily update their machines.

Long shot, maybe Mark S. can pull a trick or 2 :popcorn:
My fingers are crossed.

---

### Post by NIT006.5 on 2007-10-24
Thanks for all the input guys. Nice to see the forum liven up a little :)

Ok, this is where we stand at present:

We have agreed to follow HT's suggestion of using Yoafrica (if they are willing to provide free hosting). Since they're already hosting repo's for a couple of other distros (and we also found ISO's of Feisty and Fedora Core 7 on their ftp site) I think we stand a pretty good chance. In addition to this, we have been hugely impressed by the speed of their ftp site, which is a big bonus too. So, now that we know "where" we're trying to go, we're just trying to make it happen.

We have mailed Yoafrica (late yesterday afternoon) with an initial summary proposal, briefly outlining our request, and we just need to see if they'll bite. 

Not sure what everybody else thinks, but this is my idea of the "big picture" (once we have free hosting organised):

1. The official domain for Zim will be [www.ubuntu.org.zw](www.ubuntu.org.zw)
2. This domain will host the "public" promotional/advertising web site (which we will have to create, of course. RS, will you be willing to do your thing with graphics?)
3. From this web site, we should be able to offer local downloads of the latest Ubuntu release's iso.
4. The repository would be accessible on a sub-domain; something like archive.ubuntu.org.zw.
5. The site would also contain lists of other resources (both local and international) that are of interest to Ubuntu users - forums, mailing lists, irc channels, how-to's, etc. (As well as any other content we agree should be provided).

What do you guys think?

---

### Post by raymond.swart on 2007-10-24
Sounds good to me NC, and if Yoafrica don't bite maybe we should try and set up a meeting with them to see what else we can do. I'm sure we can give them credit on the site which might pay off as advertising for them.

I think we should some how get together the number of Ubuntu distro's being run in Zimbabwe as of now. The only fairly accurate method I could think of is somehow seeing how many pc's update, although I must admit I normally only update one pc then scp the updates to my other 5 ubuntu pc's, but my point being it might give us an idea how many people are using Ubuntu in Zim and might help our cause to get things rolling towards our goal.

---

### Post by NIT006.5 on 2007-10-24
We have had "some" feedback from Yoafrica, in that the person we contacted has forwarded our request to the owners of Yoafrica, as it will be their decision. Fingers crossed boys.

I don't really think there is any way to gather stats on how many PC's are running/updating Ubuntu in Zim. (a) There are quite a few users who don't post on forums or take part in the mailing list, so "asking" people wouldn't really work, and (b) There is no way to really monitor this except at ISP level probably, and then you would need to get ALL ISP's to collect that sort of info. So I don't really think we've got much hope there.

However, we'll see what the guys at Yoafrica say and then go from there. I don't think there's much else we can do but wait? But if they don't go for it straight away, as you say, we'd be more than happy to say "sponsored by Yoafrica" on the site.

Anyway, will keep you guys posted.

---

### Post by raymond.swart on 2007-10-24
Lets hold thumbs, it would be nice for Yoafrica to step up to the plate. Next we need to work on some HDD space to for the repo's.

---

### Post by NIT006.5 on 2007-10-24
I'm hoping Yoafrica will provide that space so we don't need to worry about it. :)

---

### Post by NIT006.5 on 2007-10-25
For those who haven't heard yet, Yoafrica has replied and said they would be happy to host the Zimbabwe Ubuntu repo for free!!! :KS

However, they don't have time to set it up themselves at the moment but implied that we could perhaps do it ourselves. We will obviously need to find out the logistics involved and do some research, as I personally haven't set up a repo mirror before. But the ball is rolling! :guitar:

Will keep everyone informed.

---

### Post by raymond.swart on 2007-10-26
Well done NC! 

I'm sure Mark would be chuffed to see what you've done in such a short time.

Ok so we can go ahead to get the mirror setup at Yoafrica!, maybe we could chat to someone from ubuntu.co.za to help us out to get it started and what is involved in making sure it is kept up-to-date.

Do we or Yoafrica! know how much space is involved in setting one up? and do we need Ubuntu.Updates to know there is one setup in Zimbabwe for any zim updates. 

Are Yoafrica! going to garuntee us speed and bandwith as I'm sure it is going to be used quite alot, we don't want people shying away from the zim repo because of slow speeds and or timeouts.

---

### Post by NIT006.5 on 2007-10-26
Thanks RS. 

I would think the best option is to use rsync to replicate the repo and keep it up-to-date. BUT that depends on "how" exactly Yoafrica like to do things. I did reply their e-mail and said we'd do some research first, but we'd have to work out the logistics with them of how to go about it.

I don't think space will be an issue. Yoafrica is already hosting mirrors for other distros so I'm sure they've got a pretty good idea of what's involved. Once we've got the local repo setup, we can register it and try to have it included as an official repo, but that will be at a later stage. Initially, Zim users will have to add the repo manually.

I think it would be a little bit rude if we start asking for guarentees on speed and such, since they're doing us a huge favour. However, the speed off their ftp server right now is really awesome - the best I've personally seen in Zim actually. So I really don't think we'll have any worries there either. It will *definitely* be a lot faster for Zimbabweans (as opposed to getting updates from servers outside Zim). However, to "avoid" creating a bandwidth problem for them (and us) I think we should encourage companies and such (with larger numbers of Ubuntu machines) to mirror the repo themselves as well (from Yoafrica).

---

### Post by PlatinumPlus on 2007-10-26
This is great news indeed!

From the little I know I would like to assume an Ubunut repo should be setup the same as a debian repo. But anyway this is good news indeed.

Well done guys and thanks yoAfrica :guitar:

---

### Post by NIT006.5 on 2007-10-30
Yup, ubuntu iso's appearing on the Yo ftp server. Definitely a BIG thank you to Yo!Africa for getting this moving for us.

Will be working on the web site itself as much as possible and I'm hoping to have it ready by next week Monday (but no promises!). Raymond will be working on spicing up the site graphics and giving it a "Zim" feel - really looking forward to seeing what you come up with RS! 

Thanks to everyone for all the support!!

---

### Post by NIT006.5 on 2007-11-14
Dear Zimbuntuans!

Following our initial request to Yo!Africa for free hosting of an Ubuntu site and repository mirror, they have informed us that they have decided to set up a full Linux repository, which will host mirrors for all the major Linux distributions, including Ubuntu. Yo!Africa have brought in Ray Goosen from Enet to set this up. I have been in touch with Ray and at this point he is still sourcing suitable hardware for the project and says that it might still be a while before everything is up and running. However, as I said to him, the benefits of this project will be huge to all of us, so I'm sure we don't mind waiting a bit longer.

Having agreed to host the site and domain for free, Yo!Africa then requested that we submit an 'official' application, which I have done. Raymond and I are still working on getting the site ready as quickly as we can, but as I've said before, lack of ZESA and the cost of running generators is slowing things down quite a bit. Progress is being made though.

---

### Post by PlatinumPlus on 2007-11-15
This is good news for Linux.

---

### Post by PlatinumPlus on 2008-01-03
Hi Guys

Has any progress been made?

---

### Post by NIT006.5 on 2008-01-07
Sorry for the delay. Been away.

Haven't heard anything back from Yo!Africa yet. Will let you know when I know more.

---

### Post by thembimoyo on 2008-04-07
I did a quick search and found [http://www.ubuntu.com/getubuntu/mirror](http://www.ubuntu.com/getubuntu/mirror)

---

### Post by NIT006.5 on 2008-04-13
Thanks Thembi.

I'm sure it's not that hard to set up a mirror, however I think the problem is just server storage space and obviously making sure that wherever the server is located, there is enough bandwidth to support the mirroring itself as well as the downloads carried out by Ubuntu users.

I checked with Ray a few weeks back and he told me that he was just waiting for the "storage capacity" from Yo!Africa. Since they've offered to do this for free, I can't be too pushy. Also, I don't think anyone else would be in a position to do it instead since it will require a lot of bandwidth etc.

And of course, in addition to this, I think a lot of people are holding back on certain projects in Zim until things have settled down here and everyone knows what's going on. 

I'm sure we'll win with the repo eventually though.

---

### Post by tkmunzwa on 2008-06-20
Yo! Africa is proving to be quite friendly to free software. Thanks dudes.

---

### Post by NIT006.5 on 2008-07-15
For those who haven't kept up with the updates on the mailing list, we are much closer to our goal now!

The server is in place and is currently replicating the repos for Ubuntu, CentOS and Debian. As I understand it, the shear volume of data involved did cause some bandwidth issues, so it has now been throttled down a bit, but is still busy replicating. Once the initial replication has been done, it should be a lot simpler as it will be only replicating "new" packages and updates, etc. So as soon as the initial replication is complete, we should be in business.

Thanks again to Kalpesh, Simpson and the other guys at Yo!Africa for pushing this, and of course to Ray for doing the repo work. Official letters of thanks have already been sent to those concerned.

I have also spoken to the Computer Society of Zimbabwe who have agreed to give us a slot in their monthly electronic newsletter, so once the repo and web site are up and running, we will place an "official" launch notice in their newsletter as well.

---

### Post by tkmunzwa on 2008-07-16
*cool!*. My thanks to all those involved.

you guys **rock**

---

### Post by NIT006.5 on 2008-08-09
Hi guys,

We are extremely pleased to announce the launch of the new Zimbabwe repository!

The repository can be accessed on [http://archive.ubuntu.org.zw](http://archive.ubuntu.org.zw) (this address will need to be added into your sources.list).

We are working on getting the mirror officially approved, and then hope to make it the default repo for Zimbabwean users. Until then however, if you require any assistance in setting your system up to use this repository, please send an e-mail to [email]repo@ubuntu.org.zw[/email] or ask for help here on the forum.

An announcement of the repo launch has also been sent to CSZ for inclusion in their August newsletter. 

Thanks again to all those involved in making this happen.

---

### Post by rgchihanga on 2008-10-11
is there a chance that there is going to be the dvd version of ubuntu on the mirror

---

### Post by NIT006.5 on 2008-10-13
> **rgchihanga said:**
> is there a chance that there is going to be the dvd version of ubuntu on the mirror

Hi,

Which dvd version are you referring to? Ubuntu is distributed on CD by default... the CD iso images are available at [http://archive.ubuntu.org.zw/ubuntu/iso/](http://archive.ubuntu.org.zw/ubuntu/iso/)

The Intrepid iso's will be available there shortly after the official release, as we'll need a little time to have them downloaded onto the local server.

Regards,
Neil

---

### Post by PlatinumPlus on 2008-10-21
> **NIT006.5 said:**
> Hi guys,

We are extremely pleased to announce the launch of the new Zimbabwe repository!

The repository can be accessed on [http://archive.ubuntu.org.zw](http://archive.ubuntu.org.zw) (this address will need to be added into your sources.list).

We are working on getting the mirror officially approved, and then hope to make it the default repo for Zimbabwean users. Until then however, if you require any assistance in setting your system up to use this repository, please send an e-mail to [email]repo@ubuntu.org.zw[/email] or ask for help here on the forum.

An announcement of the repo launch has also been sent to CSZ for inclusion in their August newsletter. 

Thanks again to all those involved in making this happen.

This is great news!

---

