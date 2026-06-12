---
title: "Taking advantage of multi-core systems"
date: 2009-05-14
forum: x86 64-bit Users
---

### Post by quantumstitch on 2009-05-14
I have noticed when running ogmrip that these instances use only one core. Is it possible to distribute this type of work across all cores (4 in my machine), to speed up the process? Or perhaps, someone could suggest an alternative to ogmrip that handles subtitles. thanks.

---

### Post by HavocXphere on 2009-05-14
> **quantumstitch said:**
> Is it possible to distribute this type of work across all cores (4 in my machine)
Not really, the code needs to be designed in a specific way to make this possible. i.e. the programmer must
implement multi-threading in his app.

---

### Post by s3a on 2009-05-14
File a wishlist bug for multi-core support.

---

### Post by Slim Odds on 2009-05-14
> **HavocXphere said:**
> Not really, the code needs to be designed in a specific way to make this possible. i.e. the programmer must
implement multi-threading in his app.

People confuse this all the time.

To use multiple cores, an application must be multi-process and not just multi-threaded.

Processes are distributed across processors (cores). Threads run on the same core as the process that started them.

---

### Post by Arup on 2009-05-14
Interestingly most of the Linux programs, especially those in x64 repos handle multi cores quite well, programs like WinFF have options to enable multi cores, so does sound converter, Handbrake and others.

---

### Post by Joeb454 on 2009-05-14
> **Arup said:**
> Interestingly most of the Linux programs, especially those in x64 repos handle multi cores quite well, programs like WinFF have options to enable multi cores, so does sound converter, Handbrake and others.

Where is the option to enable multi-core use in handbrake? Or does it just do it automatically? I've never seen the option :(

---

### Post by Arup on 2009-05-15
> **Joeb454 said:**
> Where is the option to enable multi-core use in handbrake? Or does it just do it automatically? I've never seen the option :(

In Handbrake its automatic, in WinFF there is a tab under edit>preferences

---

### Post by HavocXphere on 2009-05-16
> **Slim Odds said:**
> People confuse this all the time.

To use multiple cores, an application must be multi-process and not just multi-threaded.

Processes are distributed across processors (cores). Threads run on the same core as the process that started them.
Actually, I think its you who is confused. Allow me to quote from wikipedia:
> On a multiprocessor or multi-core system, the threads or tasks will generally run at the same time, with **each processor or core running a particular thread** or task.
> A system with n cores is effective when it is presented with n or more threads concurrently. 
> Multithreading computers have hardware support to efficiently execute multiple threads. **These are distinguished from multiprocessing systems (such as multi-core systems)** in that the threads have to share the resources of single core: the computing units, the CPU caches and the translation lookaside buffer (TLB).
So assuming that one has a reasonably modern system (Core2duo and up), the threads don't have to be on the same core.

And from Intel itself
> The rise in the number of dual core processors in desktop and mobile computers over the last year should give software developers a compelling reason to **multi-thread their applications**.
[http://www3.intel.com/cd/ids/developer/asmo-na/eng/331847.htm](http://www3.intel.com/cd/ids/developer/asmo-na/eng/331847.htm)

---

### Post by cfrein on 2009-06-16
Just edit the ogmrip-profile you are using and change the number of threads on the video tab.

---

### Post by ghostborg on 2009-10-16
I am using ogmrip 0.13.2 and I do not see a thread option under the Video tab. Did they remove it. This is really sloooowww.:confused:

Update: The Thread number must be auto. While running an encode I noticed mencoder had a Thread value of 4. 

Still does not utilize 4 cores like Handbrake does.

---

### Post by bosbeemer on 2009-10-19
> **Slim Odds said:**
> People confuse this all the time.

To use multiple cores, an application must be multi-process and not just multi-threaded.

Processes are distributed across processors (cores). Threads run on the same core as the process that started them.


---------------------
That's not true ... 
Each thread can be configured to run on a separate core. I have personally written applications where threads in the same process are configured to take advantage of multiple cores. Look at the man pages for following functions in Linux.

[B][B]pthread_setaffinity_np
[/B][/B]**[B][B][B]pthread_getaffinity_np**[/B][/B][/B]

****

---

