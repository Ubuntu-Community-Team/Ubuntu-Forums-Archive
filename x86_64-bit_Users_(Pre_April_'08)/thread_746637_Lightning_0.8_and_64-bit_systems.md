---
title: "Lightning 0.8 and 64-bit systems"
date: 2008-04-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Rohaq on 2008-04-05
So it looks like a new version of the Thunderbird Lightning plugin has reared its head, and again I can't see a 64 bit compatible version released. I've tried editing the install.rdf file in the XPI, but I end up with some weird effects when the plugin's loaded.

Has anyone been able to compile Lightning 0.8 properly for a 64-bit system? If so, can they provide a copy for the rest of us? :)

---

### Post by Kilz on 2008-04-05
> **Rohaq said:**
> So it looks like a new version of the Thunderbird Lightning plugin has reared its head, and again I can't see a 64 bit compatible version released. I've tried editing the install.rdf file in the XPI, but I end up with some weird effects when the plugin's loaded.

Has anyone been able to compile Lightning 0.8 properly for a 64-bit system? If so, can they provide a copy for the rest of us? :)

While it may not help, the latest [Swiftdove ]("http://swiftweasel.tuxfamily.org/")has the 64bit lightning .8 installed by default.

---

### Post by zeltak on 2008-04-06
Hi

i would also love a 64bit version of lightning so i tried to install the latest swiftdove on my hardy beta machine and this is what i got:

