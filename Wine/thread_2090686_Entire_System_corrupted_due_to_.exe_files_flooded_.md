---
title: "Entire System corrupted due to .exe files flooded in the system"
date: 2012-12-03
forum: Wine
---

### Post by omjaijagdish on 2012-12-03
I have been using Ubuntu11.04 for last 3-4 months. Few day ago, I installed wine1.4 to run .exe files on my system. Now a virus is flooded in the entire system which creates a .exe file in each & every folder. And I am unable to view pdf files, .doc documents not even C programs. All the files are corrupted. I am about to loose all of my data & unfortunately.... quit UBUNTU :(... Anyone please let me know how to recover this data...

---

### Post by mörgæs on 2012-12-03
In stead of quitting Ubuntu you should aim for quitting Windows programs and Wine. This will give you the best protection against similar attacks in the future.

Moving your question to the Wine forum.

---

### Post by monkeybrain2012 on 2012-12-03
> **mörgæs said:**
> In stead of quitting Ubuntu you should aim for quitting Windows programs and Wine. This will give you the best protection against similar attacks in the future.
.

+ 1


 Wow, some virus finally works in WINE,should get a platinum rating in WINE HQ

@OP,

Seriously though why would you read pdf in Wine? I think the virus should only affect WINE applications and it shouldn't corrupt your linux installation. To get rid of the virus just remove the .wine folder in your home directory, reinstalling WIne is not necessary and it won't help (.wine is a hidden folder so have to go to View > show hidden files in your file manager or do ctr+h to see it) Also maybe you should configure Wine in such a way that it doesn't have access to your entire home directory (open configure WIne and go to desktop integration, I don't know why by default My doucuments is linked to home and remove the z drive which is mapped to your file system) It may be also a good idea to scan your downloaded .exe files with an AV if it is from a dubious source. I think there are some virus scanners that run natively in Linux for the purpose of detecting Windows virus (e.g bittdefender for unice) and some may run in wine.

I use WIne only for limited and specialized purposes (to be exact run winbugs, use pdf-xchange viewer to fill some forms from govt may be once a year, and play plants vs zombies :)) and I never go on the internet through WINE. If I do most of my stuffs in WIne why not just use Windows? 

BTW, Ubuntu 11.04 has expired back in Oct28 so theoretically it is not secure to go online with it (no more security updates, though it is probably still a lot more secure than going online with Windows as there is no Linux virus in the wild), you should do a clean install of 12.04 or 12.10 at this point anyway.

---

### Post by omjaijagdish on 2012-12-03
but my problem is not solved yet... I have to recover my data that I am about to loose now... how can I recover my data..?

---

### Post by Elfy on 2012-12-03
You need to give more details about where this data is?

Might help to give more detail about this 'virus' as well.

---

### Post by The Cog on 2012-12-03
Also, which folders got a .exe dropped in them?
* all the folders in .wine/drive_c
* all the folders in /home/your-username
* all the folders in /

Also, why do you thing the data files are corrupt? How are you trying to view them - which viewer program - an exe or linux native program?

---

