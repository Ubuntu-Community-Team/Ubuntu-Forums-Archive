---
title: "OpenSUSE 11.0 RC 1 announced"
date: 2008-06-02
forum: openSUSE and SUSE Linux Enterprise
---

### Post by plun on 2008-06-02
A bug free Hardy is soon out....:)

[http://news.opensuse.org/2008/05/29/announcing-opensuse-110-rc-1/](http://news.opensuse.org/2008/05/29/announcing-opensuse-110-rc-1/)

- Yast2 seems to be great.  No "hidden" installs.  Really mainstream focused
and what a main stream user wants.


- The upper panel is also removed in Gnome,  AWN...?


- I am also goint to check their standard media package solutions, Totem is rather "out of order" for the moment and VLC and MPlayer just works including plugins for Firefox 3.  At least in Europe and our solutions,
often with proprietary streams. (its a commercial world)


Looks nice anyway....:)

---

### Post by olskar on 2008-06-02
Don't you think this would be better to place in the Community Cafe-thread for example? ;)

---

### Post by ronacc on 2008-06-02
Since OpenSuse 11.0 is still in developement and more comparable therefore to Intrepid this is probably the right place to discuss it .
@Plun  I had not noticed the top panel thing , I've got KDE4 for the WM on my OpenSuse install:lolflag:

---

### Post by plun on 2008-06-02
> **olskar said:**
> Don't you think this would be better to place in the Community Cafe-thread for example? ;)

No....

In the cafe they discuss complete different issues... O:)

They also directly turns it to a KDE vs Gnome battle.

or worse Ubuntu vs OpenSuse battle....:(


I think OpenSuse is more "main stream focused" and Ubuntu more
"introvert" so its details which must be discussed.


MarkS also proposed a synch for major dists and to be the first dist is maybe hazardeous beacuse of all bugs....

Heavy devs also works for Redhat or Novell.


So lets check OpenSuse and find out how they solved things and 
diffs to Hardy/intrepid.


Hopefully "Happy newbies" in the end  :lolflag:.... much more important then an old happy conservative Ubuntu users since Dapper....:)

---

### Post by ronacc on 2008-06-02
It would indeed be great if "open source" distros would learn from each other , sadly I have found this rarely to be the case . Yes we compete with each other but for the good of "open source " in general a little less "Not Invented Here"  syndrome would be nice.Constantly reinventing the wheel wastes time and resources .

---

### Post by 23meg on 2008-06-02
> **ronacc said:**
> It would indeed be great if "open source" distros would learn from each other , sadly I have found this rarely to be the case . Yes we compete with each other but for the good of "open source " in general a little less "Not Invented Here"  syndrome would be nice.Constantly reinventing the wheel wastes time and resources .

Any specifics (from Ubuntu and OpenSUSE perhaps)?

---

### Post by plun on 2008-06-02
> **23meg said:**
> Any specifics (from Ubuntu and OpenSUSE perhaps)?

Well.. I have some specific issues to check.


- The "famous" opening/mounting an ISO file... :)


- I take [Elisa]("http://packages.ubuntu.com/intrepid/elisa") as an example....

How can a  newbie find the ugly package.... ?    

Add/Remove compared with Yast.  Also compare it with PackageKit.



- Change workgroupname ? :)   gnome-system-tools and Ubuntus famous solution.


- Media package solution including dirty codecs and addons/plugins for Firefox.  


- Compiz ingegration


- Network-manager including wireless and UMTS/GPRS connections.


Just a start....:)

---

### Post by ronacc on 2008-06-02
> **23meg said:**
> Any specifics (from Ubuntu and OpenSUSE perhaps)?

I will give you 2 right off the top of my head that I personaly know to be true not anecdotes .
 1 Gdesklets , broken for 64bit since atleast Fiesty  in FC8 (alpha) I found this app to work solidly in 64bit I and many many others had been filing bugs on this to no avail so I tried extracting the FC8 RPM and replacing the ubuntus gdesklets with fedoras , it worked , I emailed the rpm to the dev for him to examine , result ,still broken in ubuntu . 
 2 the wireless card I have in one box for testing purposes (rtl8185) does not work in stock Ubuntu (gutsy,hardy,intrepid) OpenSuse 11.0 LIVECD found it configured it and I was connected using it as soon as the desktop loaded , no config no ndiswrapper no BS just connected. and as a 3rd particular look at the hoops ubuntu forces us to jump through to have a working Nvidia driver .

---

