---
title: "32-bit Totem w/ w32 on amd64"
date: 2007-04-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Anaximander Thales on 2007-04-26
I have searched several times, I've looked through the 32-bit mplayer tutorial, I've looked at 'how to get 32-bit programs to work on 64-bit archs (the sticky tutorial at the top of x86 64-bit user).'  I've not seen anything that really addresses 32-bit totem.  So, my attempt will be to either write a tutorial, or to add a post to one of the existing tutorials on how to get totem 32 working on amd64.

I understand that other feel the mplayer is the best, and other feel that vlc is the best, and some others will prefer to use xyz program.  I just prefer totem.  It's a minimalist design, it's quick and it has a simple interface.  Sure the other programs can be modified much more, but I just like the look of totem (in fact that's the only negative I have about it -- the options menu is severely lacking), and it does what I want how I want it.

This is the great thing about the OSS community -- there are so many options, and there will always be someone out there to address the problem.

I know that i'll first need to get teh 32-bit v. of Totem.  What I'm not sure is whether I'll need to get the 32-bit options of the gstreamer0.10 codecs, or whether the 64-bit solutions will work.  From the mplayer tutorial it is just install the 32-bit mplayer and all its dependencies as 32-bit, and install w32 codecs (32-bit also).  What else should I look for while attempting to conquer this -- I'm supposing I'll need 32-bit v's of the dvd stuff - dvdread, dvdcss2.

Thanks for the help

---

### Post by Kilz on 2007-04-26
> **Anaximander Thales said:**
> I have searched several times, I've looked through the 32-bit mplayer tutorial, I've looked at 'how to get 32-bit programs to work on 64-bit archs (the sticky tutorial at the top of x86 64-bit user).'  I've not seen anything that really addresses 32-bit totem.  So, my attempt will be to either write a tutorial, or to add a post to one of the existing tutorials on how to get totem 32 working on amd64.

I understand that other feel the mplayer is the best, and other feel that vlc is the best, and some others will prefer to use xyz program.  I just prefer totem.  It's a minimalist design, it's quick and it has a simple interface.  Sure the other programs can be modified much more, but I just like the look of totem (in fact that's the only negative I have about it -- the options menu is severely lacking), and it does what I want how I want it.

This is the great thing about the OSS community -- there are so many options, and there will always be someone out there to address the problem.

I know that i'll first need to get teh 32-bit v. of Totem.  What I'm not sure is whether I'll need to get the 32-bit options of the gstreamer0.10 codecs, or whether the 64-bit solutions will work.  From the mplayer tutorial it is just install the 32-bit mplayer and all its dependencies as 32-bit, and install w32 codecs (32-bit also).  What else should I look for while attempting to conquer this -- I'm supposing I'll need 32-bit v's of the dvd stuff - dvdread, dvdcss2.

Thanks for the help

You are going to need all the 32bit dependencies and plugins/codecs. The reason mplayer is used is that the nogui package is used with few dependencies.

---

### Post by Anaximander Thales on 2007-04-27
That's what I figured -- thanks, Killz.

I suppose this would need to be a new tutorial since that would be a fair amount of difference.

Wish me luck.

---

