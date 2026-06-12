---
title: "Ubuntu 11.10, Wine, and Audiogalaxy..."
date: 2011-10-14
forum: Wine
---

### Post by Kduke on 2011-10-14
Hey folks,

I upgraded to 11.10 today.  I haven't had many problems with it yet, however, I am unable to get the Audiogalaxy helper to work.

I am not sure if many people here use it.  It is a program to stream your home music collection to your phone, in my case Android.  Up until this point, I have yet to have any problems running the Audiogalaxy helper under wine until the ugprade today.

I'm curious if anyone else is having this problem.

---

### Post by christopher.wortman on 2011-10-15
[http://samiux.blogspot.com/2010/07/howto-streaming-music-from-ubuntu-1004.html](http://samiux.blogspot.com/2010/07/howto-streaming-music-from-ubuntu-1004.html)

time to do things the Linux way and break the Windows umbilical cord my friend.

---

### Post by Kduke on 2011-10-15
Thanks for the reply.  I actually started thinking the same thing.  That seems like a great guide.  I am currently using something called Subsonic (it has a native linux app).  It is working pretty great.

I will mark this thread as solved because that guide you linked offers an awesome solution.

---

### Post by Kheops_74 on 2011-10-17
May i hijack this post. I'm very interested by a solution for AudioGalaxy. I seem to have the same problem and i want it to work with my iPhone.

I install the program in Wine and when i run the .exe, i receive this message :


Call from 0x6844d479 to unimplemented function msvcp90.dll.?begin@?$basic_string@_WU?$char_traits@_W@std@@V?$allocator@_W@2@@std@@QAE?AV?$_String_iterator@_WU?$char_traits@_W@std@@V?$allocator@_W@2@@2@XZ, aborting
err:module:attach_process_dlls "tag.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\users\\sang\\Local Settings\\Application Data\\Audiogalaxy\\Audiogalaxy.exe" failed, status 80000100


Any idea? It worked great on 11.04 but not on 11.10.

Thanks

---

### Post by Kheops_74 on 2011-10-21
Anybody?

---

### Post by Kduke on 2011-10-22
Hello,

I am fairly certain that the problem is with Wine itself, not just the Audiogalaxy client in 11.10.  I think I read somewhere that Wine is not working yet.

I'm not too sure, because now that I am not dependant on Audiogalaxy, I do not have Wine installed.

---

### Post by Kheops_74 on 2011-10-22
I use Wine with AirVideo without problem. It's hard to solve. If you try it one day let me know.

---

### Post by Kheops_74 on 2011-10-22
I updated Wine to 1.3 using sudo add-apt-repository ppa:ubuntu-wine/ppa

The error message change:

wine: Call from 0x6832ddb2 to unimplemented function msvcp90.dll.??0?$basic_ostringstream@DU?$char_traits@D@std@@V?$allocator@D@2@@std@@QAE@H@Z, aborting
wine: Call from 0x6832ddb2 to unimplemented function msvcp90.dll.??0?$basic_ostringstream@_WU?$char_traits@_W@std@@V?$allocator@_W@2@@std@@QAE@H@Z, aborting
err:seh:raise_exception Unhandled exception code 80000100 flags 1 addr 0x6832ddb2

Any idea?

---

### Post by Kheops_74 on 2011-10-22
I found it. I run "winetricks vcrun2008" in a command line and reinstall AudioGalaxy.

---

### Post by LoREZ on 2012-05-20
I'm late to the party, but ...

[http://www.avidandrew.com/guides/67-audiogalaxy-linux](http://www.avidandrew.com/guides/67-audiogalaxy-linux)

---

