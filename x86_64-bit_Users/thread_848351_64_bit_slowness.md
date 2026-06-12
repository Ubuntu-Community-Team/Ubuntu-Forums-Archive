---
title: "64 bit slowness?"
date: 2008-07-03
forum: x86 64-bit Users
---

### Post by jwalker on 2008-07-03
Hi guys

I recently got a Dell XPS 1550 and of course threw on Ubuntu as soon as I was able to :KS. I installed the 64 bit version (for the first time) as the machine has a INTEL CORE 2 DUO T9300 processor, 4GB of RAM and a 256 MB NVIDIA card. 

But I am really suprised, the machine is not all that performacne wise. Truthfully the Vista partition really puts it (Hardy) to shame. 

All my drivers work, wireless etc, I had to upgrage the NVIDIA drivers because supposedly there was something wrong with the ones the Restricted Drivers Manager pulled down, but still, considering my specs I am a bit depressed. I'm no Vista hater but frankly why would I use anything else, I have gotten very used to Ubuntu and I really enjoy using it. It's the little things that make the difference for me. And the fact that I can see through a window when i move it around. 

But Firefox is not very quick. Things just aren't very 'instant', at least not when compared to Vista (32 bit version I believe). There's always a small delay, even when launching the 'start' menu. 

I did a file copy (4GB approx)to a portable usb drive (laptop hard drive enclosure) and Amarok just stopped responding (greyed out), then came back, then greyed out again, it repeated this until the file copy was over. 

It's been a few months since I used it but I am fairly sure things were much faster under Feisty, on a far less powerful machine. 

Am I mistaken about my processor being 64 bit? Should I go to the 32 bit version to see the difference? I am really quite suprised as to my machine's performance, I hope somebody can point me in the right direction. 

Thanks in advance

Chris

---

### Post by stchman on 2008-07-03
> **jwalker said:**
> Hi guys

I recently got a Dell XPS 1550 and of course threw on Ubuntu as soon as I was able to :KS. I installed the 64 bit version (for the first time) as the machine has a INTEL CORE 2 DUO T9300 processor, 4GB of RAM and a 256 MB NVIDIA card. 

But I am really suprised, the machine is not all that performacne wise. Truthfully the Vista partition really puts it (Hardy) to shame. 

All my drivers work, wireless etc, I had to upgrage the NVIDIA drivers because supposedly there was something wrong with the ones the Restricted Drivers Manager pulled down, but still, considering my specs I am a bit depressed. I'm no Vista hater but frankly why would I use anything else, I have gotten very used to Ubuntu and I really enjoy using it. It's the little things that make the difference for me. And the fact that I can see through a window when i move it around. 

But Firefox is not very quick. Things just aren't very 'instant', at least not when compared to Vista (32 bit version I believe). There's always a small delay, even when launching the 'start' menu. 

I did a file copy (4GB approx)to a portable usb drive (laptop hard drive enclosure) and Amarok just stopped responding (greyed out), then came back, then greyed out again, it repeated this until the file copy was over. 

It's been a few months since I used it but I am fairly sure things were much faster under Feisty, on a far less powerful machine. 

Am I mistaken about my processor being 64 bit? Should I go to the 32 bit version to see the difference? I am really quite suprised as to my machine's performance, I hope somebody can point me in the right direction. 

Thanks in advance

Chris

Yes, Core 2 Duo processors are 64 bit.  I have a C2D in my Toshiba and it is very fast running 64 bit.  My laptop only has 2GB RAM and an x3100 video card.

I although wiped Vista from the hdd.  Did you make free space for Ubuntu or use wubi?

If you must dual boot then make free space.

As far as video drivers the restricted driver manager will suffice.

---

### Post by jwalker on 2008-07-03
Hmmm I created free space I did not bother using wubi as it's a new one on me and I am comfortable using the patitioner in the Ubuntu installer. 

Are there any speed tests etc you could recommend so that I could compare with you? I certinaly wouldn't say that mine is running 'very fast'. It's not slow (although that file copy incident enraged me) but I certinaly don't want Vista to out perform it, the difference in Firefox is especially noticable in that regard :-(

---

### Post by dabl on 2008-07-03
I doubt seriously that the "64-bitness" of your system is a cause of any sluggishness.  It's probably other factors.  Maybe this will be of some benefit:

