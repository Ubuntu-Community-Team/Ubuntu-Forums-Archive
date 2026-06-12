---
title: "broken synaptic package manager"
date: 2009-03-19
forum: x86 64-bit Users
---

### Post by Vansch76 on 2009-03-19
Hi Everyone

I managed to break Synaptic Package Manager. Im using Ubuntu Studio 2.1.
I was doing an update/upgrade and installed a file set that included
the file "zenity". After the upgrade, Synaptic complained that..

Reading package list...error

e : problem parsing dependency depends.
e : error occurred while processing file zenity (newversion1).
e : problem with mergelist /var/lib/dpkg/status
e : the package lists or status file could not be parsed or opened.

Is there a way to delete the last update?

I finally managed to copy /var/lib/dpkg/status file to my desktop for a backup and then change the permission so I could edit it.

I looked at my laptop and found a similar file listing that as comma's
instead of hyphens.

I looked at the line listed and changed the hyphen to a comma.

I was not able to edit the file while it was in the /var/lib/dpkg folder,
so I deleted the original since I had the corrected copy.

Now to the next problem.

I cant copy the file from my desktop to /var/lib/dpkg.
When I try to copy the /Desktop/status file it says it does not exist.
I dont know what the file extension is for status either.

Im mostly sure its a root vs normal user thing, but I dont kn know
how to fix that part.

So that is where I need your advice.
That is assuming that I have the first part right.

So what do you think guys?

Thanks in advance

Vanessa

---

### Post by ninboy on 2009-03-19
> **Vansch76 said:**
> Hi Everyone

I managed to break Synaptic Package Manager. Im using Ubuntu Studio 2.1.
I was doing an update/upgrade and installed a file set that included
the file "zenity". After the upgrade, Synaptic complained that..

Reading package list...error

e : problem parsing dependency depends.
e : error occurred while processing file zenity (newversion1).
e : problem with mergelist /var/lib/dpkg/status
e : the package lists or status file could not be parsed or opened.

Is there a way to delete the last update?

I finally managed to copy /var/lib/dpkg/status file to my desktop for a backup and then change the permission so I could edit it.

I looked at my laptop and found a similar file listing that as comma's
instead of hyphens.

I looked at the line listed and changed the hyphen to a comma.

I was not able to edit the file while it was in the /var/lib/dpkg folder,
so I deleted the original since I had the corrected copy.

Now to the next problem.

I cant copy the file from my desktop to /var/lib/dpkg.
When I try to copy the /Desktop/status file it says it does not exist.
I dont know what the file extension is for status either.

Im mostly sure its a root vs normal user thing, but I dont kn know
how to fix that part.

So that is where I need your advice.
That is assuming that I have the first part right.

So what do you think guys?

Thanks in advance

Vanessa
Well,
possible the file not exists because the route should be ~/Desktop/status
```
sudo mv ~/Desktop/status /var/lib/dpkg/status; chown root:root /var/lib/dpkg/status
```

That should work... I'm just trying to help you move the file, but I don't know if you fix in the file is valid... Besides, I don't think using a status file of another workstation is a good practice, you could end with an even more corrupt synaptic...

---

### Post by 3Miro on 2009-03-20
I did somehting similar when my xorg.config on 8.04-32bit got corrupt, I just copied one from my 8.04-64bit. I don't know if the other one would work. Doesn't this file contain information about all of your packages, they wouldn't be the same on the two systems and you may run into trouble.

I would try to fix the broken stats file first.

---

### Post by Vansch76 on 2009-03-20
Hey Ninboy

Way to go!!  I was able to move the file using the line of code you provided!  I next ran sudo dpkg --configure -a.  
I got an error regarding a syntax error.  After a couple of tries to fix the syntax error with out 
success I deleted the entire zenity section.  Then ran sudo dpkg --configure -a again.  
This gave me a broken package which I was able to fix in synaptic.   

So my system is happy again!

Also I guess I worded my post wrong.  I did not copy the status file from 
another computer, I only compared the two, and then edited the broken one.

But Im glad you "smart guys" knew what to do!

Thanks again
Vanessa

---

### Post by ken78724 on 2009-03-21
Vanessa & Ninboy: 
:lolflag::lolflag:Good work. Signed in as I received an error message installing 8.10 desktop 64-AMD & my synaptic pack manager appeared to have stumble. Turned in before solving the issue. Glad to see a code that worked. 

Ken

---

