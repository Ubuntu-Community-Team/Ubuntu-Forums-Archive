---
title: "Lightning Calendar Plug-In for Thunderbird AMD64"
date: 2007-07-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by daniel_summers on 2007-07-21
I couldn't find a 64-bit version of this plug-in, so I decided to build it myself.  It works, so I'm sharing it with the community.  More details, and the plug-in, [can be found here]("http://www.djs-consulting.com/linux/blog/2007/lightning-calendar-plug-in-for-thunderbird-amd64") on my tech blog.  (If you get a 500, just refresh - my web host is behaving strangely this morning...)

Enjoy!

---

### Post by ashur@trogdor on 2007-07-23
Thanks Daniel!

I'll install this tonight.

- Dale

---

### Post by michael37 on 2007-07-25
Daniel,

Which build of 64-bit Thunderbird 2 did you use?   

Thanks.

---

### Post by daniel_summers on 2007-07-26
> **michael37 said:**
> Daniel,

Which build of 64-bit Thunderbird 2 did you use?

Well, that's an interesting question.  :)  The build process actually builds Thunderbird first, then builds the plug-in based on the Thunderbird it just built.  I downloaded the file "lightning-sunbird-0.5-source.tar.bz2" from the ["Other Systems" area]("http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.5/source/") off the Lightning box on the [calendar project]("http://www.mozilla.org/projects/calendar/") home page.  (It's 39 MB!)

I then ran "sudo apt-get build-deps mozilla-firefox" (I think that's what it was, anyway) and it downloaded a whole slew of stuff.  From that point, I followed the directions on the ["Build Lightning"]("http://www.mozilla.org/projects/calendar/lightning/build.html") link off the [Lightning home page]("http://www.mozilla.org/projects/calendar/lightning/").  I ran the configure script they gave in the CVS instructions ("./configure --enable-application=mail --enable-extensions=default,lightning") then ran make.  I didn't install Thunderbird, as I already had it - I just pointed it to the "/dist/xpi-stage" directory and installed the "lightning.xpi" file.

I hope the answer you were looking for is somewhere in that explanation.  :)  Did you try it, and did it work?

---

### Post by michael37 on 2007-07-26
> **daniel_summers said:**
> Well, that's an interesting question.  :)  The build process actually builds Thunderbird first, then builds the plug-in based on the Thunderbird it just built.  I downloaded the file "lightning-sunbird-0.5-source.tar.bz2" from the ["Other Systems" area]("http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.5/source/") off the Lightning box on the [calendar project]("http://www.mozilla.org/projects/calendar/") home page.  (It's 39 MB!)

I then ran "sudo apt-get build-deps mozilla-firefox" (I think that's what it was, anyway) and it downloaded a whole slew of stuff.  From that point, I followed the directions on the ["Build Lightning"]("http://www.mozilla.org/projects/calendar/lightning/build.html") link off the [Lightning home page]("http://www.mozilla.org/projects/calendar/lightning/").  I ran the configure script they gave in the CVS instructions ("./configure --enable-application=mail --enable-extensions=default,lightning") then ran make.  I didn't install Thunderbird, as I already had it - I just pointed it to the "/dist/xpi-stage" directory and installed the "lightning.xpi" file.

I hope the answer you were looking for is somewhere in that explanation.  :)  Did you try it, and did it work?

I had miserable experience building Thunderbird on Solaris.  I know people do it, but I just couldn't get it working.  So, I am a bit sceptical trying to build Tbird myself with or without Lightning, although I am sure it is easier on Linux than on Solaris.

I was hoping the 64-bit Tbird 2 was available in binaries, then I would just download your lightning xpi :)

---

### Post by daniel_summers on 2007-07-26
> **michael37 said:**
> I was hoping the 64-bit Tbird 2 was available in binaries, then I would just download your lightning xpi :)