### Post by 23meg on 2008-06-02
[QUOTE=ronacc]1 Gdesklets , broken for 64bit since atleast Fiesty in FC8 (alpha) I found this app to work solidly in 64bit I and many many others had been filing bugs on this to no avail so I tried extracting the FC8 RPM and replacing the ubuntus gdesklets with fedoras , it worked , I emailed the rpm to the dev for him to examine , result ,still broken in ubuntu .[/QUOTE]

Packaging is one area that's crying for more inter-distro collaboration. There's a project with participants from many distros dedicated to investigating ways of using dVCS to collaborate on package maintenance: [http://vcs-pkg.org/](http://vcs-pkg.org/)

[QUOTE=ronacc]2 the wireless card I have in one box for testing purposes (rtl8185) does not work in stock Ubuntu (gutsy,hardy,intrepid) OpenSuse 11.0 LIVECD found it configured it and I was connected using it as soon as the desktop loaded , no config no ndiswrapper no BS just connected.[/QUOTE]

In what way do you think this is this connected to NIH syndrome / reinventing the wheel?  

[QUOTE=ronacc]and as a 3rd particular look at the hoops ubuntu forces us to jump through to have a working Nvidia driver .[/QUOTE]

What hoops? It's pretty simple with Jockey, which happens to be a rewrite focusing mainly on being agnostic regarding distros and desktop environments, and can be used by other distros in the near future.

---

### Post by RAOF on 2008-06-02
> **plun said:**
> ...
- I take [Elisa]("http://packages.ubuntu.com/intrepid/elisa") as an example....

How can a  newbie find the ugly package.... ?    

By installing elisa with add/remove, and having the ugly package automatically installed?  Apt now treats Recommends: as dependencies by default, so this should just work.

> **plun said:**
> 
Add/Remove compared with Yast.  Also compare it with PackageKit.


- Change workgroupname ? :)   gnome-system-tools and Ubuntus famous solution.


- Media package solution including dirty codecs and addons/plugins for Firefox.  


- Compiz ingegration


- Network-manager including wireless and UMTS/GPRS connections.


Just a start....:)

There isn't any *content* in this list - with the exception of some network-manager features which intrepid will almost certainly have by virtue of including the (presumably available) new 0.7 release.  

Take: > Add/Remove compared with Yast.  Also compare it with PackageKit.  *This doesn't say anything*!  A useful statement would be something like "I find PackageKit's inability to install multiple packages at once annoying, but it has a clean interface.  Add/Remove doesn't show enough information, and has slow search.  Yast frobs the knobs 25% faster than both".

---

### Post by LaRoza on 2008-06-02
Moved to OpenSUSE forum.

---

### Post by ronacc on 2008-06-02
> **23meg said:**
> 

In what way do you think this is this connected to NIH syndrome / reinventing the wheel?  




What hoops? It's pretty simple with Jockey, which happens to be a rewrite focusing mainly on being agnostic regarding distros and desktop environments, and can be used by other distros in the near future.

even puppy linux handles most wireless cards with more ease than Ubuntu .We are still trying to "invent " a way that works .


If jockey happens to correctly detect your card correctly and if it happens to be working for your card at that particular instant its not too many hoops if burps however it wipes out your xorg.conf . I can and do handle this when necessary but that is not "user friendly behavior".

---

### Post by 23meg on 2008-06-03
[QUOTE=ronacc]even puppy linux handles most wireless cards with more ease than Ubuntu .We are still trying to "invent " a way that works .[/QUOTE]

So you've tried both with "most wireless cards"? Have you investigated how exactly Puppy does this and whether/how Ubuntu can benefit from their work? 

[QUOTE=ronacc]if burps however it wipes out your xorg.conf .[/QUOTE]

That's a bug, not "NIH syndrome". File it.

---

### Post by ronacc on 2008-06-03
> **23meg said:**
> So you've tried both with "most wireless cards"? Have you investigated how exactly Puppy does this and whether/how Ubuntu can benefit from their work? 



That's a bug, not "NIH syndrome". File it.

I have not investigated how puppy does it and I have only tried it with the 3 wireless cards that I have , the score there is puppy sees all 3 and uses 2 by just telling it to connect the third (eeepc) requires either certain versions of puppy or some tweeking ,Ubuntu sees 2 uses 1 (the eee with a specialised version) the 3rd (rtl8185) it dont even see but hardinfo does show it.

actualy its "failalways X" that does, the dammage jockey just precipitaes the disaster by failing to load the driver (or not having the right one).and I did file on it, I'll look up the bug# later.


edit: bugs I have filed against RM/jockey   105285   184988   190090

---

