---
title: "A real difference between 32 and 64 bit?"
date: 2007-05-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by Pipboy2000k on 2007-05-31
Is there a real difference between 32 and 64 bit linux (or windows?)

i use 64 bit windows (due to its compatibility with 32 bit arch) but linux seems different, can anyone explain why to me?

---

### Post by rsambuca on 2007-05-31
It completely depends on what applications you will be running whether you will find any difference or not.

---

### Post by ryanVickers on 2007-05-31
For most, I've really noticed no difference (but I really have nothing to compare too, just an informed guess), but for rendering large files in kino, I noticed it seems alot faster (as if cycles of processor wasn't all that was running faster).  There are downsides too, though, if you need a flash/java player for firefox, you may not be able to find a working one for 64 bit at this time, unless you use automatix(2)

---

### Post by shad0w_walker on 2007-05-31
To put it in not so simple terms: Libaries.  The reason that windows has the reasonable 32bit compatibility is that most windows apps provide all their own dependencies, so they come with their own supply of 32bit support files.

Due to linux (Specifically debian type distros) grabbing everything seperatly to make things more ordered, it only grabs the 64bit libaries it needs so 32bit programs simply lack the support files they need. If you install them then there is no reason that 32bit programs wont work just fine in a linux environment. This would be alot easier if the debian packages could specify if they require 32bit or 64bit libaries (Dont know if they do or not, just assuming this is why it cant be automatically pulled a dependancy)

And answering the first question. No.

There is no really noticable diffrence between 64bit and 32bit right now. The only time you will notice any major diffrences is for very specific things (Transcoding, stuff like that)

---

### Post by Pipboy2000k on 2007-05-31
> **shad0w_walker said:**
> 

And answering the first question. No.

There is no really noticable diffrence between 64bit and 32bit right now. The only time you will notice any major diffrences is for very specific things (Transcoding, stuff like that)



Thanks, the meant a lot to me

yeah im running 64 bit ubuntu right now and im having some architecture problems, but yeah ... 

besides that im totally new to linux so i dont think i made the right choice when i chose that (although i had all the prerequisites)

---

### Post by shad0w_walker on 2007-05-31
If your new to ubuntu (or linux in general) its probably best just to run a 32bit distro unless you have a good reason. There are so many little things in 64bit which can be sorted but really shouldnt need to be dealt with (AKA they work automagically in 32bit but dont in 64) its probably easiest just to run a 32bit version.

But, if you already have the 64 bit version installed and your happy with it, just stick with it, if you have to fix things yourself or jump through a couple of hoops it can teach you alot about linux. Plus if you switch back to 32bit you will feel pampered even more because its all sorted for you.

---

### Post by Pipboy2000k on 2007-06-01
as far as i can tell, there is really no difference... I have to install programs with command lines constantly, ( and i really dont know how, reading isnt helping me much) and i havent tried out 32 bit honestly, and im thinking hard about it...but doing this will force me to format my dual boot partition..

but thanks a bunch for that detailed description!

any suggestions on tutorials for installing things though? ( i know its a bit off topic but its something that im not getting an answer out of...)

---

### Post by Kilz on 2007-06-01
> **shad0w_walker said:**
> If your new to ubuntu (or linux in general) its probably best just to run a 32bit distro unless you have a good reason. There are so many little things in 64bit which can be sorted but really shouldnt need to be dealt with (AKA they work automagically in 32bit but dont in 64) its probably easiest just to run a 32bit version.
 
IMHO this is wrong. We do the user a disservice by dumbing down. After all for most common uses the setup is not hard. The few 32bit packages needs have howto's and scripts available for install. The person who decides to replace an os should be able to accomplish it.
You may also be forgetting that some 64bit hardware has problems running the 32bit operating system. By saying "just install the 32bit os and you wont have problems", you are in fact telling a lie.

> **Pipboy2000k said:**
> as far as i can tell, there is really no difference... I have to install programs with command lines constantly, ( and i really dont know how, reading isnt helping me much) and i havent tried out 32 bit honestly, and im thinking hard about it...but doing this will force me to format my dual boot partition..

but thanks a bunch for that detailed description!

any suggestions on tutorials for installing things though? ( i know its a bit off topic but its something that im not getting an answer out of...)
That depends on what you want to do, what applications. Here is a good site you may want to bookmark, it tells[ how to install most anything.]("http://www.monkeyblog.org/ubuntu/installing/"). Before anything else you want to try and install applications from the repo's or repositories. then its just selecting, click apply , and watch it install.

Dont think about the bit of the system. No matter what version you are running you are going to have to do some setup and a lot of learning at first. Stick with the 64bit version and post questions in this section and you shouldnt have many problems. Ubuntu is constantly updating, some people are still thinking like the current version is Breezy (4 versions ago) when 64bit was much harder. Things have improved each version.

---

### Post by shad0w_walker on 2007-06-01
I wasnt saying that installing 32bit is some magic cure for all your woes, i was saying that for a majority of users there is no real advantage to running 64bit and that it undeniably easier to install the flashplayer in 32bit then rummaging the forums and finding the script to run.

---

