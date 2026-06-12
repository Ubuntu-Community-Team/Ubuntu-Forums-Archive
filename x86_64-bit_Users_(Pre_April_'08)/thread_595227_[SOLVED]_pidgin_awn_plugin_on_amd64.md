---
title: "[SOLVED] pidgin awn plugin on amd64"
date: 2007-10-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Ehtetur on 2007-10-28
Anyone get the Pidgin AWN plugin working on Gutsy x64???

Pidgin doesn't see the pidgin_awn.so plugin on my x64 machine so I can't enable it.
It works fine on my x86 machine, I installed the plugin the same way on both:
copied pidgin_awn.so into ~/.purple/plugins.

---

### Post by pgvoorhees on 2007-10-29
yah, it needs a recompile for the AMD64 arch.

Try compiling with this source file. Make sure that your pidgin-dev package is installed. That should take care of your dependencies.

just unzip, in terminal type:
make <enter>
make install <enter>

Then go to the pidgin plugin page and enable the new AWN plugin.

---

### Post by Ehtetur on 2007-11-02
> **pgvoorhees said:**
> yah, it needs a recompile for the AMD64 arch.

yup, that did it!
At last, I can remove the pidgin icon from the system tray..
Thanks!!

---

### Post by terminal on 2007-11-03
Hey can you please upload the compiled .so file for amd64 ? I am not able to compile it properly . Thx

---

### Post by zeltak on 2007-11-04
yeah id also appreciate it !

thx

Zeltak

---

### Post by Ehtetur on 2007-11-04
> **terminal said:**
> Hey can you please upload the compiled .so file for amd64

Sure, here 'tis...
I replaced the *.so in pgvoorhees' file with the *.so compiled for x64_86.

---

### Post by kidguayas on 2007-11-05
How do I install it?
Thanks

---

### Post by revchris on 2007-11-05
Do I have to extract that to a specific place or just extract it anywhere then run make/make install?

---

### Post by Ehtetur on 2007-11-05
You need to extract pidgin.awn.so from the file and copy it into ~/.purple/plugins.
```
tar -zxvf pidgin_awn-rev20_x64_86.tar.gz
mkdir ~/.purple/plugins
cp pidgin_awn.so ~/.purple/plugins.
```

Restart pidgin and go to Tools --> Plugins.. You should see the AWN plugin listed.
Click it to enable it.

---

### Post by revchris on 2007-11-05
Thanks... :D

---

### Post by terminal on 2007-11-11
Thanks alot for this . Works like a charm .

---

### Post by mauricevh on 2007-11-23
Mmm for me it doesnt seem to work. I see the plugin in the Pidgin plugin list but when I enable it, nothing happens, not even after a restart. Any suggestions?

---

### Post by Ehtetur on 2007-11-23
You need to create a launcher for pidgin in AWN.
The plugin will change the pidgin icon in AWN to reflect your status (avail, away, etc) and you'll also see the number of unanswered messages you have.

---

### Post by Newcomer Johannes on 2007-12-20
First I would like to say thankyou :)


But the AWN Plugin works after restart not anymore.

I had done it exactly how Ehtetur had explain
> You need to extract pidgin.awn.so from the file and copy it into ~/.purple/plugins.
Restart pidgin and go to Tools --> Plugins.. You should see the AWN plugin listed.
Click it to enable it. 
Now I have restart and it works fine.
But after I restart again it doesn`t works anymore.:(

sorry for my bad English, I`m from Germany
But I hope you can understand my problem in spite of that.

---

### Post by Ehtetur on 2007-12-23
Newcomer Johannes - I too am from Germany. :grin:

Can you confirm that you extracted pidgin.awn.so from **pidgin_awn-rev20_x64_86.tar.gz** ?
Make sure that you created a launcher for pidgin in AWN.
Verify that you have the x64_86 kernel:
> uname -a

Since it sounds like you installed it properly, I think your problem is caused by one of the things above.

---

### Post by Newcomer Johannes on 2007-12-28
thank you Ehtetur

I had need a launcher for Pidgin 
now it works fine :)
the pidgin plugin is a really great feature

---

### Post by heinzbitte on 2008-01-06
I'm not very good at this whole thing.  I have pidgin installed and AWN working for the most part.  Can anyone give me step by step instructions to get this plugin working on my AMD 64 that an idiot like me could follow?

Thanks.

---

### Post by hcooh on 2008-04-18
I can't download it !

Is the link dead ?

---

### Post by moporoco on 2008-07-15
Great plugin, thanks!

---

