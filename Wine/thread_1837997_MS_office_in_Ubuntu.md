---
title: "MS office in Ubuntu"
date: 2011-09-02
forum: Wine
---

### Post by rathish.arumugam on 2011-09-02
Hey guys!!!

I recently shifted to Ubuntu and I'm finding a little problem with the office programs. 
Still in my office people use Microsoft Office and I'm the only one using open Office. 

Now I'm very much attached to Ubuntu and I don't want to shift from Ubuntu. My friend suggested that by using a software called "wine" I can run .exe files in Ubuntu. 

Can I install Microsft office through wine?

Else is there any other way to get MS -Office in Ubuntu?

---

### Post by dodo3773 on 2011-09-02
> **rathish.arumugam said:**
> Hey guys!!!

I recently shifted to Ubuntu and I'm finding a little problem with the office programs. 
Still in my office people use Microsoft Office and I'm the only one using open Office. 

Now I'm very much attached to Ubuntu and I don't want to shift from Ubuntu. My friend suggested that by using a software called "wine" I can run .exe files in Ubuntu. 

Can I install Microsft office through wine?

Else is there any other way to get MS -Office in Ubuntu?

I run office 2007 in wine. I use a commercial version of wine though called "crossover-linux". If you don't mind spending a couple of bucks I highly recommend it. It pretty much does everything for you. Outlook even works with the new version.

---

### Post by haqking on 2011-09-02
You could use wine but the proprietary software runs its best in its native environment.

Alot of people use wine or similiar or Virtualisation.

try [www.virtualbox.org]("http://www.virtualbox.org") if you want to run it natively.

Or dual boot

---

### Post by uRock on 2011-09-02
Hello and Welcome to the forums,

You can use the MS Office in the browser by logging into your Hotmail account. It'll let you create and edit documents within the browser.

---

### Post by Jerry N on 2011-09-02
Office versions 2007 and older work well with Wine but as has been pointed out Codeweavers Crossover makes installing Windows programs much easier.  I have personally run Office 97 and Office 2003 (and a number of other rather old Windows programs) using Crossover and find that Word and Excel perform better than their counterparts in OpenOffice or LibreOffice. I have not tried to use Access so I can't say how well it works.  I have limited experience with Windows in a virtual memory environment but when I tried it a saw a marked degradation in performance compared with running Windows applications in Crossover.  Running Windows applications in Linux is offensive to some Linux purists.  I suppose running Abiword, gnumeric, and GIMP in Windows is offensive to some Windows purists too.  Being a pragmatist, I say do what works for you!  

Jerry

---

### Post by sandyd on 2011-09-02
Unless you want to use something other than the Three Core Apps - Word, Excel, Powerpoint, WINE will do fine. The core apps get looked at the most.

But anyways... The whole compatability list is here -> [http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992)

Don't use office 2010. Installer works if you put your back into it, but the apps don't.

---

### Post by b.ash on 2011-09-02
I switched to Open Office before switching to linux and loved it from the moment I loaded it. Is there something Word can do that OO can't?

---

### Post by Jerry N on 2011-09-02
> **b.ash said:**
> I switched to Open Office before switching to linux and loved it from the moment I loaded it. Is there something Word can do that OO can't?

Other than Word macros, probably not.  However, the Open Office Writer is only somewhat compatible with Word.  In particular, formatting can get screwed up between the two.  Not that one is better than the other, it is just that they are not the same.

Jerry

---

### Post by Mark Phelps on 2011-09-04
> **rathish.arumugam said:**
> ...
Can I install Microsft office through wine?..

If you're going to RELY on using MS Office on a daily basis, then it's important to understand the limitations that folks have mentioned ... summarized below:
1) Only the "core" Office products work.  Don't ask about Outlook or Access because they will not work.  Also, once you start branching out into stuff like Project, Info Path, Visio, you're getting into other Office apps that most likely, will NOT work.
2) Office 2010 does not work.  Period.  It took Codeweavers three years to get SOME of Office 2007 to work, and by the time they did, Office 2010 was already out.  So, if you need 2010, expect it to be YEARS before that will happen.
3) The Wine add-ons (like Winetricks or Crossover) simplify installation and configuration, they do not provide additional features.  Meaning, if it doesn't work in Wine, it won't work using any of the add-ons.
4) The new Office 2007 default formats (docx, for example) do NOT work well with non-Office products.  Lots of complaints heard here about Open Office and/or Libre Office not handling these files properly. Nothing you do here is going to change that.

So, basically, if you really need to rely on MS Office for daily usage, you're better off dual-booting and retaining a working MS Windows version of MS Office.

---

### Post by snip3r8 on 2011-09-04
> **dodo3773 said:**
> I run office 2007 in wine. I use a commercial version of wine though called "crossover-linux". If you don't mind spending a couple of bucks I highly recommend it. It pretty much does everything for you. Outlook even works with the new version.