[http://rudd-o.com/archives/2007/10/02/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that/](http://rudd-o.com/archives/2007/10/02/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that/)


:)

---

### Post by tuxxy on 2008-07-03
I run x86 Ubuntu and I can confirm there are no delays - on menus or firefox and as for Amorak I use Banshee, maybe check your system before blaming Ubuntu :confused:

---

### Post by soxs on 2008-07-03
to make sure its not a problem with nautilus, try copying from harddrive to your usbpen via console:
```
R = recursiveness
v = show messages
f = force, don't ask for overwrite, just do
* = wildcard
```
```
cp -Rv /source/dir/* /target/dir/on/pendrive
```
targetdir is likly to start with /media/sda1 (last 2 chars may change)

---

### Post by Frenske on 2008-07-03
Firefox 3 memory/cpu usage is a disaster. Since I have upgraded to HH which came with the Firefox 3, surfing the internet is less fun. I can't run songbird and play songs at the same time surfing the internet using Firefox since every time something more than a text page, the computer stutters along with song.

Everything was fine when using ubuntu 7.10 and Firefox 2.

I have been given a lot of tips to stream Firefox 3 but all ineffective.

---

### Post by tuxxy on 2008-07-03
use Firefox 2 then

---

### Post by Yellow Pasque on 2008-07-03
Try Swiftweasel (link in sig)

---

### Post by soxs on 2008-07-04
[www.opera.com](www.opera.com)
works like a charm

---

### Post by jwalker on 2008-07-04
Nice stuff everyone, thanks for the suggestions, I will do some research over the weekend. 

And it's good to know my gear is 64 bit, so I am on the right track, no need to change distro, only to bang it into shape! :grin:

I did read someone else have issues with Nautilus so I may try another... whatever Nautilus is while I'm at it. 

I will be in touch! 

Also FWIW I read that a lot of people had issues with flash under 64 bit? Not me, so far at least...

Thanks again for all the suggestions.

---

### Post by javierfh on 2008-07-04
I have similar hardware and the only thing i have noticed, it is that takes quite long to boot the machine. 
I get the Ubuntu logo, and then the orange bar starts showing the progress and about 10 % it freezes for about a minute or minute and a half and then continues. That has never happened before and i wonder if it has to do anything with 8.04 or the fact that it is the first time i use ubuntu 64 bits edition.

has anyone experienced similar things?
Any tips how to fix that one?

Javi

---

### Post by soxs on 2008-07-04
> **jwalker said:**
> Nice stuff everyone, thanks for the suggestions, I will do some research over the weekend. 

And it's good to know my gear is 64 bit, so I am on the right track, no need to change distro, only to bang it into shape! :grin:

I did read someone else have issues with Nautilus so I may try another... whatever Nautilus is while I'm at it. 

I will be in touch! 

Also FWIW I read that a lot of people had issues with flash under 64 bit? Not me, so far at least...

Thanks again for all the suggestions.

Nautilus is your filmanager (the progie that opens when you go to places and select home)

---

### Post by jwalker on 2008-07-07
Hi all

I have done a bit of reading and have decided that I will not take any action. I came across a post in one thread (XP faster than Ubuntu or some such) and have decided that I will refrain from under taking any manual fixes etc. The final post in the thread mentioned is by a forum mod who advised that Ubuntu is already heavily modified for the desktop environment, and that many manual tweaks are ineffective or detriental to your machine's performance. The mod also stated (I believe) that XP is faster than Ubuntu, to a degree, situation depending, perspective wise. 

Upon closer inspection, I noted that my menu for example, takes time to load only the very first time I click it (approx 2-3 secs). But every time I click it after that, no matter how much time has passed, it appears instantly. Other applications behave similarly, taking longer loading the first time and then much loading much faster any time after that.

I have posted an image of 'top' running when copying approx 7 gig to my ntfs partition. In truth, while this was running, most applications ran solidly. I loaded up a few, including gimp, had amarok playing as well, and continued to surf the net and use my machine, without any stabilty or performance issue. The only real issue is Amarok itself, when skipping a song during this copy phase, it greyed out, was slow and sluggish and generally fairly poor at responding, especially when compared to Nautilus and the other apps. Unfortunatly when skipping a song trying to do anything else was difficult, it was almost like amarok was chewing up a huge amount of my resources. Also when skipping a song whilst not copying any major files, Amarok behaves normally. Is it a disk reading issue? The OS doesn't like too many seperate process reading the disc at once or something?