### Post by Kilz on 2007-06-01
> **shad0w_walker said:**
> I wasnt saying that installing 32bit is some magic cure for all your woes, i was saying that for a majority of users there is no real advantage to running 64bit and that it undeniably easier to install the flashplayer in 32bit then rummaging the forums and finding the script to run.

Exactly what is an average user? Can you tell me, will they rip a cd? Maybe back up a DVD? Will they do any graphics editing or creating?
Your also recommending the 32bit version because the Flash install is easier? That it might take , what 4 or 5 minutes to find the info and run a script?

---

### Post by Pipboy2000k on 2007-06-01
Flame on guys...

ive made my decision

---

### Post by jespdj on 2007-06-01
> **Pipboy2000k said:**
> yeah im running 64 bit ubuntu right now and im having some architecture problems, but yeah ... 

What do you mean by "architecture problems"?

---

### Post by rsambuca on 2007-06-01
> **Pipboy2000k said:**
> Flame on guys...

ive made my decision

What was your final decision, by the way?

---

### Post by Pipboy2000k on 2007-06-01
> **jespdj said:**
> What do you mean by "architecture problems"?

i cant install anything that is from a 32 bit architecture, or at least thats how its coming up for me when i get .deb  files and such

 

and my decision was to just use 32 bit, i tried it on my other laptop and it seems to have less issues

---

### Post by shad0w_walker on 2007-06-01
To install deb files for a 32bit distro you need to force the architecture (As far as im aware easiest to do from command line) and then make sure that you have the 32bit versions of all the needed libaries installed on your system.

Also, good luck with the 32bit setup, hope it works out nicely for you and sorry about the little arguement developing earlier, just seems that people cannot point out legitmate issue with the 64bit ubuntu release with out being told they are wrong.

Anyway, enjoy Ubuntu and have fun.

---

### Post by morghi76 on 2007-06-01
I'm not an expert and I'm not able to explain it from a technical point of view, but I have a AMD X2 3800+ and when last week I decided to try Feisty on this new computer (I had Dapper on an old laptop) I went for the x64 version. I mean, I have a 64bit processor and I have access to a great 64bit distro: why not trying it?
Thanks to this forum and the howTos made by people like Kilz I managed to have everything running (except for my G15 keyboard) with very few "terminal" action... If everybody with a 64bit processor goes for a 32bit OS, nobody will ever feel the need to port the software. I don't see the point in going for the "easy" way, as it's not that easier anyway. I actually feel it takes the same level of effort and you may learn a lot more about linux too. But it's only the opinion of a beginner...

---

### Post by Pipboy2000k on 2007-06-01
> **shad0w_walker said:**
> To install deb files for a 32bit distro you need to force the architecture (As far as im aware easiest to do from command line) and then make sure that you have the 32bit versions of all the needed libaries installed on your system.

Also, good luck with the 32bit setup, hope it works out nicely for you and sorry about the little arguement developing earlier, just seems that people cannot point out legitmate issue with the 64bit ubuntu release with out being told they are wrong.

Anyway, enjoy Ubuntu and have fun.

dude, seriously  "LOL @ that" but yeah, im running 32 bit right now, suprisingly i do notice a difference in performance! but anyways, im going to stick with this until im used to linux...

---

### Post by shad0w_walker on 2007-06-01
Thats a first, what are you doing where your noticing the diffrence? I havent personally noticed any speed diffrences.

---

### Post by Pipboy2000k on 2007-06-01
> **shad0w_walker said:**
> Thats a first, what are you doing where your noticing the diffrence? I havent personally noticed any speed diffrences.

its nothing drastic, it just feels a little bit more clunky...

---

### Post by Kilz on 2007-06-01
> **shad0w_walker said:**
> To install deb files for a 32bit distro you need to force the architecture (As far as im aware easiest to do from command line) and then make sure that you have the 32bit versions of all the needed libaries installed on your system.

Also, good luck with the 32bit setup, hope it works out nicely for you and sorry about the little arguement developing earlier, just seems that people cannot point out legitmate issue with the 64bit ubuntu release with out being told they are wrong.

Anyway, enjoy Ubuntu and have fun.

No, you didnt point out a problem IMHO you posted FUD. That fud was involved in a user using the 32bit version on 64bit hardware. Sadly this same FUD is all over. The Fear of something new was reinforced by you.

> **shad0w_walker said:**
> Thats a first, what are you doing where your noticing the diffrence? I havent personally noticed any speed diffrences.

Could it be that you dont use the same applications? Thats why I asked what you think the average user does.

---

### Post by Pipboy2000k on 2007-06-10
> **Kilz said:**
> Exactly what is an average user? Can you tell me, will they rip a cd? Maybe back up a DVD? Will they do any graphics editing or creating?
Your also recommending the 32bit version because the Flash install is easier? That it might take , what 4 or 5 minutes to find the info and run a script?

I'm sure you understand that im completely new to linux. So learning linux and what its about, and comparing the differences between windows and linux. I have enough trouble trying to learn the command line (as well as the commands and their meanings) and new file types, and the history of linux as well so i may better understand it.

in short... yeah im gonna go with 32 bit because i dont want to look up some special script that i dont know what it does so i can run flash (or java) at 64 bit speeds (which are different but i dont mind...) and so i can save 4 minutes...and understand what im doing at the same time

---

