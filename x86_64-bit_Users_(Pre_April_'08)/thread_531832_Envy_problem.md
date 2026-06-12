---
title: "Envy problem"
date: 2007-08-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by masoodkamal on 2007-08-22
hi tseliot

man u made a good tool (if i get it working ) :)  .
it showing dependency problem !
u didnt mention it anywhere that we have to install any modules to make it working.

Plz help i am new to linux and now frustrated :(

---

### Post by tjotser on 2007-08-22
try PM'ing or visit his blog, i doubt he will find (or look for) your post in the x64 section...

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Could you be a bit more specific about what dependencies give you troubles, and post output.
You will be surprised what people know about certain stuff around here... (not me btw) :KS

---

### Post by dabl on 2007-08-22
Yep, it needs the "fakeroot" package and some python packages that you might not already have installed.  Just make a note of what Envy asks for when you try to install it -- they are all in the repos.  Once you have the other packages installed, Envy will be happy to be installed.  :popcorn:

---

### Post by masoodkamal on 2007-08-22
hi 

i got the error msg

Error: Dependecy is not satisfiable:build essential

now i know tht i need some package called build-essential but whr shuld i get one. and how
i mean which commands r used.
For e.g. 
  in a post here for installing nvidia drivers (which also i can not install :() a person mentioned "less " command but dont mentioned how to close it , it took 15 min to find how to close the file when opened with less command.

So plz help. i want to install nvidia drivers.

---

### Post by masoodkamal on 2007-08-24
Man !!

i am really looking forward for some help. i tried every thing ppl tell here to install nvidia drivers.
i think i dont have build-essential package. do no body have them on fresh install ? or only i dont have it !
And how i can get it.

Plz help :(

---

### Post by Jup on 2007-08-24
Hey,

If im correct you can install build-essential by opening a terminal and typing

**sudo apt-get install build-essential**

Should this not work it's also possible to install it through synaptic.

---

### Post by crjackson on 2007-08-24
> **masoodkamal said:**
> Man !!

i am really looking forward for some help. i tried every thing ppl tell here to install nvidia drivers.
i think i dont have build-essential package. do no body have them on fresh install ? or only i dont have it !
And how i can get it.

Plz help :(

**system>administration>synaptic package mannager>search>build-essential>mark install>apply**

---

### Post by tseliot on 2007-08-24
Make sure you have all the repositories enabled (also universe and multiverse) in your /etc/apt/sources.list on Ubuntu

If you do not know how to enable those repositories, please take a look at this page:
[enabling_extra_repositories]("http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories")

---

### Post by ramkumail on 2007-08-29
hi envy got installed after installing build essentials from command line by entering "sudo apt-get install build-essential"
. I got envy from [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
 Opened this package from gdebi package manager. firefox automatically did this.

---