I know the binaries exist.  I added the [Ubuntu Mozilla Team's preview archive]("https://wiki.ubuntu.com/MozillaTeam/PreviewArchives") to my sources for apt to upgrade Thunderbird for 2.0.  If you can install deb files, you could probably get it from them.  I'd also be happy to send the binary I built somewhere, if you'd like to test it - just let me know.

---

### Post by michael37 on 2007-07-27
> **daniel_summers said:**
> I know the binaries exist.  I added the [Ubuntu Mozilla Team's preview archive]("https://wiki.ubuntu.com/MozillaTeam/PreviewArchives") to my sources for apt to upgrade Thunderbird for 2.0.  If you can install deb files, you could probably get it from them.  I'd also be happy to send the binary I built somewhere, if you'd like to test it - just let me know.

Thanks for the link.  They don't have the latest 2.0.0.5 there.  

That's ok -- I think I will stick with 32-bit Tbird for now (it works, and the lightning binary from releases.mozilla.org also works) and *wimp* out until next Ubuntu release with Tbird 2 support.

---

### Post by daniel_summers on 2007-07-27
> **michael37 said:**
> Thanks for the link.  They don't have the latest 2.0.0.5 there.

I think the 2.0.0.5 is in the standard Ubuntu repositories.  The preview archives have 3, but it's called something else (Grand something-or-other).  I'm running 2.0.0.5 64-bit.  :)

---

### Post by michael37 on 2007-07-28
> **daniel_summers said:**
> I think the 2.0.0.5 is in the standard Ubuntu repositories.  The preview archives have 3, but it's called something else (Grand something-or-other).  I'm running 2.0.0.5 64-bit.  :)

Which version of Ubuntu are you running?

I am running Fiesty Fawn, and according to Synaptic, the only version in repos is 1.5.0.10.  Those are official repos.  

P.S.  I downloaded 32-bit Tbird 2.0 using ubuntuzilla.

---

### Post by daniel_summers on 2007-07-28
> **michael37 said:**
> Which version of Ubuntu are you running?

I am running Fiesty Fawn, and according to Synaptic, the only version in repos is 1.5.0.10.  Those are official repos.

That's the version I'm running.  I just pulled up Synaptic, and right-clicked on "firefox".  Under the "Versions" tab, there are two versions listed as available...

 - 2.0.0.5+1-0ubuntu1 (feisty-security)
 - 2.0.0.3+1-0ubuntu2 (feisty)

Do you have the security update repository enabled?

---

### Post by michael37 on 2007-08-01
> **daniel_summers said:**
> That's the version I'm running.  I just pulled up Synaptic, and right-clicked on "firefox".  Under the "Versions" tab, there are two versions listed as available...

 - 2.0.0.5+1-0ubuntu1 (feisty-security)
 - 2.0.0.3+1-0ubuntu2 (feisty)

Do you have the security update repository enabled?

I do.  My Firefox is version 2.0.0.5.

Thunderbird, however, lags behind.  Here is what I get for Thunderbird:

- 1.5.0.10-0ubuntu3 (fiesty)
- 1.5.0.12-0ubuntu0.7.04 (fiesty-security)

As far as I know, the unavailability of Tbird 2 in Fiesty is a known problem not expected to be fixed until Gutsy.

---

### Post by daniel_summers on 2007-08-01
> **michael37 said:**
> I do.  My Firefox is version 2.0.0.5.

Thunderbird, however, lags behind.  Here is what I get for Thunderbird:

- 1.5.0.10-0ubuntu3 (fiesty)
- 1.5.0.12-0ubuntu0.7.04 (fiesty-security)

As far as I know, the unavailability of Tbird 2 in Fiesty is a known problem not expected to be fixed until Gutsy.

Heh - you should have 2.0.0.6 now (well, you'll get it next time you update).  Yes, the Thunderbird in Feisty is going to be 1.5.  Adding those Mozilla Team preview archives is how I got the 2.0 series (currently 2.0.0.0, built 20070525).

---

### Post by michael37 on 2007-08-03
Repost from [thread]515828[/thread]

> **BoogieKnight said:**
> this site has 32 and 64 bit .deb packages for Thunderbird 2.0.0.5

[http://ubuntu.iuculano.it/dists/feisty/thunderbird/](http://ubuntu.iuculano.it/dists/feisty/thunderbird/)

i had to install the thunderbird-locales package first in order to install the application package but after that everything runs perfect. hope this helps.

Enjoy!

---

### Post by michael37 on 2007-08-06
> **daniel_summers said:**
> I couldn't find a 64-bit version of this plug-in, so I decided to build it myself.  It works, so I'm sharing it with the community.  More details, and the plug-in, [can be found here]("http://www.djs-consulting.com/linux/blog/2007/lightning-calendar-plug-in-for-thunderbird-amd64") on my tech blog.  (If you get a 500, just refresh - my web host is behaving strangely this morning...)

Enjoy!

I installed Thunderbird 64-bit from Luculano's depository and it works fine.  Then,  I downloaded your lightning plugin and it works quite well too!

Thank you!

P.S. When installing the plugin, double check that you are running 64-bit Tbird, not 32-bit or something like that.

---

### Post by daniel_summers on 2007-08-07
> **michael37 said:**
> I installed Thunderbird 64-bit from Luculano's depository and it works fine.  Then,  I downloaded your lightning plugin and it works quite well too!

Thank you!

Cool!  :)  I think I'm going to set a topic up on my blog that I'll attach future upgrades for the plug-in.  (I've got another product I host too - I think that's how I'm going to control it.  WordPress is pretty flexible.)

I'll post the link here when I get it finalized...

> **michael37 said:**
>  P.S. When installing the plugin, double check that you are running 64-bit Tbird, not 32-bit or something like that.

Ah - is that what caused the message I got in the e-mail to be different than the one I saw when I got here?  :)

---

### Post by daniel_summers on 2007-08-07
OK - here's the post that has the links...

[http://www.djs-consulting.com/linux/blog/2007/releases-for-lightning-and-xine](http://www.djs-consulting.com/linux/blog/2007/releases-for-lightning-and-xine)

---

### Post by michael37 on 2007-08-07
> **daniel_summers said:**
> Ah - is that what caused the message I got in the e-mail to be different than the one I saw when I got here?  :)

Yes :)

