---
title: "ubuntu 16.0 64bit + wine + OneNote path lim-t : Can I overcame 260 char-s path lim-n?"
date: 2017-07-31
forum: Wine
---

### Post by aleximioustostas on 2017-07-31
Hi guys. I had some experiments with my work environment and decided install ubuntu + wine + office apps. One of the main reason why I chose ubuntu was 'path limitations', compared to windows I can create 2000+ characters 'tree of folders' when in windows10 I have ~260 characters limit. Btw I tried enable long-path feature (available in windows10, from ~1.600 build, inside win10) but had failure. 

Problem: I can work with **OneNote**, but **can't** use ubuntu file-system advantages and create folders that **more then 260 characters** in sum length. If I create folders and '.onenote' files manually OneNote just don't see folders that deeper than 260 characters in sum length on file names. It I tried create same 'system' through OneNote interface I got 'you can't create .... more than 260 char...'
 I made some research about my needs and I need about 1000+ length (different statistic documents and such things, to keep it organized).

Can I off this restriction somehow? I knew it can increase amount of resources, but it's ok for me.
    Can I remove part of code in installed OneNote which responsible for it? (Haven't this lvl experience, but ready to try:p)
    Does Vain have such additions?
    


Why can't you use another NoteTaking app?
Because I already have about 50GB OneNote stuff, and can't migrate it with same quality and without pain :( 


Sorry if any eyes-shining (english grammar:p) thing exists in my message.

---

### Post by vocx on 2017-07-31
> **aleximioustostas said:**
> Hi guys. I had some experiments with my work environment and decided install ubuntu + wine + office apps. One of the main reason why I chose ubuntu was 'path limitations', compared to windows I can create 2000+ characters 'tree of folders' when in windows10 I have ~260 characters limit. Btw I tried enable long-path feature (available in windows10, from ~1.600 build, inside win10) but had failure. 

Problem: I can work with **OneNote**, but **can't** use ubuntu file-system advantages and create folders that **more then 260 characters** in sum length. If I create folders and '.onenote' files manually OneNote just don't see folders that deeper than 260 characters in sum length on file names. It I tried create same 'system' through OneNote interface I got 'you can't create .... more than 260 char...'
 I made some research about my needs and I need about 1000+ length (different statistic documents and such things, to keep it organized).

**Can I off this restriction somehow?** I knew it can increase amount of resources, but it's ok for me.
    **Can I remove part of code in installed OneNote which responsible for it? **(Haven't this lvl experience, but ready to try:p)
    Does Vain have such additions?
    
Maybe Wine is emulating the same directory limitations as Windows, which is why you see the same behavior. Or maybe the OneNote program has this limitation hardwired in its code. How can you modify OneNote? Since it's not open source, you cannot just modify integral parts of it easily.

> 
Why can't you use another NoteTaking app?
Because I already have about 50GB OneNote stuff, and can't migrate it with same quality and without pain :( 

Sorry if any eyes-shining (english grammar:p) thing exists in my message.
I honestly don't know what OneNote does, but if you have 50 GB of "notes", that's really strange. And the fact that you feel the need of having 1000 character long directories tells me that probably you need to think hard on the way you store information. Improving the way you store thing will be helpful now, before you need to store another 50 GB of stuff.

I presume you use some sort of hierarchical way of storing, so you should probably move some directories to an upper level, and thus save a directory level.
```

/dir_one/
    parameter_1/
        sub_parameter_1/
        sub_parameter_2/
        sub_parameter_3/
    parameter_2/
        sub_parameter_3/

```

```

/parameter_1/
    sub_parameter_1/
    sub_parameter_2/
    sub_parameter_3/
/parameter_2/
    sub_parameter_3/

```

---

### Post by deadflowr on 2017-07-31
*Thread moved to **Wine**.*

---

### Post by aleximioustostas on 2017-07-31
> **vocx said:**
> 
I presume you use some sort of hierarchical way of storing, so you should probably move some directories to an upper level, and thus save a directory level.
```

/dir_one/
    parameter_1/
        sub_parameter_1/
        sub_parameter_2/
        sub_parameter_3/
    parameter_2/
        sub_parameter_3/

```

```

/parameter_1/
    sub_parameter_1/
    sub_parameter_2/
    sub_parameter_3/
/parameter_2/
    sub_parameter_3/

```

Thanks for answering! :)


It's fun but I already use something like 

```

/1/
   TOC.onenote
   1/
   2/
   3/
     TOC.onenote/
     1/
     2/
     3/ 
     1/
       TOC.onenote/
       ...

```
And so on.

> [COLOR=#000000]I honestly don't know what OneNote does, but if you have 50 GB of "notes", that's really strange. And the fact that you feel the need of having 1000 character long directories tells me that probably you need to think hard on the way you store information. Improving the way you store thing will be helpful now, before you need to store another 50 GB of stuff.[/COLOR]


Yes, I think if I will not figure something about "win10 long paths" or "wine long paths" options, I will work on OneNote parser and something with open code. But it's can take few-6 months =(

---