zeltak@voices:~$ swiftdove
the settings directory exists
/usr/local/swiftdove/swiftdove: 76: gawk: not found
mv: cannot remove `/prefs.js': Permission denied
tee: /prefs.js: Permission denied


does anyone know whats wrong?

thx

Zeltak

---

### Post by Cappy on 2008-04-06
```
sudo apt-get install gawk
```

found out the packagename from typing "gawk" on the command line and hitting enter

you may also need to run the program with sudo

The beginner talk section would be better place for this.

---

### Post by zeltak on 2008-04-06
hi

ok that worked...but is there anyway not to run it as root?

thx

zeltak

---

### Post by Marabu on 2008-04-08
Hi all,

I have made a lightning-build for a 64-bit Linux (Compiled on Kubuntu, x86_64 GNU/Linux) for anybody who is interested:
[lightning-0.8-linux-x86_64.xpi]("http://cheetah.ehosting.ch/lightning-0.8-linux-x86_64.xpi")

Cheers

---

### Post by bobradu on 2008-04-08
Lifesaver, thanks.  Especially since my Google Provider went bottoms up without 0.8.

---

### Post by Marabu on 2008-04-08
Glad I could help, it was the same for me too this morning. Can't live without my Google Provider! :)

---

### Post by Rohaq on 2008-04-08
Awesome Marabu, thanks!

---

### Post by cybergalvez on 2008-04-09
> **Marabu said:**
> Hi all,

I have made a lightning-build for a 64-bit Linux (Compiled on Kubuntu, x86_64 GNU/Linux) for anybody who is interested:
[lightning-0.8-linux-x86_64.xpi]("http://cheetah.ehosting.ch/lightning-0.8-linux-x86_64.xpi")

Cheers

Thanks you are a life saver

---

### Post by zeltak on 2008-04-09
thx alot

no more tinkiring with getting swiftdove to work!


Zeltak

---

### Post by queno on 2008-04-09
Marabu, you're a god! Thank you so much for this. I've been looking for a fix for lightning 0.8 on 64 Bit for the last couple of days! Compiling the lightning source did not work out for me...

---

### Post by Marabu on 2008-04-09
> **queno said:**
> Marabu, you're a god! Thank you so much for this. I've been looking for a fix for lightning 0.8 on 64 Bit for the last couple of days! Compiling the lightning source did not work out for me...
That's strange, I didn't have to fix anything. The thing with Lightning (and Sunbird) is that unlike other extensions, it includes binaries which obviously are architecture dependent. So what i did is I downloaded the source from [ftp://ftp.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.8/source](ftp://ftp.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.8/source), compiled it and found my .xpi in /dist/xpi-stage/lightning.

---

### Post by stickk on 2008-04-09
> **zeltak said:**
> thx alot

no more tinkiring with getting swiftdove to work!


Zeltak

Please explain in exactly what "tinkering" you had to do.

---

### Post by jpeach on 2008-04-09
thanks

---

### Post by teknorah on 2008-04-09
> **Marabu said:**
> Hi all,

I have made a lightning-build for a 64-bit Linux (Compiled on Kubuntu, x86_64 GNU/Linux) for anybody who is interested:
[lightning-0.8-linux-x86_64.xpi]("http://cheetah.ehosting.ch/lightning-0.8-linux-x86_64.xpi")

Cheers


Awesome, possum!  Thx... by any chance do you have a guide for building thunderbird/firefox add-ons from source (primarily an issue for my 64-bit version of Ubuntu)?

---

### Post by zeltak on 2008-04-10
Hi stickk


what i meant (as you can see in the begining of the post) is that i couldnt get swiftdove to run unless i was running it as root

thx

Zeltak

---

### Post by Marabu on 2008-04-10
> **norahaura said:**
>  by any chance do you have a guide for building thunderbird/firefox add-ons from source (primarily an issue for my 64-bit version of Ubuntu)?

Usually I don't compile firefox extensions. Many extensions don't need to be compiled anyway. Otherwise just download the source, configure and compile it. :) Or what exactly is not clear about compiling a source?
Well okay, sometimes you have to install some additional dev-packages...

Marabu

---

### Post by Kilz on 2008-04-10
> **zeltak said:**
> Hi stickk


what i meant (as you can see in the begining of the post) is that i couldnt get swiftdove to run unless i was running it as root

thx

Zeltak

That sounds like the files somehow got owned by root, a simple chown command would have solved it.

---

### Post by jbroome on 2008-04-10
> **Marabu said:**
> Hi all,

I have made a lightning-build for a 64-bit Linux (Compiled on Kubuntu, x86_64 GNU/Linux) for anybody who is interested:
[lightning-0.8-linux-x86_64.xpi]("http://cheetah.ehosting.ch/lightning-0.8-linux-x86_64.xpi")

Cheers

Thanks a bunch, was looking for this.  A+++  would install again. :)

---

### Post by zeltak on 2008-04-11
Hi

this is the last part of what i get from the terminal when i run in as my user (not root)

user_pref("ttb.cat0.tags", "");
user_pref("ttb.cats", "cat0");
user_pref("ttb.cats.delimiter", "%");
user_pref("ttb.cats.migrated", true);
user_pref("unread.firstRun", false);
user_pref("wallet.caveat", true);
Cannot find mozilla runtime directory. Exiting.

With root it runs fine

i am runing it on hardy if i havnt mentioned it before

Zeltak

---

### Post by Kilz on 2008-04-11
> **zeltak said:**
> Hi

this is the last part of what i get from the terminal when i run in as my user (not root)

user_pref("ttb.cat0.tags", "");
user_pref("ttb.cats", "cat0");
user_pref("ttb.cats.delimiter", "%");
user_pref("ttb.cats.migrated", true);
user_pref("unread.firstRun", false);
user_pref("wallet.caveat", true);
Cannot find mozilla runtime directory. Exiting.

With root it runs fine

i am runing it on hardy if i havnt mentioned it before

Zeltak

Since there isnt a Hardy version that may be an issue. But the following command should help. Edit it to replace YourUsername with your login.
```
sudo chown -R YourUsername:users /usr/local/swiftdove
```

---

### Post by roobz on 2008-04-11
Thank you so much, Marabu. You're great!

I just wonder how I can compile this extension for myself. Maybe one day.....

---

### Post by zeltak on 2008-04-12
hi Kilz's and thx for the reply

unfortunately the permission change does not work.

anything else i should try?


zeltak

---

### Post by Kilz on 2008-04-12
> **zeltak said:**
> hi Kilz's and thx for the reply

unfortunately the permission change does not work.

anything else i should try?


zeltak

Can you tell me what the results of 
```
ls -al ~/.swiftdove 
```is ?

---

### Post by zeltak on 2008-04-12
here are the results

total 64
drwxr-xr-x   3 zeltak zeltak  4096 2008-04-06 08:33 .
drwxr-xr-x 159 zeltak zeltak 12288 2008-04-12 18:18 ..
-rw-r--r--   1 zeltak zeltak 30102 2008-04-12 07:33 20012.js
drwxr-xr-x  12 zeltak zeltak  4096 2008-04-12 07:33 5muqtm8d.default
-rw-r--r--   1 zeltak zeltak   335 2008-04-06 08:29 appreg
-rw-r--r--   1 zeltak zeltak   145 2008-04-06 08:29 .directory
-rw-r--r--   1 zeltak zeltak    94 2008-04-06 08:29 profiles.ini


thx for helping!

Zeltak

---

### Post by Kilz on 2008-04-12
> **zeltak said:**
> here are the results

total 64
drwxr-xr-x   3 zeltak zeltak  4096 2008-04-06 08:33 .
drwxr-xr-x 159 zeltak zeltak 12288 2008-04-12 18:18 ..
-rw-r--r--   1 zeltak zeltak 30102 2008-04-12 07:33 20012.js
drwxr-xr-x  12 zeltak zeltak  4096 2008-04-12 07:33 5muqtm8d.default
-rw-r--r--   1 zeltak zeltak   335 2008-04-06 08:29 appreg
-rw-r--r--   1 zeltak zeltak   145 2008-04-06 08:29 .directory
-rw-r--r--   1 zeltak zeltak    94 2008-04-06 08:29 profiles.ini


thx for helping!

Zeltak

I did a little modifying of the swiftdove start script, I'm attaching it, untar it and place it in /usr/local/swiftdove.

---

### Post by zeltak on 2008-04-12
thx again

i copied the script and now i get this

the settings directory exists1
settings file check passed


any ideas?

thx

Zeltak

---

### Post by Kilz on 2008-04-12
> **zeltak said:**
> thx again

i copied the script and now i get this

the settings directory exists1
settings file check passed


any ideas?

thx

Zeltak

I looked at the file, that is not an error. Swiftdove checks that some files exist and reports if they do. Dose the program start? If so its doing exactly what is should.

---

### Post by zeltak on 2008-04-13
hi

swiftfdove does not start at all, not even as root now

zeltak

---

### Post by CPower1 on 2008-05-02
> **Marabu said:**
> Hi all,

I have made a lightning-build for a 64-bit Linux (Compiled on Kubuntu, x86_64 GNU/Linux) for anybody who is interested:
[lightning-0.8-linux-x86_64.xpi]("http://cheetah.ehosting.ch/lightning-0.8-linux-x86_64.xpi")

Cheers

Thanks!!!
It works!

---

### Post by gros777 on 2008-05-07
Thank for the archive, it was very helpful to me (¡muuuuchisimaas gracias!!)

:guitar:

---

### Post by jw5801 on 2008-05-08
Thanks for the lightning build! Is there any way to get the 'lightning' part of Thunderbird and Sunbird to display the same things? It'd be nice to have Sunbird as both a standalone and as a plugin to Thunderbird.

---

### Post by hariprs on 2008-05-21
> **Marabu said:**
> Hi all,

I have made a lightning-build for a 64-bit Linux (Compiled on Kubuntu, x86_64 GNU/Linux) for anybody who is interested:
[lightning-0.8-linux-x86_64.xpi]("http://cheetah.ehosting.ch/lightning-0.8-linux-x86_64.xpi")

Cheers

Thanks a lot..

---

### Post by Il Capitano on 2008-06-03
> **Marabu said:**
> That's strange, I didn't have to fix anything. The thing with Lightning (and Sunbird) is that unlike other extensions, it includes binaries which obviously are architecture dependent. So what i did is I downloaded the source from [ftp://ftp.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.8/source](ftp://ftp.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.8/source), compiled it and found my .xpi in /dist/xpi-stage/lightning.

Thanks a lot for the compiled version and the explanation you provide with it! How did you compile it? Is it just running ./make in the source dir?

---

### Post by sawjew on 2008-06-18
There is another way to get lightning for 64 bit systems;

add this to your sources.list

```
deb http://ppa.launchpad.net/mozillateam/ubuntu hardy main
deb-src http://ppa.launchpad.net/mozillateam/ubuntu hardy main
```

and then;

```
sudo apt-get install lightning-extension
```

and you're done and it will keep you up to date.

It seems to work fine but these are Mozilla testing repositories so I don't know how stable they will be.

---

### Post by stewballs on 2008-07-02
Brilliant response to an community need...

---

### Post by ds3 on 2008-07-12
Just for reference, Mozilla does provide a 64 bit version of Lightning. They just "hide" it under the "Other Systems" link which takes you to a link to the xpi file here:
[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.8/contrib/linux-x86_64/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.8/contrib/linux-x86_64/)

---

