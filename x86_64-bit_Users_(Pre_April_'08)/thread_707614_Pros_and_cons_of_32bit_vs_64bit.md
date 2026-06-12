---
title: "Pros and cons of 32bit vs 64bit"
date: 2008-02-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by the lemming on 2008-02-25
My PC has an AMD 64bit 3400+ processor and utill now I have only played with 32bit operating systems.

Could somebody please give me the pros and cons of both sets of operating systems?

Would I even notice the difference on any of the applications that I run or when surfing the internet?

Cheers

---

### Post by Cappy on 2008-02-25
Look at the top sticky:
[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

This question is asked every couple of days.

You would not experience any speed up while browsing the internet. Only processor intensive tasks would be faster.

---

### Post by chrisccoulson on 2008-02-25
There is a lot of information in that thread.

But, to summarize (as Cappy said), you probably won't notice much difference with 64-bit if you're just browsing the web. Having said that, don't let that be a reason *not* to use 64-bit though. There are very few reasons not to use 64-bit now. I have used 64-bit for pretty much 2 years now (since Breezy), and I've seen the 64-bit version mature significantly over this time.

I haven't found any open-source applications that haven't been ported to 64-bit now. Most proprietary applications that don't run native 64-bit yet are really easy to install (for example, Google Earth, Adobe Reader and Skype are available through the Medibuntu repositories. Flash can be used with 64-bit Firefox using nspluginwrapper, which is set-up automatically if you install Flash through the repositories)

---

### Post by nfm on 2008-02-26
64-bit arch will use ~1.5x more memory. Programs are open to extra cpu registers which when used can yield performance increase over x86, you will need to refer to cpu's developer manual for more info. Speed-ups may be seen if a particular package was compiled to be compatible with a certain architecture, e.g. i386, and some optimizations were sacrificed in order to preserve the compatibility. Compiling code for a x86_64 arch enables all optimizations to be turned on, since x86_64 arch is very recent and features many popular instructions and extensions.

---

### Post by jespdj on 2008-02-26
> **nfm said:**
> 64-bit arch will use ~1.5x more memory.
This is not true in general; not all programs will use more memory than in the 32-bit version of Ubuntu.

---

### Post by flick on 2008-02-26
@ the lemming :

I'm a pretty typical "desktop user" -- web surfing, IM, music management, photo editing, spreadsheet for budgeting, word processing for my nonexistent fiction writing career. Been using the 64bit versions of Ubuntu since Edgy 6.10, my experience has been : no more hangups/issues than with 32bit, honestly very few hangups at all, where I've noticed performance boosts : photo rendering, and ripping CDs and DVDs, and compiling things from source ( been recently learning how to package .debs for my own use ).

No reason to not run 64bit OS if you have a 64bit processor.

---

### Post by Kilz on 2008-02-26
> **jespdj said:**
> This is not true in general; not all programs will use more memory than in the 32-bit version of Ubuntu.

Seeing how most 64bit computers have 1gb or ram or more, even if they use slightly more ram it really doesn't matter. Especially if more ram is being used to benefit performance.
I have rarely seen swap used even when both of my cores are being fully used. In fact if I ever reinstall (I probably will for Hardy) I'm thinking of eliminating it or making it real small.

---

### Post by rs3 on 2008-02-26
I have seen most of my performance gains in Compiz Fusion and music/movie ripping/encoding.  In the case of Compiz, the performance difference has been basically subjective (it "looks" smoother to me), but music and movie rips are almost twice as swift.

On the downside--and this is minor to me--my laptop exhibits a slightly shorter battery life in 64-bit than in 32-bit, but I understand this is due to the lack of dynticks support in Gutsy and earlier kernels (Hardy addresses this).

---

### Post by samwyse on 2008-02-27
I don't see a speed increase, I don't encode stuff often enough to notice, but it does use more memory. Flash is actually nicer, because it runs in a separate process (npviewer) which means if Firefox hangs due to the plugin you can just kill npviewer and continue browsing without killing Firefox.

---

### Post by rs3 on 2008-02-27
> **samwyse said:**
> Flash is actually nicer, because it runs in a separate process (npviewer) which means if Firefox hangs due to the plugin you can just kill npviewer and continue browsing without killing Firefox.

I understand that it is possible to disable individual flash animations with Gnash; handy, that, when you don't want to deal with problematic animations or, even better, advertisements.

(I have had to kill npviewer.bin many times, but not lately.)

---

### Post by Cappy on 2008-02-27
In Opera you can turn off Plugin support by default on pages. I only turn on plugin (flash!) support on domains I WANT like youtube.

Firefox's noscript lets you do the same thing.

---

