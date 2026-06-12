---
title: "Kile 1.9 for x86_64?"
date: 2007-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Erwin123 on 2007-01-25
Hi there,

since I updated to Edgy, I'm missing the new 64bit version 1.9 of Kile in the repositories (universe). It has only 1.8, but for i386 a version 1.9 exists. So what's wrong?

[http://packages.ubuntulinux.org/edgy/tex/kile](http://packages.ubuntulinux.org/edgy/tex/kile)

Regards,
Erwin


P.S.: I'm not sure whether I'm in the right group, please forbear with me if not...

---

### Post by incubus on 2007-01-25
Hmm... that's not fair, I agree.

I suspect that they backported Kile 1.9 for the i386 platform, but forgot about us.  But this is just a guess, I could be wrong.

Is there much difference between the two versions?

incubus

---

### Post by Erwin123 on 2007-01-26
There isn't really a changelog. But the Kile homepage states that they fixed more than 50 bugs from 1.8 to 1.9 ... This sounds like a reasonable argument for upgrading, doesn't it?

Erwin

---

### Post by incubus on 2007-01-26
Erwin123,

Although I absolutely agree with you, I wouldn't worry so much if Kile 1.8 is doing everything you want right now.  I don't remember having any problem with mine.  You know, "if it ain't broke..."

I believe the best way to get it would be to go to Launchpad and file a request.  It may be a great contribution to the community.

incubus

---

### Post by kleeman on 2007-01-27
I tried rebuilding the debs with amd64 on edgy with 1.9.3 and 1.9.2. Both builds fail with a rather weird g++ syntax error. I suspect a later version of a kdelib is needed.

---

### Post by incubus on 2007-02-11
erwin and kleeman,

Now that I have to write a paper, I had to install Kile and I think I found a good reason for upgrading to version 1.9.  The new version, as maintained by Debian, does not depend on old TeTeX anymore.  It can use texlive instead, as seen here:

[https://launchpad.net/ubuntu/+source/kile/+bug/74233](https://launchpad.net/ubuntu/+source/kile/+bug/74233)

Even in Feisty, Kile for amd64 is still version 1.8.

kleeman, it's so strange that i386 has Kile 1.9, I would think they have the same kde libraries.

incubus

---

### Post by kleeman on 2007-02-12
Incubus,

A quick check shows that Debian testing is now at 1.9.3 for amd64. You could give that a shot or else try recompiling the orig.tar.gz and dsc files for edgy.....

---

### Post by incubus on 2007-02-12
Nice, thank you, I'll give it a try and tell you the results.

incubus

---

### Post by incubus on 2007-02-12
I tried the Debian Package and it works beautifully, flawlessly, I was impressed (all this took me less than 5 min).

I hope the Ubuntu repositories get updated to incorporate it.

incubus

---

### Post by hardhu on 2007-03-05
> **incubus said:**
> I tried the Debian Package and it works beautifully, flawlessly, I was impressed (all this took me less than 5 min).

I hope the Ubuntu repositories get updated to incorporate it.

incubus

Unfortunately, in feisty herd 4 for amd64 the problem is still present: kile version is 1.8.1-3 and it still depends on tetex-bin :(

---

### Post by kleeman on 2007-03-05
> **hardhu said:**
> Unfortunately, in feisty herd 4 for amd64 the problem is still present: kile version is 1.8.1-3 and it still depends on tetex-bin :(
I suggest a bugreport be put in launchpad.....

---

### Post by incubus on 2007-03-05
There's a bug report, which I confirmed and assigned to the Kubuntu team.  But so far, nobody replied back.  I think we should call this to the attention of a particular person, but I'm not sure about whom.

[https://launchpad.net/ubuntu/+source/kile/+bug/67263](https://launchpad.net/ubuntu/+source/kile/+bug/67263)

incubus

---

### Post by kleeman on 2007-03-05
Can you bump up it's importance? Might attract the eye of a kubuntu dev :lolflag:

---

### Post by incubus on 2007-03-05
I did try that, but the "importance" combo box is locked.

So I assigned it to Jonathan Riddell.  He will probably get mad at me, but hopefully he will assign to the right person too.  : )

incubus

---

