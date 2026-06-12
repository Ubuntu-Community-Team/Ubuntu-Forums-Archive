---
title: "Broke My Netflix on Ubuntu 13.04"
date: 2013-04-12
forum: Wine
---

### Post by ernestj on 2013-04-12
I was using Netflix on Ubuntu for the past several months. 

I do not know what I did, but all of a sudden it asked me if I wanted to update Wine.

I said yes and then it was all over. 

Now, I can get Netflix to open, however, when I play a move, all I get is sound and no video.

I tried to remove the install.
 
And then re-install it, using the instructions form this link:

[http://www.techrepublic.com/blog/opensource/how-to-get-netflix-streaming-on-ubuntu-1210/4019](http://www.techrepublic.com/blog/opensource/how-to-get-netflix-streaming-on-ubuntu-1210/4019)

But still not working,

Any ideas????

Thanks,

Ernie

---

### Post by kernelmanic on 2013-04-12
A Silverlight upgrade breaks all previous version of netflix player. 

At this point, I can not stream or play anything on netfix. Seems that there was an 'update' to silverlight that breaks all 
prior versions of netflix players. One _must_ upgrade silverlight 
in order to view netflix.  All it says on netflix is 


"you are almost ready to watch" blahblah  "first upgrade silverlight in order to enhance"  blah blah  "viewing quality" 

gee - it was working yesterday, and the quality was peachy. 


There is no way to say 'no thanks' - either upgrade or you can not view . 
I called netflix support, and there is no way to get around this.


I tried to 'install' the version of silverlight that netflix was pushing 
on me, but there are some problems, and also, it listed on mozilla's blocklist.
Maybe I have to upgrade more than once in netflix? i do not know. 
Hopefully the netflix/wine-browser folks will take a look at this.


cheers,


kernelmanic

---

### Post by jawilljr on 2013-04-13
I got the same message earlier...here is what I did to fix it:

```
rm -Rf ~/.wine-browser
```

Restart netflix-desktop.

That resets the netflix-desktop settings.

Jerry

---

### Post by kernelmanic on 2013-04-13
Yay.

I moved/renamed .wine-browser  in case I needed something from it, but this did the trick.
Thanks ! 
 
@jawilljr   - I use bodhi, so I am not on this forum often.  Am I supposed to click on something so that you get more karma or beans or stackflow or reputation or votes , etc etc ?

---

### Post by ernestj on 2013-04-13
I emailed the developer and he helped me. 
The fix above works.

---

### Post by cfmackey on 2013-04-14
> **jawilljr said:**
> I got the same message earlier...here is what I did to fix it:

```
rm -Rf ~/.wine-browser
```

Restart netflix-desktop.

That resets the netflix-desktop settings.

Jerry

This solution worked for me, even after I had pushed the Silverlight update. Should be a viable fix until Microsoft decides to throw another one our way.

---

### Post by baddison1 on 2013-05-01
> **jawilljr said:**
> I got the same message earlier...here is what I did to fix it:

```
rm -Rf ~/.wine-browser
```

Restart netflix-desktop.

That resets the netflix-desktop settings.

Jerry


Yup!! This worked for me also! Thank you very much.

---

### Post by SaoNigar on 2013-07-19
Excellent !
I did the job for me too,
Thank you very much

---

### Post by Lightning Dragon on 2013-07-20
Hi,

Just wanted to say this solved the problem for me. My problem, though, was a bit more extreme. It broke all my Wine and Ubuntu install. I couldn't open anything without it restarting Ubuntu to the log in page. Once I did the above, everything was back to normal.

Thanks for sharing!

---

### Post by doucette-4 on 2013-08-09
I'm having the same issue after upgrading to 13.04 (sound works fine but no video). I tried the solution posted above, but it doesn't seem to have worked. I've also tried completely purging netflix-desktop, removing the ppa, and re-installing everything again, but that didn't change anything either.

Is there anything that I can check or do? Many thanks!

---

### Post by fborup-e on 2013-08-13
> **jawilljr said:**
> I got the same message earlier...here is what I did to fix it:

```
rm -Rf ~/.wine-browser
```

Restart netflix-desktop.

That resets the netflix-desktop settings.

Jerry

This works fine -yihaa
Thanks

---

### Post by texaswriter on 2013-08-13
> **jawilljr said:**
> I got the same message earlier...here is what I did to fix it:

```
rm -Rf ~/.wine-browser
```

Restart netflix-desktop.

That resets the netflix-desktop settings.

Jerry

This has worked for me as well in the past. For a stretch of time, it was happening quite regularly that I needed to run that command. I haven't had to do that in many months.

I've watched 100s of hours now on Netflix streaming on Ubuntu... good stuff!!

---

### Post by steamer360 on 2013-08-17
I tried removing and reinstalling the app multiple times, and that didn't work. Even the command line code doesn't work. When I try to open the app, it says "performing local installation" and then exits after 2 seconds. Can somebody please help with this?!

---

### Post by cheetahz on 2013-08-18
Thanks woked great back up and running

---

### Post by smbjwright on 2013-08-19
I am doing a first install of the NetFlix desktop.  When I launch NetFlix I get "Compositing is not available, please enable compositing support and relaunch Netflix Desktop".  But the message leaves me with out a hint of how to enable "compositing".
Any ideas?  What program has "compositing" disabled and how is it enabled?

---

### Post by fabloub on 2013-09-22
As many people mentioned, the command rm -Rf ~/.wine-browser did not fix things for me. Here is what I did to make it work.
-I removed my old version of wine (1.4) and installed wine1.6 (you need to add a ppa; steps 1&2 on this page: [http://www.itworld.com/software/365919/install-wine-16-ubuntu-1304](http://www.itworld.com/software/365919/install-wine-16-ubuntu-1304))
-I had installed pipelight, so I got rid of that as well (sudo apt-get remove pipelight)
-I also got rid of a bunch of things from that installation that were not needed anymore (sudo apt-get autoremove)
-Next, I removed both .wine-browser and .netflix-desktop (rm -Rf ~/.wine-browser && rm -Rf ~/.netflix-desktop)
-Then I started the app again and it worked.

I know how frustrating this is. Good luck.

---

