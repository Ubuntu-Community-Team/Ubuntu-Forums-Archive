---
title: "upgrade 32bit to 64bit version"
date: 2005-06-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by machetti on 2005-06-15
hi, i am a linux newbie and i currently have a 32bit version of ubuntu hoary hedgehog/kubuntu running on my amd64bit machine. i recently recieved my 64bit cds and i want to try it out. i want to know if it is possible to upgrade directly to the 64bit version without having to format my existing installation.

---

### Post by l.tambiah on 2005-06-17
Although im not totally sure on this, i would say you would better off with a fresh install. The 64bit system uses 64bit compiled packages therefore they are different to the 32bit packages. By trying or attempting to upgrade to 64bit from 32 bit you could create many dependency problems. So dont do it unless you want a unstable system.

---

### Post by Drain on 2005-06-17
I imagine that if you had seperate partitions for your /home directory (and maybe /var), that you could just pop in the AMD64 distro, have it format the / directory, and your settings and data would be just fine. If you had to compile anything extra for the 32-bit version, or mess with a lot of settings to get things running smoothly, you're probably in for a lot more work. 

[www.ubuntuguide.org](www.ubuntuguide.org) still applies for just about everything but the multimedia codecs.  :smile:

---

### Post by Haegin on 2006-10-09
I am also interested in this. I would hope to go from dapper 32bit to edgy 64bit (I have seperate /home if all goes arse over face) but I would like to do this without reinstalling. Even if it puts the laptop I'm doing it on out of action for a week. I think it sounds like a challenge and a learning experience (I used to break my linux install almost weekly just for the learning experience of fixing it...though of course at the time I called it system improvement and claimed I was trying to get some cool feature working).

So, is it possible?

---

### Post by Kilz on 2006-10-09
> **Human Prototype said:**
> I am also interested in this. I would hope to go from dapper 32bit to edgy 64bit (I have seperate /home if all goes arse over face) but I would like to do this without reinstalling. Even if it puts the laptop I'm doing it on out of action for a week. I think it sounds like a challenge and a learning experience (I used to break my linux install almost weekly just for the learning experience of fixing it...though of course at the time I called it system improvement and claimed I was trying to get some cool feature working).

So, is it possible?

I wouldnt try it. Start fresh.

---

### Post by jdong on 2006-10-09
There is no clear-cut way of upgrading from 32-bit Ubuntu to 64-bit, and the fact that apt-get can't deal with multiarch further complicates any user attempts to get it done via a sneaky way.

I'm not gonna say it's not possible.... I'm sure if you're creative enough you'll find a way to do it. However, for most, my best suggestion is to back up the /home directory and do a fresh install.

---

### Post by Haegin on 2006-10-10
Thanks for the advice but as /home is seperate I would like to give it a try just for the fun of it. If it does go horribly wrong then I can reinstall from the proper CD but for now I will try my hardest...

How does apt know what the architecture of the computer is as the repositories in the sources.list do not have anything to say which architecture they are. Does it just read it from a variable or does it just look at the kernel? If so could I compile a kernel for x86_64 and then use apt to update it?

Alternatively I was thinking I could download the edgy 64 bit cd and add it to apt then tell it to update from that and be very hopeful.

Any comments/thoughts?

---

### Post by jdong on 2006-10-10
APT knows what architecture it's being run on.

What you have to do, basically, is run dpkg --get-selections > selections.txt to save what packages you've installed. Use dpkg --force-architecture to install a 64-bit kernel, reboot into it, then remove /var/lib/dpkg and have debootstrap make a fresh root. Then, run dpkg --set-selections < selections.txt. Run apt-get dselect-upgrade to effect the changes.

This will likely end up with a unusually broken system, as some /etc and /var files are architecture specific, and also some packages might leave dangling files around.

You're best off doing the dpkg --get-selections, reformatting and installing a clean 64-bit Ubuntu, then running dpkg --set-selections. This will restore all the packages you've installed, leaving just /etc customization.

---

### Post by Haegin on 2006-10-10
Wow! Thanks - sounds like fun for when I'm bored at work...
Thank you very much for all the help you have given me with what may turn out to be a futile project. I am going to remove known problem packages and the dapper install is fairly new with only some web design tools on it so hopefully it should be ok if I'm lucky. I will post my results soon...

---

### Post by Haegin on 2006-10-11
[quote=jdong]then remove /var/lib/dpkg and have debootstrap make a fresh root[/quote]
Thanks again for all the help but what would this stage entail? Would that mean moving the root directory or is it just a debootstrap root as an environment for installing debs in?

---

### Post by kuja on 2006-10-11
If you're to the point that you're doing a debootstrap, you're better off doing a full reinstall anyway. debootstrap sets up a minimal base system,  though it doesn't do all the additional work that the installer would do for you (ie: installing a kernel, setting up grub, setting up networking, adding a user, etc, etc)

---

### Post by Haegin on 2006-10-11
The reason I am keen on doing it this way is the learning experience. I want to see if I can keep this thing going without doing a reinstall from cd. I know this will give me problems and this is partly why I want to do it. I learnt so much more with hoary and warty than I did dapper purely because more stuff broke so I had to learn how to fix it. Much more interesting. This way I should continue to learn.

I know this probably sounds stupid but I am on a gap year and want to learn as much as possible before I go to uni next year. Also as I have another computer (my desktop) it wouldn't be fatal for this laptop to be out of action for a while.

---

### Post by kuja on 2006-10-11
I agree with you there. There are very few instances which actually "need" a reinstall. Major disk/filesystem corruption and this are about the only things you would really "need" to do it for. If you're that curious about the install process, why not take the live cd and set up your system from scratch using dchroot and debootstrap? Shouldn't be hard to find a tutorial or wiki for doing it laying around. Most of the process is similar to what jdong described, just, you won't have the incompatible architecture dependent files laying around guarenteeing you a headache.

---

### Post by Haegin on 2006-10-11
Maybe that is the way to go. I just didnt want to have to reinstall but I guess it is a rather major change. Thanks for all the help and advice with this. I will go looking for a guide to a manual install.

---

