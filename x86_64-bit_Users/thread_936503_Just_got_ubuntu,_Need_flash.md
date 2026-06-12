---
title: "Just got ubuntu, Need flash"
date: 2008-10-02
forum: x86 64-bit Users
---

### Post by Vertoxic on 2008-10-02
someone plz help me get flash to work on my laptop i just got ubuntu 64 bit on my lappy intel 2.0 4 gig ram ATI 2600hd
thx in advance

all fresh just got it, if there is anthing else i need to do plz let me know!

---

### Post by RealG187 on 2008-10-02
type this command

```
sudo apt-get install ubuntu-restricted-extras
```
Gives you flash, java (I think), and extra codecs (MP3, WMA, DivX)

---

### Post by Vertoxic on 2008-10-02
ok i just tried that but no luck :(

---

### Post by lonniehenry on 2008-10-02
See the sticky above on the first page of this x86 64 bit users section.

---

### Post by Vertoxic on 2008-10-02
> **lonniehenry said:**
> See the sticky above on the first page of this x86 64 bit users section.
i just did it did not do any good....
  
 do i need to enable some kind of syntatic package or something or what should i just go back and install 32 bit wich is much easier?

---

### Post by Vertoxic on 2008-10-02
someone plz help me thank you!

---

### Post by Yellow Pasque on 2008-10-02
> **Vertoxic said:**
> someone plz help me thank you!
Hyper-posting and making threads about installing Vista over Ubuntu less than an hour after you installed Ubuntu kind of makes you look like a troll (or a Ritalin kid). I'm not sure which one is worse.

---

### Post by jespdj on 2008-10-03
Just install it like this:
```
sudo apt-get install flashplugin-nonfree
```
Note, that's exactly the same as on 32-bit. It's not easier or harder to install Flash on 64-bit as it is on 32-bit (if you're running Ubuntu 7.10 or newer).

---

### Post by Sef on 2008-10-03
Applications > Add/Remove > SHOW: change to 'All Available Applications' > SEARCH:  macromedia > click on the box next to Macromedia flash plug in > click apply changes > apply > close.

---

### Post by Kilz on 2008-10-03
> **Vertoxic said:**
> Hi guys i just got Ubuntu 6 bit4 installed on my new laptop m-6864 Gateway intel 2.0 4 gig ram ATI 2600HD 
need to install flash wich dont work... cant watch youtube :(
i kinda new to this so plz help me thx!
i tried 

sudo ./GetFlash

toliy@toliy-laptop:~$ sudo ./GetFlash
sudo: ./GetFlash: command not found

dont know what it is do i need to get some admin option or something i just installed this like 5 min ago thx guys!!!!

The command here is to run the automated install script.

> **Vertoxic said:**
> yes i got the newest version from their website just a few min ago :) 
64 bit

Indicating he is running Hardy Heron 8.04.

But if we take a look at [the Flash Sticky]("http://ubuntuforums.org/showthread.php?t=772490") we see THERE IS NO SCRIPT FOR HARDY. In fact in the Hardy section
**[COLOR="Red"]DO Not[/COLOR]** install the scripts below. Run all the commands above again. The script will only make things worse. 

Then we see the **[SIZE="4"][COLOR="Red"]Big Bold Red[/COLOR][/SIZE]** letters suggesting exactly what to do to get help
**[SIZE="4"][COLOR="Red"]How to get help (Please Read Before Making a Post)[/COLOR][/SIZE]**
below that is 
When you make a post, make in in this thread.
Incude some info
Report the bug on launchpad
Then the kicker.
**[COLOR="Red"]Hardy users should not install the automated script or try other methods.[/COLOR]**

Riggght its a flash problem....

I will say no more. Im sure if I do I will get a warning for something. 	:-#

---

### Post by saru411 on 2008-10-04
> **kilz said:**
> the command here is to run the automated install script.



Indicating he is running hardy heron 8.04.

But if we take a look at [the flash sticky]("http://ubuntuforums.org/showthread.php?t=772490") we see there is no script for hardy. In fact in the hardy section
**[color="red"]do not[/color]** install the scripts below. Run all the commands above again. The script will only make things worse. 

Then we see the **[size="4"][color="red"]big bold red[/color][/size]** letters suggesting exactly what to do to get help
**[size="4"][color="red"]how to get help (please read before making a post)[/color][/size]**
below that is 
when you make a post, make in in this thread.
Incude some info
report the bug on launchpad
then the kicker.
**[color="red"]hardy users should not install the automated script or try other methods.[/color]**

riggght its a flash problem....

I will say no more. Im sure if i do i will get a warning for something. 	:-#
[size="7"]my hero[/size]

---

### Post by saru411 on 2008-10-04
"double post"

---