Office 2007 works perfectly in wine

---

### Post by dodo3773 on 2011-09-04
> **Mark Phelps said:**
>   Don't ask about Outlook or Access because they will not work. 


Outlook does work with the new crossover. I tested it with my gmail. No stunnel workaround either.

---

### Post by Mark Phelps on 2011-09-05
> **dodo3773 said:**
> Outlook does work with the new crossover. I tested it with my gmail. No stunnel workaround either.

That's good news ... WHICH version of Outlook, and WHICH version of Crossover?

---

### Post by dodo3773 on 2011-09-05
> **Mark Phelps said:**
> That's good news ... WHICH version of Outlook, and WHICH version of Crossover?

Currently using "Outlook 2007" and "CrossOver Linux Standard 10.0.0"

---

### Post by aura7 on 2011-09-06
Here is the youtube video for installing Office 2010 on Ubuntu

[http://www.youtube.com/watch?v=Ae-Qgd-WG8Q](http://www.youtube.com/watch?v=Ae-Qgd-WG8Q)

---

### Post by vikas barnes on 2011-09-06
Most of the day to day word processing tasks u can do with OO. 
To share files with co-members, just save them in MS-Office 97/2000 format as well

---

### Post by mastablasta on 2011-09-06
> **Jerry N said:**
> Other than Word macros, probably not. However, the Open Office Writer is only somewhat compatible with Word. In particular, formatting can get screwed up between the two. Not that one is better than the other, it is just that they are not the same.
 
Jerry
 
Office will for example change the theme on the fly so oyu can actually see what the docuemnt will look like withouth first confirming or using any preview windows. there are also many other stuff it can do that OO can't only most people don't use them anyway and don't know about them. Also Office 2007/2010 has many good & ready solutions for design. which are incompatible with OOo.
 
i would say
 
MS office 2000 < Open (Libre) Office < Office 2007/2010
 
Office 2007 is different due to use of ribbons. it can be annoying at times but once oyu get used to it it actually makes some sense.
 
For most tasks though Open office is just fine.

---

### Post by Mark Phelps on 2011-09-06
> **aura7 said:**
> Here is the youtube video for installing Office 2010 on Ubuntu

Did you bother to read the part where they say it runs "but crashes very often" -- basically, rendering this useless.

---

### Post by nipunshakya on 2011-09-06
Mr. Mark Phelps has really pointed out the fundamental things needed to be considered and i think he has addressed everything pretty well here......
Personally, i think dual booting can solve your problem if u are very needy regarding the Office 2010

---

### Post by hijiz on 2011-09-06
the easiest way to install office is play on linux [www.**playonlinux**.com]("http://www.playonlinux.com")

---

### Post by Mark Phelps on 2011-09-06
> **hijiz said:**
> the easiest way to install office is play on linux [www.**playonlinux**.com]("http://www.playonlinux.com")

While that is true, what you failed to point out is the following:
1) Office 2010 is NOT supported
2) For Office 2007, the following apps do NOT work: Access, Groove, Outlook.

---

### Post by I2k4 on 2011-09-06
> **uRock said:**
> Hello and Welcome to the forums,

You can use the MS Office in the browser by logging into your Hotmail account. It'll let you create and edit documents within the browser.

Depending on the user's needs, specifically how sophisticated the Office documents created and shared with his colleagues, I think this is the most sensible place to start:

[http://www.officelive.com/en-us/](http://www.officelive.com/en-us/)

The new online Office is pretty limited as to certain functions, especially Excel macros - more like Google Docs than full out Office itself.  But if the shared Office documents are not too fancy, they would always be actual Office documents, with no file translation issues or apologies for "virtual" OS muckups, that would not be appreciated or even acceptable at work.

---

### Post by Mark Phelps on 2011-09-07
> **I2k4 said:**
> ...[http://www.officelive.com/en-us/](http://www.officelive.com/en-us/)

 

That only works if you upload your documents to Microsoft -- something not ALL of us are willing to do!

---

### Post by I2k4 on 2011-09-08
> **Mark Phelps said:**
> That only works if you upload your documents to Microsoft -- something not ALL of us are willing to do!

A legitimate issue - I've got Office docs I wouldn't show Microsoft. On the other hand there are whole businesses and even some government agencies running off Google Docs and exposing all their emails to GMail.  (The competing Microsoft Office service is too new and undeveloped for that.)

The original poster has to decide based on his work requirements, since he committed his hard drive to Ubuntu. My own requirements have lead me to keep Windows/Office on the hard drive, and use Ubuntu on USB.  Users make and deal with their decisions, and should take the time to decide wisely.

---

### Post by ubun2geek on 2011-09-08
Just use winetricks on wine - it will work seamlessly

---

### Post by howefield on 2011-09-09
Thread moved to the "*Wine*" forum.

---

