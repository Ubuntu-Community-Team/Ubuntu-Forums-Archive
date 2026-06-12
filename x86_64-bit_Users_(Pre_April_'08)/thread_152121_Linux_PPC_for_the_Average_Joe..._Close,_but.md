---
title: "Linux PPC for the Average Joe... Close, but"
date: 2006-03-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by Down8ve on 2006-03-29
Howdy Folks,


Please excuse my rant.  This is for the amateur, not those of you who love messing with computers!

I've been toying around with linux on various Mac notebooks and desktops for a while now, and have come to the conclusion that you can't do better than OS X on these machines.  My gripes:

No Flash.

Mutimedia is a royal pain.

Distros other than Ubuntu, especially YDL, are incredibly flawed for what is advertised.  Yellow Dog is pretty much useless these days... plain to see they make their money elsewhere.

Easy Wireless.

All these distros feel slow compared to OS X, even on my 7-year-old notebook.

Video editing.

Music notation (my interest)

Look, I love playing with Linux, and have tried Fedora 4, Yellow Dog, and Ubuntu (the best of them all) and realize they all have too many shortcomings for average Joes like me.  

Now that the Mac has gone Intel perhaps this will change, but for now, I'd stick with OS X on at least one partition.

Again, my apologies.  Ubuntu is SO close for the casual user, but now that Macs are Intel-based, what will happan to these PPC distros?

DSM

---

### Post by erniewinner on 2006-03-29
[-(  mmm... well as a person who faffs on all platforms. my experience is the opposite. mac os is too expensive. not well maintained. not even as well as windows. ie. windows 98se still gets security patches, thats an 8 year old os! mac os 10.2 no longer gets updated, so is no longer useful on the net, and thats a couple of years old. then apple drop support when the user base still demands the technology ie. beige g3 floppy not supported on mac os x or proper graphics support for that machine. obviously thats an old computer but it will still be usefull on ubuntu! there are a lot of issues with apple. i also own a performa 6210... (road apple!)
what are apple special for now they've given in to intel???:rolleyes:

---

### Post by dpny on 2006-03-29
I'm not sure what the point of your post is, but my $0.02:

Doesn't sound like your needs are Average Joe needs, especially with video editing and music notation. Non-linear editing, in particular, is highly specialized and usually involves fine-tuning your machine and several thousand dollars of ancillaries. I helped an ex-girlfriend get into video-editing, and it's not something you do for fun over a weekend.

My largely clueless brother typifies your average computer user. He spends 95% of his time doing one of four things: surfing the web, reading email, writing papers and managing his iPod. Based on my experience, after a whole two weeks of fooling with Ubuntu, is that once one is over the awkardness which comes with a new OS, it looks perfectly capable of doing these things.

---

### Post by ssam on 2006-03-29
yes its true about things like flash. i am not sure the companies will ever put the effort in to make powerpc binaries of programs (there a few who do, like opera). opensource flash players can do some flash, and opensource java is coming close to sun java (i think).

i manage happily with out flash, but i guess some people can't.

most multmedia codecs can be installed by following [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) . gstreamer and totem are much improved in dapper.

yellowdog don't seem to be that interested in the desktop. they have big customers like the US navy who get the most attention.

the original airport works very well in linux. the airport extreme driver is very new and has rough edges still. dapper will have network-manager, which will let you choose a wireless access point from a list in the gnome panel, and will ask for a WEP key when needed.

how much ram do you have? less that 256mb will make ubuntu quite a bit slower. more than 512 is good. using lighter window mangers also tends to speed things up. xfce is still quite friendly, or openbox is very fast, but very minimal. gnome got lots of performance love in the past few months, so dapper will feel quite a bit faster.

linux is nowhere close to mac os x in terms of desktop video editing applications. i beleive it is used quite a bit at the very high end of film making, but mostly with expensive comercial applcaitions like apple's shake, and maya. you could look at kino, diva, and pitivi. also i have heard that blender can be used for video editing.

i dont realy know about music authoring software.

i think ubuntu will keep making a powerpc version for quite a while. i expect people to want to give linux a go on their old powerpcs when apple stop supporting them.

linux is not quite ready for everyone yet, but i think its getting closer. please give dapper a try when it is released, it has many improvements.

---

### Post by stmiller on 2006-03-29
I'm a composer and can comment on the music notation part.

For music software, Rosegarden is pretty darn good. Record/mix audio tracks in with midi using soft synths, or your own midi hardware for playback. Has very good music notation. Uses soundfonts.
(And no- Lilypad is not a music notation 'program' like Finale/Sibelius. It is a music typesetting program (no GUI). No interface to plug in a score like Sibelius or Finale, you must use their own programming language to get a score.)

You can get respectable scores with Rosegarden. And for sound synthesis, programs like Pd and Csound are strong Linux programs, used in commercial music among other academic school programs with advanced computer music studios. Csound with Cecilia can help you make literally any kind of sound you want.

Ardour is a hard disc multitrack recording program, aka pro-tools. 

The bad part for Ubuntu: most music Linux apps need jackd to run, and there are current problems with jackd in Ubuntu PPC. See posts in this forum. Rosegarden works w/o jack, though fluidsynth and also other key programs (ardour) need jack.

Most audio programs take advantace of LADSPA plugins, which can be found. These let you manipulate audio inside the program (sort of like a VST plugin).

Other programs to check out: Brahms, MusE

---

### Post by erniewinner on 2006-03-29
:cool:  i'd love a simple multitrack tape recorder type interfaced linux app, like cakewalk guitar tracks... i like nero for putting video to dvd on pc... linux nero will need a while to grow.  
i tried rosegarden but i did i think i've have to try that again sometime, couldn't get it working.

---

### Post by ssam on 2006-03-30
i think [jokosher]("http://www.jokosher.org/") is the new kid on the block for recording and mixing. i expect there will be a stable version in dapper+1 in october.

---

### Post by Baggypants on 2006-03-30
Audacity will do simple multitrack audio recording, I've used it a fair bit and it works for me (probably because it is very basic :D )

---

### Post by erniewinner on 2006-03-30
:KS thanks. i had heard and messed with audacity for a bit. but i didn't know it could do multitrack! i've given it ago and i like it. how many tracks can you record? is it limited only by your hardware? also i've been using windows and a creative card. what are the limits on recording from multiple sources? i'd like to capture vocals on one channel and guitar on another... (at the same time.):cool:

---

### Post by anders_gud on 2006-04-02
[QUOTE=Down8ve]
Video editing.
[/QUOTE]

For now Blender is the only working video editor for PPC (Kino is broken w/t sound issues on ppc).

Try it out ubuntu .deb: 
[http://www.gudmundson.se/anders/uploads/blender_2.41-1ubuntu1.2_powerpc.deb](http://www.gudmundson.se/anders/uploads/blender_2.41-1ubuntu1.2_powerpc.deb)
Or Blender.org testing builds forum:
[http://www.blender3d.org/forum/viewforum.php?f=18&sid=cb634d0d1e0f0e815ffc9f3cd6a67aac](http://www.blender3d.org/forum/viewforum.php?f=18&sid=cb634d0d1e0f0e815ffc9f3cd6a67aac)

---

