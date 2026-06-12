---
title: "DEB_BUILD_ARCH=x86_64"
date: 2008-06-13
forum: x86 64-bit Users
---

### Post by of_darkness on 2008-06-13
as i dont want my created deb packages to be called amd64 as i dont use amd 64 ,i use intel 64bit.. but i cant find out howto change DEB_BUILD_ARCH=amd64 to DEB_BUILD_ARCH=x86_64...

---

### Post by pytheas22 on 2008-06-13
I believe that the convention is to use "amd64" regardless of whether it's an Intel or AMD chip, because it's compatible with both.  We say i386 (or i486, i586...) for 32-bit architectures, too, even though they can run on both Intel or AMD CPU's.  So I don't think it's not going to let you change the name because it would violate the rules.  Maybe someone else has more information...

---

### Post by Kilz on 2008-06-13
Not only that, since the system is set up to check for the architecture set to amd64 in the package, if you create packages with the architecture of x86_64 you will get wrong architecture errors when you try to install them.

---

### Post by of_darkness on 2008-06-13
> **Kilz said:**
> Not only that, since the system is set up to check for the architecture set to amd64 in the package, if you create packages with the architecture of x86_64 you will get wrong architecture errors when you try to install them.
*well that is a no problem, i usaly havto use --force-all beckause of bad version numbers ,older packages gets "higer" version numbers and such..

I just dont like the name amd64 beckuse amd is a brand , and it is not the brand of my comp. simple as that. well it only a name you say, to me its a big deal..

---

### Post by pytheas22 on 2008-06-13
> I just dont like the name amd64 beckuse amd is a brand , and it is not the brand of my comp. simple as that. well it only a name you say, to me its a big deal..

I agree; one of the reasons I use Linux is because I got so sick of the branding that infests other platforms.  But as I said, Intel gets its name (less explicitly, but still there) on the iX86 builds, so I guess it balances out.  It would be nicer to just say 386 or x86_64, however, and I'd be interested to know why the conventions were established with branding in the first place.  I think it's also dumb to call the architecture amd64 because it confuses a lot of people.

At least we can use our computers without seeing an apple on every application or being asked incessantly if we want to join MSN network or use Live search, et cetera.

---

### Post by Arkold Thos on 2008-06-13
It's because AMD 64 bits architecture was released by first, it works in AMD and Intel, so I think that is _STUPID_ the arguing about this, first cause Debian got the same name for that architecture, same with other distributions, and I doub't they change sooner or later.

---

### Post by Kilz on 2008-06-14
> **Arkold Thos said:**
> It's because AMD 64 bits architecture was released by first, it works in AMD and Intel, so I think that is _STUPID_ the arguing about this, first cause Debian got the same name for that architecture, same with other distributions, and I doub't they change sooner or later.

I think you nailed why Ubuntu uses the amd64 name for the architecture. Since it is Debian based it would be more work to change something that doesn't matter.

---

### Post by of_darkness on 2008-06-14
> **Arkold Thos said:**
> It's because AMD 64 bits architecture was released by first, it works in AMD and Intel, so I think that is _STUPID_ the arguing about this, first cause Debian got the same name for that architecture, same with other distributions, and I doub't they change sooner or later.
*
well it may have been first ,but i dont think its stupid to have correctnes...

its lika in sweden foks say data insted of dator(computer) of ewrything that belongs to a computer..

amd64 is as it says a 64bit arcitechture computer from the manufactur amd. it cant be anything ells. that would be in my mind on the werge of insanity tu use amd as prefix for an intel 64bit computer.

thats my stand on things enyway. and i think i must reconsinder my usage of kubuntu becuse of this.. so if any one knows of a distrubution that use the correcrt x86-64 and have no plans of hewing out kde 3.5branch..

---

### Post by Kilz on 2008-06-14
> **of_darkness said:**
> *
well it may have been first ,but i dont think its stupid to have correctnes...

its lika in sweden foks say data insted of dator(computer) of ewrything that belongs to a computer..

amd64 is as it says a 64bit arcitechture computer from the manufactur amd. it cant be anything ells. that would be in my mind on the werge of insanity tu use amd as prefix for an intel 64bit computer.

thats my stand on things enyway. and i think i must reconsinder my usage of kubuntu becuse of this.. so if any one knows of a distrubution that use the correcrt x86-64 and have no plans of hewing out kde 3.5branch..

There are lots of distributions that dont use the amd64 label. Most rpm distros dont. But, and this is important, there is no other community like Ubuntu's. None as helpful, polite, or active. So if its all important to you that some numbers are on packages, have fun! The rest of us will be here, enjoying what is important, a well supported, active linux distro. :D

---

### Post by John.Michael.Kane on 2008-06-15
You could also try building an architecture-independent deb package.

In your control file under the Architecture field you should be able to pass the following value (all), which would indicate an architecture-independent package. 

Using the (all) value should leave you with a file labeled myfoo_your version_all.deb.

---

### Post by Arkold Thos on 2008-06-15
Well, I am Debian user since 5 years ago, for some reasons I got many problems with it in mine new computer (altough the others uses Debian). Since this is the desktop computer I need sometimes help of a great community, as the Ubuntu one, thats why I use it, and because I don't have the same problems as in Debian cause drivers <.<.

And I still think that want to change amd64 to intel64 is **** haha, I use a Q6600 and I really don't think is necessary :) always know that it refers to any 64-bits processor

---

