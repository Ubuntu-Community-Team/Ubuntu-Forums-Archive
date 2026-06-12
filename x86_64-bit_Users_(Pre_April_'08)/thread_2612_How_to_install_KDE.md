---
title: "How to install KDE"
date: 2004-10-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by GLDavid on 2004-10-29
Hello

I'm sorry if this thread is a repost but I don't understand how to install KDE.
Here's my sources.list :
```

deb http://archive.ubuntu.com/ubuntu/ warty main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu/ warty-security main restricted  
deb http://archive.ubuntu.com/ubuntu/ warty-updates main restricted universe multiverse 

```
If I well red the documentation, I had to put the Universe packages in my sources.list, so I think I've done it.
But, always, when I want to launck apt-get install kde, I've got many errors :
```

 Depends: kde-amusements but it is not going to be installed
 Depends: kdeaddons but it is not going to be installed
 Depends: kdemultimedia but it is not going to be installed

```

Thank you very much for answers.

---

### Post by GLDavid on 2004-10-30
Well, no one has an idea ?
I know, everyone here prefers Gnome, But I want to choose between KDE and Gnome  :neutral: .

Thank you very much.

---

### Post by united on 2004-10-30
KDE installed just fine and complete for me.

sudo apt-get install kde

Here is my respository list

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
deb [http://jrfonseca.dyndns.org/debian](http://jrfonseca.dyndns.org/debian) ./
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted

John

---

### Post by FLeiXiuS on 2004-10-30
Thats all you have to do.  Update your apt sources and enable the universe repo.  Then
```

sudo apt-get update && sudo apt-get install kde

```

My APT List
I would recommend using mine, the way you enabled muliverse and universe in one line could cause problems.
```

deb http://archive.ubuntu.com/ubuntu warty main restricted
deb-src http://archive.ubuntu.com/ubuntu warty main restricted

deb http://archive.ubuntu.com/ubuntu warty main restricted universe
deb-src http://archive.ubuntu.com/ubuntu warty main restricted universe

deb http://security.ubuntu.com/ubuntu warty-security main restricted
deb-src http://security.ubuntu.com/ubuntu warty-security main restricted

```

---

### Post by GLDavid on 2004-10-31
Hello

Thank you very much for your answers.
I am sorry but even with united solution or FLeiXiuS, I can not install KDE with the same error that I mentionned above.
So, what's the problem. 
I've done sudo apt-get update && sudo apt-get install kde, and I've got the error  :?  :cry: 

Thanks again for anwers.

---

### Post by united on 2004-10-31
OK, so what is now in your sources list - If it's the same as your first post then I guess you would get the same results.

If it is the same as your first post then change to mine or to FleiXuS's sources list. It should work.

John

---

### Post by GLDavid on 2004-10-31
Hello John

Here's my sources.list :
```

deb http://archive.ubuntu.com/ubuntu warty main restricted
deb-src http://archive.ubuntu.com/ubuntu warty main restricted

deb http://archive.ubuntu.com/ubuntu warty main restricted universe
deb-src http://archive.ubuntu.com/ubuntu warty main restricted universe

deb http://security.ubuntu.com/ubuntu warty-security main restricted
deb-src http://security.ubuntu.com/ubuntu warty-security main restricted

```
I think it is the same than yours or FLeiXiuS.
And If I make a apt-get update && apt-get install kde, I have always the same errors  ](*,) 
So, what's the problem ???

Thanks for answers.

Happy Halloween  :twisted:

---

### Post by josel on 2004-10-31
Try adding this source
[http://geeksoc.org/~jr/ubuntu/](http://geeksoc.org/~jr/ubuntu/) unstable main

I have been running kde 3.3.0 without problems so far .

Now does anyone where the latest koffice can be found that works on ubuntu??

---

### Post by GLDavid on 2004-10-31
Hello Josel

Thanks for your answer but it does not work any more.
May be I forgot to tell you that I have a AMD 64.

Bye bye

Happy Halloween

---

### Post by jdong on 2004-10-31
[QUOTE=GLDavid]Hello Josel

Thanks for your answer but it does not work any more.
May be I forgot to tell you that I have a AMD 64.

Bye bye

Happy Halloween[/QUOTE]

That makes a **huge difference**! The package lists of 32-bit and 64-bit ubuntu are different; perhaps a few packages for KDE aren't built yet for Ubuntu AMD64. Moving over to AMD64 support forum, see if you can get a better answer there!

---

### Post by stodge on 2004-10-31
I get the same error and I'm definitely not using an AMD64:

```
 sudo apt-get update && sudo apt-get install kde
Get:1 http://security.ubuntu.com warty-security/main Packages [15.1kB]
Get:2 http://archive.ubuntu.com warty/universe Packages [2580kB]
Get:3 http://security.ubuntu.com warty-security/main Release [102B]
Get:4 http://security.ubuntu.com warty-security/restricted Packages [20B]
Get:5 http://security.ubuntu.com warty-security/restricted Release [108B]
Get:6 http://security.ubuntu.com warty-security/main Sources [4047B]
Get:7 http://security.ubuntu.com warty-security/main Release [104B]
Get:8 http://security.ubuntu.com warty-security/restricted Sources [20B]
Get:9 http://security.ubuntu.com warty-security/restricted Release [110B]
Get:10 http://archive.ubuntu.com warty/universe Release [83B]
Get:11 http://archive.ubuntu.com warty/universe Sources [1053kB]
Get:12 http://archive.ubuntu.com warty/universe Release [85B]
Fetched 3652kB in 15s (237kB/s)
Reading Package Lists... Done
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kde: Depends: kde-core but it is not going to be installed
       Depends: kde-amusements but it is not going to be installed
       Depends: kdeaddons but it is not going to be installed
       Depends: kdeadmin but it is not going to be installed
       Depends: kdeartwork but it is not going to be installed
       Depends: kdegraphics but it is not going to be installed
       Depends: kdemultimedia but it is not going to be installed
       Depends: kdenetwork but it is not going to be installed
       Depends: kdepim but it is not going to be installed
       Depends: kdeutils but it is not going to be installed
       Depends: quanta but it is not going to be installed
E: Broken packages
```

---

### Post by GLDavid on 2004-11-01
Ok, that's what I thought.
Thanks for the answer. Let this thread opened. If I can install KDE I will let you know. 
Bye bye !

PS : but may be some developpers of Ubuntu would tell me when the packages for KDE will be ready for AMD 64 ?

---

### Post by stodge on 2004-11-02
Is KDE 3.3 available from anywhere?

Thanks

---

### Post by jdong on 2004-11-02
you could try using apt-get --compile source <kde package> to attempt to compile the packages.

---

### Post by stodge on 2004-11-02
Oooh compiling on my PC would take weeks!!! I think I'll stick whatever the version is through Universe.

Thanks

---

### Post by jdong on 2004-11-02
Err, don't you have an AMD64? ;)

---

### Post by GLDavid on 2004-11-03
One question : why can I install Konqueror with apt-get on my AMD 64 with Ubuntu (for AMD64 of course  ;-) ) and not KDE ?
Isn't it strange ?

Bye bye and thank you very much for answer.

---

### Post by jdong on 2004-11-04
because the konqueror and kdenetwork packages are built, but not all the others are...

---

### Post by stodge on 2004-11-04
[QUOTE=jdong]Err, don't you have an AMD64? ;)[/QUOTE]

If you were asking me this question: no I don't have an AMD64, just a P3.

---

