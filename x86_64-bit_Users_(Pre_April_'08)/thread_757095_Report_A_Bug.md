---
title: "Report A Bug"
date: 2008-04-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Thomas_Klaus2 on 2008-04-16
Hello, I had a problem with 7.10:
[http://ubuntuforums.org/showthread.php?t=754782](http://ubuntuforums.org/showthread.php?t=754782) (2 Days ago)

So I made a new installation. Purely with the standart Sources list, exception:
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non free, (only 1 item : libdvdcss2).

But 7.10 AMD64 ist often hanging (PS one time during this post) in Firefox, Thunderbird, Openoffice ... almost every application for about 10 seconds (Mouse moves, but thats all).
(I also had this Problem with my last 7.10 installation, but not this often)

Its a Fujitsu-Siemsens Esprimo AMD64x2 3GB RAM...

Thats terrible when you use 7.10 AMD64 for working on other things that wont work.
And you have to report a unspecific bug too.

Thomas_Klaus2

---

### Post by Thomas_Klaus2 on 2008-04-17
Thank you for so many beneficial hints after 21 hours.
But I cant go on working with this (30 times 10s stops during an hour).
Ill try the 32 version on this new pc (The third new Ubuntu installation since 3 weeks)
Im not interestet to use my 5 stable Windows 32 versions or Vista 64 for home office , but for special applications like virus testing 
(You can test the incoming viruses with Qemu too. The HD is replaced in 2 minutes.I didnt arrive to install bitdefender on qemu,
so I have to check for the name on real Windows) ,or explore2fs.exe, since I changed to Debian32, later Ubuntu 32 , both stable,   five years ago.

---

### Post by dje on 2008-04-17
Reporting a bug on the forums won't do much, [URL="https://launchpad.net/ubuntu/+filebug"]report bugs on launchpad
[/URL]
> Thank you for so many beneficial hints after 21 hours.
Sarcasm won't do you any favours in getting this problem fixed, everyone on the forums help in their spare time out of their own free will

dje

---

### Post by Thomas_Klaus2 on 2008-04-18
sorry, I only wanted to advise that such problem exists. Im sarcastic too, unfortunately.
Especially when everything seems buggy: Not only my OS.
Once, looking for the 64 subforum I found much links with "report a bug". Later, when
I was looking for "report a bug" I only found the 64 forum, without making a longer excursion. Maybe a 64 developper will read this randomly even when placed here.
Intending to install the 32 version of 7.10, just waiting for the next massive appearance
of my "report a bug", the 10s stops were getting rare. I thought they disappeared for an hour yesterday: But they are still here, Today not as often as yesterday. I had it 5 lines ago again...
Thank you

---

### Post by Thomas_Klaus2 on 2008-04-20
Hi,

the 10s Stops are going on. During the european nights the 10 second stops are much
more frequent then during the european daytime. Recently I was on a support page,
but I found just empty windows. Then I realized that this page requires flash player.
5 days ago by installing 7.10 AMD ,flash was working.So I tried apt-get --reinstall install
flashplugin-nonfree, or even apt-get remove flashplugin-nonfree and take the player from adobe without success, because there were only 32 players. By the way sometimes npviewer is killing firefox (dont remember to have ever choosed npviewer, maybe a side effect), later a grey window appears, seeming to show that npviewer is trying something. I have to close it. Theres also no other package then
"standart" installed or automatically updated, as I already said. The 10 second stops
maybe a X-Error, but where do I find the right xerrorlog again?

Rg. T_K2

---

### Post by Thomas_Klaus2 on 2008-04-22
Hi,
now theres tree days ago when I replaced 64 by 32.

First I had to start the 32 live CD 3 times until a visible mouse pointer appeared.
(Thats maybe not a good first impression for a OS thats in fact better than Windows..., for a newbie)

Then the maximum screen resolution was 800x600, so for installing 7.10 32 OR 64 the normal way, the buttons "forward" or "next" or ... were invisible or out of range to reach by mouse (The last seven installations, for different reasons,
I used random key combinations I forgot to pass this). Now I know that you can put the top panel AND the botton
panel to left and right with "properties". So a small part of the button "forward" gets visible and reacheable.

The installation part was OK.

Then, leaving on "Live CD", I tried to put the former top-panel from the right to the top again.
But I didnt find a point to get "properties" again (When I left pushed "System" on the right panel: "Evolution..." appeared)
Then I removed "Applications" to get a point for the mouse right click to get panel "properties" again.
I got "properties" again and the right panel moved to the top again, but the items "Applications" and
"Places" and "System" have disappeared. So I choosed "add to panel" and finally "Main Menu", after a while,
to get sth. similar to the former "System". There were many tries until this.

After tree days the stops (mouse moves but nothing else works) on 32 are still there. But not this often as on
64. They are more rare, the stopping time is about 3 to 7 seconds on every application from qemu to firefox, even on
pure gnome, on this Fujitsu-Siemens Esprimo AMD 64x4800 3GB RAM. It seems they appear especially when I make a mouse action without skill. Its tolerable: Flash still works and npviewer never called again (After 3 days!!!). 

If I had a little less to do with my own problems on Fujitsu-Siemens Esprimo AMD 64x4800 3GB RAM and 7.10 AMD64 and 32, and how to report them exactly, Whenever theres not enough time to show the whole way and situation, I would welcome to check other reports.

I installed avira Antivir on the Win2000 emulator with success, so I can get the Virus names now without changing to real Windows before finally.

---

### Post by Kilz on 2008-04-22
> **Thomas_Klaus2 said:**
> 

After tree days the stops (mouse moves but nothing else works) on 32 are still there. But not this often as on
64. **They are more rare, the stopping time is about 3 to 7 seconds on every application from qemu to firefox, even on**
pure gnome, on this Fujitsu-Siemens Esprimo AMD 64x4800 3GB RAM. It seems they appear especially when I make a mouse action without skill. Its tolerable: Flash still works and npviewer never called again (After 3 days!!!). 



You are not the fist person to move to 32bit hoping that it would solve all your problems only to find that it doesn't.
So now you not only do you have the problem, you have a operating system that isnt right for your hardware.
To me it sounds like a hardware issue. perhaps bad ram, did you run the memtest on the install disk?

---

### Post by Thomas_Klaus2 on 2008-04-24
Good idea, I wanted to run the memtest too (Wihtout expecting any error).
But after 11 hours theres no error displayed.

I finally changed 64 to 32 because Flashplayer has disappeared after 3 days.
And I wasnt in the mood to find Flashplayer again. 
(By the way, two months ago Flashplayer disappeared on 32 with a Ubuntu update. I couldnt do anything then remove flashplugin-nonfree, retart and get
the flasplugin-nonfree from adobe, and to avoid this update later. To make
flash working again.) Maybe posting a new thread? 
The odd npviever was already calling since 2 days, taking all system resources, I dont know for what reason.
This ubuntu state is terrible if theres a lot of work to do.
(Maybe only viewing a support page that must be in flash)
For moderate work (as now) its tolerable.

thank you

---

### Post by Thomas_Klaus2 on 2008-05-26
Hello,

it was cause the nvidia 3D accelerator doesnt work well with gutsy. 
The same works perfect with hardy: No more OS problems.

Kind Regards,

Thomas_klaus

---

