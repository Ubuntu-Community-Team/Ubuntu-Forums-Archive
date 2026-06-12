---
title: "I cant see my ubuntu desktop"
date: 2008-01-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by novik420 on 2008-01-19
Alright i downloaded ubuntu 7.10 for amd 64/intel users
burned the iso and etc...
popped it into my drive and booted up the comp everything go wells and when i hit run/install
the ubuntu name comes up along with the oj box but once that completes the screen goes black
but i can hear the sound of the desktop loading but my screen is blank
any help?

---

### Post by John.Michael.Kane on 2008-01-19
> **novik420 said:**
> Alright i downloaded ubuntu 7.10 for amd 64/intel users
burned the iso and etc...
popped it into my drive and booted up the comp everything go wells and when i hit run/install
the ubuntu name comes up along with the oj box but once that completes the screen goes black
but i can hear the sound of the desktop loading but my screen is blank
any help?

More info might be needed in order to assist you.

what is the machines spec's eg: video card,main board,monitor type?

You can try this. At the boot/install prompt (make sure to hit F6 first),and add the command below to the boot parameter.

```
nosplash noapic nolapic
```

note: do not remove any of the commands already shown in the boot line. just add the above commands to it.

---

### Post by novik420 on 2008-01-19
nvidia evega e-geforce 7300 gt graphics card
amd 64 athlon processor
hp v72 monitor
if this is any help
i am way newb to all of this and would really aprreciate help on geting ubuntu up and running

---

### Post by novik420 on 2008-01-20
can anyone explain to a newb how to fix this problem
i have seen the /etc/usplash.conf wa of solving this problem
but how do i go about doing that?
i am trying to install ubuntu 7.10 desktop for amd64/intel users
off of a live cd
when i run anything the ubuntu name comes up with the orange loading bar
and once that completes the screen goes black
any help???

---

### Post by asdrock358 on 2008-01-20
Hey, i have the same problem.  Any solutions out there, what was this splash thing...did it work for you.  good luck learning ubuntu.

best

Adam

---

### Post by novik420 on 2008-01-20
can anyone explain to me how to do the /etc etc...
or how to run commands from the live cd menu
ex: startx
i have tried two monitors with this
hp v72
and a gateway ev700
i have a evega nvidia ge-force 7300gt graphics card

---

### Post by John.Michael.Kane on 2008-01-21
> **novik420 said:**
> can anyone explain to me how to do the /etc etc...
or how to run commands from the live cd menu
ex: startx
i have tried two monitors with this
hp v72
and a gateway ev700
i have a evega nvidia ge-force 7300gt graphics card

Have you tried this method, which was posted above.
You can try this. At the boot/install prompt (make sure to hit F6 first),and add the command below to the boot parameter.

```
nosplash noapic nolapic
```

note: do not remove any of the commands already shown in the boot line. just add the above commands to it.

Also you are asking questions, and not posting any methods you are trying. The live cd is known to give users problems on certain hardware, in your case you may want to try the alternate install cd.

---

### Post by novik420 on 2008-01-21
> **John.Michael.Kane said:**
> Have you tried this method, which was posted above.
You can try this. At the boot/install prompt (make sure to hit F6 first),and add the command below to the boot parameter.

```
nosplash noapic nolapic
```

note: do not remove any of the commands already shown in the boot line. just add the above commands to it.

Also you are asking questions, and not posting any methods you are trying. The live cd is known to give users problems on certain hardware, in your case you may want to try the alternate install cd.

i have tried the nosplash method
i have tried ubuntu 7.10 amd64 and the 7.10 standard users download live cds
i have also attempted 6.10 still had this same problem
i have swithched out monitors
and i have tried a few boot methods
none have succeeded i have come to believe that the problem is with my grafix card

---

### Post by John.Michael.Kane on 2008-01-21
> **novik420 said:**
> i have tried the nosplash method
i have tried ubuntu 7.10 amd64 and the 7.10 standard users download live cds
i have also attempted 6.10 still had this same problem
i have swithched out monitors
and i have tried a few boot methods
none have succeeded i have come to believe that the problem is with my grafix card

As i said the live cd has been known to give users issues on certain hardware combinations. Have you tried the alternate iso linked here [URL="http://releases.ubuntu.com/7.10/ubuntu-7.10-alternate-amd64.iso"]
Gutsy Gibbon 7.10 Alternate install CD[/URL]

---

### Post by novik420 on 2008-01-21
> **John.Michael.Kane said:**
> As i said the live cd has been known to give users issues on certain hardware combinations. Have you tried the alternate iso linked here [URL="http://releases.ubuntu.com/7.10/ubuntu-7.10-alternate-amd64.iso"]
Gutsy Gibbon 7.10 Alternate install CD[/URL]

thank you so much man that one worked
i appreciate all of the help

---

