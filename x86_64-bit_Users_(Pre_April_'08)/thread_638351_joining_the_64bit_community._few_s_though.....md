---
title: "joining the 64bit community. few ?s though...."
date: 2007-12-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by -MoonDoggie- on 2007-12-11
i've been getting my feet wet in linux for a very short amount of time, and am very excited to be trying out Ubuntu now. 

here's the thing: i still don't know to much about linux, and i'm basically taking a "hold my beer" approach  to this and running into 64bit computing balls out.....the good thing is i'm a fast learner, i'm kinda having fun at the idea of venturing into something i know nothing about, and vista has given me the drive to tell it to go f....well ya get the picture. 

anyway, i choose to go with 64bit because i figured if i'm gonna do this, i might as well do it right. here's the questions:

1. i'm downloading an Ubuntu iso through bit torrent. i made sure its the right one and all, its just that it's a dvd version and so its around 4gigs. i looked around the ubuntu site and they dont seem to offer a 4gig iso download. so, i'm guessing this iso i'm downloading is just jam packed with software. does anyone reccommend this? or should i just get the one off the main site?.....at 20-30kb per second......

2. can anyone inform me on weather wireless networking will work right off the bat? currently thats the only way i can access the internet and i need to be able to look at the guides while i mess with this thing. i guess i can find out for myself with the live cd tomorrow though......


too much writing huh? well fortunately thats all for now. thanks in advance for any replies.

---

### Post by Melcar on 2007-12-11
4 gigs!! Damn, that's huge.  The image file is a mere 697MBs.  Just get it off the main site.  As for wireless, it depends on your particular device.  Try it out first as a LiveCD and see if it works.  I know for a fact that most (probably all) Broadcom chips do not work (they need ndiswrapper or firmware hacks).

---

### Post by dfreer on 2007-12-12
There are official torrents available of pretty much every release (amd64, i386, feisty, gutsy, CD, DVD, etc etc), and there is almost always seeders around, however you have to dig for them.

---

### Post by rsambuca on 2007-12-12
Unless you won't have an internet connection after you install, then I wouldn't waste my time on the DVD.  Anything you want or need from the repositories can be quickly installed in seconds or a few minutes at most.  No need to waste your time downloading a bunch of stuff you will likely never want nor need.

---

### Post by -MoonDoggie- on 2007-12-12
phew, thank goodness. guess that's what i get for not fully exploring the downloads page.......thanks for the responses.

as for the wireless thing, yes i have BroadCom. sabayon linux didn't want to work with it either. guess it applies to all distributions.....well i've seen a few guides here and there to get it working so it shouldn't be too bad. 

one other thing, i was reading the article linked in the announcements topic about 64bit computing and another question has popped up:

1. in the article it stated that with being allowed to utilize 4gigs of ram, it becomes more of a "necessity" than a "luxury". so would only having 2gigs of ram hinder processes in 64bit? it wouldn't really make sense to use 64bit when 32bit would actually turn out to be more efficient.

again thanks for the responses and any future replies.

---

### Post by rsambuca on 2007-12-12
> **-MoonDoggie- said:**
> phew, thank goodness. guess that's what i get for not fully exploring the downloads page.......thanks for the responses.

as for the wireless thing, yes i have BroadCom. sabayon linux didn't want to work with it either. guess it applies to all distributions.....well i've seen a few guides here and there to get it working so it shouldn't be too bad. 

one other thing, i was reading the article linked in the announcements topic about 64bit computing and another question has popped up:

1. in the article it stated that with being allowed to utilize 4gigs of ram, it becomes more of a "necessity" than a "luxury". so would only having 2gigs of ram hinder processes in 64bit? it wouldn't really make sense to use 64bit when 32bit would actually turn out to be more efficient.

again thanks for the responses and any future replies.

That article is incorrect.  Do you have a link to it? - I would like to see it.  1GB is plenty for most desktop use.

---

### Post by -MoonDoggie- on 2007-12-12
here's the article link, swiped from the "advantages and disadvantages" sticky thread: [http://www.bit-tech.net/bits/2007/10/16/64-bit_more_than_just_the_ram/1](http://www.bit-tech.net/bits/2007/10/16/64-bit_more_than_just_the_ram/1)

and here is the page its found on: [http://www.bit-tech.net/bits/2007/10/16/64-bit_more_than_just_the_ram/5](http://www.bit-tech.net/bits/2007/10/16/64-bit_more_than_just_the_ram/5)

look under "it's not all beer and skittles", second paragraph.

---

### Post by rsambuca on 2007-12-12
That 5 - 10% looks about right, but since linux is very efficient with resources, it isn't as big a deal as the writer seems to think. I have 1GB and have never touched my swap yet.

---

### Post by Jouke74 on 2007-12-12
Ubuntu 64 bit will work easily down to 512 Mb. From there until 128 Mb it will require some tweaking for good performance, or for example use Xubuntu. Lower than 128 mb I would not advice the use of the latest Ubuntu's anymore. 

From the 2 GB internal memeory I have I use about 200 mb on average with Xubuntu AMD64 (I like XFCE).

If wireless needs to be set-up without any internet connection make sure you have the right files downloaded before you wipe your system partition of your harddisk empty :) Or make sure you have access to internet through another way. You will probably need internet help to get everything running.

---

### Post by kuja on 2007-12-12
> **rsambuca said:**
> Unless you won't have an internet connection after you install, then I wouldn't waste my time on the DVD.  Anything you want or need from the repositories can be quickly installed in seconds or a few minutes at most.  No need to waste your time downloading a bunch of stuff you will likely never want nor need.

I disagree, the DVD *does* have a few perks, one of them most notably being that it is both the alternate and the regular installer in one, and will also let you install a relatively basic cli system too.

---