Thanks for posting.  Also, feel free to mention that the stock Linux plugin from the calendar website is 32-bit.  It does not work with 64-bit Thunderbird.

---

### Post by daniel_summers on 2007-08-07
Guess what I found out today?  Mozilla now has a 64-bit Lightning plug-in available from them.  I [detail it here]("http://www.djs-consulting.com/linux/blog/2007/mozilla-now-hosting-64-bit-lightning-plug-in").

---

### Post by PurposeOfReason on 2007-08-08
Thanks so much for this. It's things like this that are making my second 64bit attempt go much smoother. :)

---

### Post by michael37 on 2007-08-08
I am preparing updates to the wiki page 
[https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion)

My plan is to 
- add luculano's repository for Thunderbird 2.0
- create Lightning page

Comments welcome.

---

### Post by michael37 on 2007-08-08
Quick question to community:  What  is the easiest way to determine whether one is running 64-bit or 32-bit version of Thunderbird?  As opposed to Firefox, Thunderbird is not as forthcoming in Help/About.

---

### Post by michael37 on 2007-08-10
Lightning how to is now live at [https://help.ubuntu.com/community/ThunderbirdLightning](https://help.ubuntu.com/community/ThunderbirdLightning)

---

### Post by mrpurple on 2007-08-31
i'm running ubuntu feisty 64 and thunderbird (i think be 64), so i installed lighting following the procedure for 64.
at the end i see the calender only at the bottom left corner. if i click on it doesn't come the calender in the main windows. it is also impossible to create a new calender, the procedure is halting after i put the name of the new calender. Also if i go in the top menu calender and pointing at view => weekly (or whatever) the page doesn't display.

thank YOu for any help

---

### Post by michael37 on 2007-08-31
> **mrpurple said:**
> i'm running ubuntu feisty 64 and thunderbird (i think be 64), so i installed lighting following the procedure for 64.
at the end i see the calender only at the bottom left corner. if i click on it doesn't come the calender in the main windows. it is also impossible to create a new calender, the procedure is halting after i put the name of the new calender. Also if i go in the top menu calender and pointing at view => weekly (or whatever) the page doesn't display.

thank YOu for any help

Could you please run this mysterious command in the terminal:
```

ldd ~/.mozilla-thunderbird/*.default/extensions/*/components/lib*.so

```

If it doesn't produce any output, you preferences may be in .thunderbird, so then run
```

ldd ~/.thunderbird/*.default/extensions/*/components/lib*.so

```

---

### Post by michael37 on 2007-08-31
> **mrpurple said:**
> i'm running ubuntu feisty 64 and thunderbird (i think be 64), so i installed lighting following the procedure for 64.
at the end i see the calender only at the bottom left corner. if i click on it doesn't come the calender in the main windows. it is also impossible to create a new calender, the procedure is halting after i put the name of the new calender. Also if i go in the top menu calender and pointing at view => weekly (or whatever) the page doesn't display.

thank YOu for any help

How did you install Thunderbird?  On the second thought, it does sound like you have the wrong architecture of Lightning.  In that case, go to Tools/Addons, uninstall Lightning, restart Thunderbird, and install the 32-bit version.

---

### Post by mrpurple on 2007-08-31
the second of the two misteryous command produce this:
> 
mrpurple@mrpurple-lap:~$ ldd ~/.thunderbird/*.default/extensions/*/components/lib*.so
/home/mrpurple/.thunderbird/d4mydse7.default/extensions/{e2fda1a4-762b-4020-b5ad-a41df1933103}/components/libcalbasecomps.so:
        libpthread.so.0 => /lib/libpthread.so.0 (0x00002ab124813000)
        libxpcom.so => not found
        libxpcom_core.so => not found
        libplds4.so => /usr/lib/libplds4.so (0x00002ab124a2f000)
        libplc4.so => /usr/lib/libplc4.so (0x00002ab124c32000)
        libnspr4.so => /usr/lib/libnspr4.so (0x00002ab124e38000)
        libdl.so.2 => /lib/libdl.so.2 (0x00002ab125072000)
        libmozjs.so => not found
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00002ab125277000)
        libm.so.6 => /lib/libm.so.6 (0x00002ab12557b000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00002ab1257fd000)
        libc.so.6 => /lib/libc.so.6 (0x00002ab125a0c000)
        /lib64/ld-linux-x86-64.so.2 (0x0000555555554000)