Thanks for your suggestions but I think I'd like to change my question to 'Why is Amarok so crap under Hardy'? It gobbles my resources while simply skipping a song and it won't update my iPod. It was very well behaved under Feisty. I'd like it behaving well because I have a lot of time for Amarok. 

Top from amarok changing song:

[IMG]http://img45.imageshack.us/img45/8427/amaroktopcq0.png[/IMG]

Top from the other day doing file copy - the only conclusion i can come to is skipping a song while doing a copy will cause my system to have issues. Even when this happens it still only using 50 percent of the processor, so what gives? 

Black marks to hide my secret identify, good luck detectives :)

[IMG]http://img102.imageshack.us/img102/3060/topdr6.png[/IMG]

---

### Post by DizzyTech on 2008-07-07
From experience and from the experience of others, it's almost definitely the NVIDIA card, the hard drive, or RAM/swap.  More specifically:  you need a better NVIDIA driver or your HDD is going bad.

I, myself, haven't ever had an NVIDIA card... but the drivers (especially old ones) cause a lot of problems where you wouldn't think.

Unnaturally slow OS' that go in the area of crashing and not loading things, can fall under the hard drive category.

Unnaturally slow Ubuntu that has crashing apps has to do with bad (or not enough) RAM and swap space.  Press 'Alt' + F2 and enter "gnome-system-monitor" in the dialog that appears.  Check the Resources tab in the window that pops up for the charts in the center.

---

### Post by Yellow Pasque on 2008-07-08
> But every time I click it after that, no matter how much time has passed, it appears instantly. Other applications behave similarly, taking longer loading the first time and then much loading much faster any time after that.

That's normal behavior. Hard disk seek times are given in milliseconds, while CPU and RAM times are nanoseconds. Can you say bottleneck? The good news is that solid-state drives are on the horizon and you can get small ones for a reasonable price right now that you can store OS and apps on if you want instant response.

---

### Post by Tekno_Cowboy on 2008-07-08
I have had a similar problem across mulitple distributions and systems. Try setting the CPU throtling to performance and see if your problems go away. Not as big a problem in Fedora or Mandriva, but for some reason is in Debian distros for me.
Hope that helps.

---

### Post by Yellow Pasque on 2008-07-08
> **Tekno_Cowboy said:**
> I have had a similar problem across mulitple distributions and systems. Try setting the CPU throtling to performance and see if your problems go away. Not as big a problem in Fedora or Mandriva, but for some reason is in Debian distros for me.
Hope that helps.
If you want to waste electricity and generate a lot of heat/fan noise, this is a great idea. Otherwise, let your CPU underclock/volt when it's not doing anything intensive.

---

### Post by steveneddy on 2008-07-08
I really don't know what I'm doing right, but I use an Nvidia card, run the driver from the repos, and the OSD is beautiful, FF is blazing fast and Flash 10 works beautifully on my 64 but Hardy install.

I have an 18 month old core 2 Duo laptop with 2 Gig RAM, so nothing special.

I did a fresh reinstall and polished up the GUI, added a few themes and a couple of applications.

I can say that I really did nothing special.

I even run Java iced tea from the repos and Java runs great in Firefox.

I think it may be the fact that I run most of the software from the repos and what else I have I compile from source.

Under 1 minute boot times, including logging in and 20 second shut down times.

Suspend and hibernate both work.

And, even with compiz running, it is the snappiest laptop I know of.

---

### Post by jwalker on 2008-07-09
Hi all

After even further deliberating I have decided that I will go 'down' to 32 bit, at least for the year, while the rest of the world catches up to our too-cool-for-school 64 bit ways. 

While many of you do not have any issues, I cannot say that my Dell XPS 1550 is the same. In fact, even the mouse pad has the odd issue.

So my finaly question is, how do I install 32 Hardy over the top of my 64 bit install? Without screwing up GRUB and losing my Vista partition et al?

Thanks again!

---

### Post by denisius on 2008-07-10
Cause slow working of Amarok can be SQLLite, - just change to MySQL and you will have very very fast one, that's my expirience.

---

