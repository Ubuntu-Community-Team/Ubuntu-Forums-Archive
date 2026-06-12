---
title: "Running ms office 10"
date: 2012-06-04
forum: Wine
---

### Post by inashdeen on 2012-06-04
Hi, can someone show me a step by step on point me to an appropriate site on how to run ms office 2010 on wine 1.5

Thanks in Advance

---

### Post by sffvba[e0rt on 2012-06-04
*Thread moved to **Wine**.*


404

---

### Post by inashdeen on 2012-06-04
Thanks. Honestly, I don't know how to open this thread in wine.

---

### Post by Basher101 on 2012-06-04
In general, it wont run. I had found a tutorial a long time ago that showed a lot of .dll files which you had to get manually in order for it to somewhat work, but still not functional. If you need it badly either dualboot or use virtualbox if your PC can handle it.

---

### Post by MadmanRB on 2012-06-04
You may have better luck with playonlinux as it does help installation with MS office better.
You can get the latest playonlinux here:

[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

Though personally I say Librfeoffice does the same job in the end

---

### Post by Basher101 on 2012-06-04
i had tried to get it to run in PlayOnLinux, wont work...just errors all over. Gave up, got myself RT se7en, took my windows 7 dvd, and threw out all features/drivers/stuff i wont need to run it in a Virtualbox. End result was a 1,5 GB install which runs without networking (and not to mention without all the features)


p.s. Dont use RT se7en....it took me a whole weekend to find all the components i had to keep for it to run and get it to 1,5 gigs..

---

### Post by inashdeen on 2012-06-04
I don't think playonlinux could run ms office 10 as of now. well, i have red article saying it would work. i actually tried, and it work, but its too buggy on 1.4. on 1.5, it didnt work at all :(

---

### Post by Mark Phelps on 2012-06-04
By the way ... MS Office 2010 is NOT Office 10.  MS Office 2010 is actually Office 14.  

Microsoft likes to have two different names for the same product -- the one they advertise to the public (Office 2010) and the one they use internally (Office 14).

---

### Post by AnotherMuggle on 2012-06-04
Do you have any special requirements which make Microsoft Office your only option?

Unless you have a specific reason then you'd do better to just use LibreOffice.

---

### Post by forrestcupp on 2012-06-05
LibreOffice is absolutely not a good suggestion for someone who needs Office.

If you use PlayOnLinux's PPA, you'll be able to upgrade to the latest version. I believe that the latest version supports Office 2010. If you update and find that it isn't supported by default, they have a script [in their script repositories](http://www.playonlinux.com/repository/?cat=3&type=0) that will install Office 2010. This is the easiest way to get it working.

After you do that, check out my [HowTo about associating your filetypes with PlayOnLinux installed Office](http://ubuntuforums.org/showthread.php?t=1940522). It also shows how to get a shortcut for Word, Excel, etc. into a Dash search.

---

### Post by AnotherMuggle on 2012-06-05
> **forrestcupp said:**
> LibreOffice is absolutely not a good suggestion for someone who needs Office.

...

Like I said, it depends on what the need for Microsoft Office is.  I "needed" it right the way through university but never once fell short with only OpenOffice at my disposal.

---

### Post by forrestcupp on 2012-06-05
> **AnotherMuggle said:**
> Like I said, it depends on what the need for Microsoft Office is.  I "needed" it right the way through university but never once fell short with only OpenOffice at my disposal.

LibreOffice is great at what it does. But if you need good formatting compatibility with docx files, it's not a good solution. It can do docx, but not very well. If you can get away with using ODF formats, LibreOffice is an excellent choice. Of course if you need to use Publisher or Access, you'll have to have MS Office, but those don't even work in Wine.

---