/home/mrpurple/.thunderbird/d4mydse7.default/extensions/{e2fda1a4-762b-4020-b5ad-a41df1933103}/components/libstoragecomps.so:
        libpthread.so.0 => /lib/libpthread.so.0 (0x00002acb95d9d000)
        libxpcom.so => not found
        libxpcom_core.so => not found
        libplds4.so => /usr/lib/libplds4.so (0x00002acb95fb9000)
        libplc4.so => /usr/lib/libplc4.so (0x00002acb961bc000)
        libnspr4.so => /usr/lib/libnspr4.so (0x00002acb963c2000)
        libdl.so.2 => /lib/libdl.so.2 (0x00002acb965fc000)
        libmozjs.so => not found
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00002acb96801000)
        libm.so.6 => /lib/libm.so.6 (0x00002acb96b05000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00002acb96d87000)
        libc.so.6 => /lib/libc.so.6 (0x00002acb96f96000)
        /lib64/ld-linux-x86-64.so.2 (0x0000555555554000)
/home/mrpurple/.thunderbird/d4mydse7.default/extensions/{e2fda1a4-762b-4020-b5ad-a41df1933103}/components/libwebdav.so:
        libpthread.so.0 => /lib/libpthread.so.0 (0x00002b9142344000)
        libxpcom.so => not found
        libxpcom_core.so => not found
        libplds4.so => /usr/lib/libplds4.so (0x00002b9142560000)
        libplc4.so => /usr/lib/libplc4.so (0x00002b9142763000)
        libnspr4.so => /usr/lib/libnspr4.so (0x00002b9142969000)
        libdl.so.2 => /lib/libdl.so.2 (0x00002b9142ba3000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00002b9142da7000)
        libm.so.6 => /lib/libm.so.6 (0x00002b91430ac000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00002b914332e000)
        libc.so.6 => /lib/libc.so.6 (0x00002b914353c000)
        /lib64/ld-linux-x86-64.so.2 (0x0000555555554000)



thank's hor the help

---

### Post by michael37 on 2007-08-31
I am having stronger and stronger feeling that you ended up with 32-bit Thunderbird (it's neither bad nor good -- both 32-bit and 64-bit Thunderbirds are usable on 64-bit Ubuntu).  See my post above.

---

### Post by mrpurple on 2007-08-31
i installed thunderbird if i remember well from application add/remove ...
i  thought it was 64 (because my version is ubuntu feisty 64) if not how can i reinstall it ?

---

### Post by mrpurple on 2007-08-31
ok sorry  i find the solution ... i always installed the wrong pluging .... (i have alot in my computer for different version and platform)
so thank to all you for the help.
:guitar:

---

### Post by michael37 on 2007-08-31
> **mrpurple said:**
> i installed thunderbird if i remember well from application add/remove ...
i  thought it was 64 (because my version is ubuntu feisty 64) if not how can i reinstall it ?

The installation of Thunderbird is easy.  Follow **"Automated repository-based installation on Fiesty 7.04 (32-bit and 64-bit versions -- preferred method)"** from [this guide](https://help.ubuntu.com/community/ThunderbirdNewVersion).

The uninstallation depends on what kind of installation you performed.  Let's try to find what it was.

Do this:
```

which thunderbird
thunderbird -V
dpkg -l | grep -i thunderbird

file -b /usr/bin/thunderbird

```

It will say something symlink to ../lib/thunderbird/thunderbird or /opt/thunderbird/thunderbird.

Go to that directory (in the former case, cd /usr/bin/../lib/thunderbird, in the latter case, cd /opt/thunderbird), and run 

```

file -b thunderbird-bin
ldd thunderbird-bin

```

---

### Post by Kilz on 2007-09-24
The latest build of [Swiftdove]("http://swiftweasel.sourceforge.net/") has lightning installed by default.

---

