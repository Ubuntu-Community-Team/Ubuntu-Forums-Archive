---
title: "is there a 64bit &quot;server&quot; or &quot;minimalist&quot; install,distro?"
date: 2008-12-07
forum: x86 64-bit Users
---

### Post by binskipy2u on 2008-12-07
id love to install a 64bit server w/ lil or nothing. (and add what i want), dont care about compiz, just have a nice list of 20 apps i want, and their dependencies, codecs, multimedia, fonts etc.. 
as minimalistic as possible.. but able to see all 4 gigs of my ram.. 
any ideas? suggestions?

thanks

ubuntu or kubuntu is fine..

just want to streamline it, and ive tried installing arch i cant seem to read their user/install manual.. i must have a mental block or something lol

---

### Post by em4r1z on 2008-12-07
Search before starting a new thread:
[http://ubuntuforums.org/showthread.php?t=962048](http://ubuntuforums.org/showthread.php?t=962048)

---

### Post by iponeverything on 2008-12-07
By default the install is very lean for ubuntu server.

[http://ubuntu.media.mit.edu/ubuntu-releases/intrepid/ubuntu-8.10-server-amd64.iso](http://ubuntu.media.mit.edu/ubuntu-releases/intrepid/ubuntu-8.10-server-amd64.iso)

---

### Post by binskipy2u on 2008-12-07
can you "apt-get install say.. kde kubuntu-desktop 

or could you just apt-get the apps you want.. and let the dependencies fall where they may?

is there a "how-to" to build up a server install into a home desktop system?

hope i'm asking this correctly..

thanks

---

### Post by em4r1z on 2008-12-07
Why would you install a complete desktop environment using a minimal installation? Unless you wanted to learn about the process, it's contradictory.
Again, search before asking. This is what I'd do: [http://ubuntuforums.org/showthread.php?p=6027693#post6027693](http://ubuntuforums.org/showthread.php?p=6027693#post6027693) Use aptitude instead of apt-get.

Oh!, don't confuse a server install with a minimal install. The former contains, well, the basic server applications and a  specific kernel while the latter is just a base system you can turn into anything.

---

### Post by marcelkoopman on 2008-12-07
> **binskipy2u said:**
> id love to install a 64bit server w/ lil or nothing. (and add what i want), dont care about compiz, just have a nice list of 20 apps i want, and their dependencies, codecs, multimedia, fonts etc.. 
as minimalistic as possible.. but able to see all 4 gigs of my ram.. 
any ideas? suggestions?

thanks

ubuntu or kubuntu is fine..

just want to streamline it, and ive tried installing arch i cant seem to read their user/install manual.. i must have a mental block or something lol

I would suggest Xubuntu 8.10 for AMD64. This is really fast and small.
Give it a try here: [http://www.xubuntu.org]("http://www.xubuntu.org")

---

### Post by Washington Irving on 2008-12-09
> **em4r1z said:**
> Why would you install a complete desktop environment using a minimal installation? Unless you wanted to learn about the process, it's contradictory.

I'm not sure it's contradictory. Actually I'd like to do it because I understand that you can install openbox or fluxbox instead of gnome and then only the applications which you need and end up with a very light and fast ubuntu. I think it's a cool idea. There's a thread about doing just this somewhere on these forums I believe (customising your installation of Ubuntu from a minimal install cd).

---

### Post by awam66 on 2008-12-09
There is a 64 bit version of Fluxbuntu Gutsy Gibbon which is a minimal install.
See:
[http://releases.fluxbuntu.org/gutsy/rc/](http://releases.fluxbuntu.org/gutsy/rc/)

---

### Post by snowpine on 2008-12-09
> **awam66 said:**
> There is a 64 bit version of Fluxbuntu Gutsy Gibbon which is a minimal install.
See:
[http://releases.fluxbuntu.org/gutsy/rc/](http://releases.fluxbuntu.org/gutsy/rc/)

Fluxbuntu is not a minimal install; it's a complete Ubuntu distro using Fluxbox as its windows manager.

---

### Post by awam66 on 2008-12-09
> **snowpine said:**
> Fluxbuntu is not a minimal install; it's a complete Ubuntu distro using Fluxbox as its windows manager.

Yes, but it is small and runs on low memory systems with minimum resources.

---

### Post by snowpine on 2008-12-09
> **awam66 said:**
> Yes, but it is small and runs on low memory systems with minimum resources.

But the OP has 4gb of ram...??

Anyway, if you want to learn about a minimal install, my advice is against Fluxbuntu. It already has Openoffice, Kazehakase, Pidgin, Rox, etc. installed--not the same experience at all as building your own minimal system from the command line. More like an example of what is possible starting from a minimal install. (ps I like Fluxbuntu, not saying it's a bad distro, just not what the OP needs.)

---

### Post by Therion on 2008-12-09
Well I think what's needed is a little clarification.

Does the OP want a distro that utilizes minimal resources (e.g. RAM) or one with minimal additional software coming preinstalled?

Server-distros are light on both because they're designed, obviously, for a server; but I place them in a category all by themselves since they're not designed for desktop use.

---

### Post by bodhi.zazen on 2008-12-09
There is indeed a minimal install CD :

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

I am hoping they make a 64 bit JEOS soon, that would be awesome.

If you want something smaller, you can do a debbotstrap.

If you want you can do a server install, but you may not want apache, MYSQL, or the server kernel. In that event, use the alternate CD and perform a command line only system.

If you wish a minimal distro, as an alternate to Ubuntu see :

[http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

---

### Post by em4r1z on 2008-12-09
> **Washington Irving said:**
> I'm not sure it's contradictory. Actually I'd like to do it because I understand that you can install openbox or fluxbox instead of gnome and then only the applications which you need and end up with a very light and fast ubuntu.Yet he hinted about installing kubuntu-desktop. Neither Openbox nor Fluxbox are complete desktop environments, hence my answer.

---

